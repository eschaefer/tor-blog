---
layout: post
title: "Hidden Services need some love"
permalink: hidden-services-need-some-love
date: 2013-04-22 20:13:05
author: asn
category: blog
status: closed
tags: ["hidden services", "love", "research"]
---

Hidden Services are in a peculiar situation. While they see a loyal fan-base, there are no dedicated Tor developers to take care of them. This results in a big pile of features that need to be researched, implemented and deployed to make Hidden Services more secure and effective.

The purpose of this blog post is threefold:

1.  Introduce Hidden Service operators to various shortcomings of the Hidden Service architecture.
2.  Introduce researchers to various research questions regarding Hidden Services.
3.  Introduce developers to the plethora of coding tasks left to be done in the hidden Service ecosystem.

  

Note that not every idea listed in the blog post is going to turn out to be a great idea. This post is more of a brain-dump than a solid fully-analyzed agenda.

In any case, let's get down to the issues:

  

* * * * *

  

### Hidden Service Scaling

  

The current Hidden Services architecture does not scale well. Ideally, big websites should have the option to completely migrate to Tor Hidden Services, but this is not possible with their current architecture.

One of the main problems with a busy Hidden Service is that its Introduction Points will get hammered by clients. Since Introduction Points are regular Tor relays, they are not intended to handle such load.

Therefore, one of the first steps for improving Hidden Services scalability is increasing the durability of its Introduction Points. Currently, a Hidden Service selects the number of its Introduction Points (between one and ten) based on a self-estimation of its own popularity. Whether [the formula currently used](https://gitweb.torproject.org/tor.git/tree/src/or/rendservice.c?id=42b42605f8d8eac25361be229354f6393967df4f#n1032) is the best such formula is an open research question.

Another problem with Hidden Services is the lack of load balancing options. While you can load-balance a Hidden Service using TCP/HTTP load balancers (like [HAProxy](https://en.wikipedia.org/wiki/HAProxy)), there is no load-balancing option similar to DNS round-robin, where load balancing happens by sending clients to different server IP addresses. Such load-balancing could be achieved by allowing a Hidden Service to have multiple "subservices". Such an architecture, although appealing, introduces multiple problems, like the intercommunication between subservices, where the long-term keypair is stored, how introduction points are assigned, etc.

  

### Defense against Denial of Service of Introduction Points

  

The adversarial version of the previous section involves attackers intentionally hammering the Introduction Points of a Hidden Service to make it unreachable by honest clients. This means that an attacker can temporarily bring down a Hidden Service by DoSing a small number of Tor relays.

To defend against such attacks, Syverson and Øverlier introduced *Valet nodes* in their PETS 2006 paper: [*"Valet Services: Improving Hidden Servers with a Personal Touch"*](http://freehaven.net/anonbib/#valet:pet2006). *Valet nodes* stand in front of Introduction Points and act as a protection layer. This allows Hidden Services to maintain a limited number of Introduction Points, but many more contact points, without clients learning the actual addresses of the Introduction Points.

Valet nodes are not implemented yet, mainly because of the big implementation and deployment effort they require.

  

### Key Length

  

The long-term keypair of a Hidden Service is an RSA-1024 keypair which nowadays is considered weak. This means that in the future, Hidden Services will need to migrate to a different keysize and/or asymmetric cryptographic algorithm.

A side effect of such migration is that Hidden Services will get a different onion address, which might be troublesome for Hidden Services that have a well-established onion address. To make the transition smoother, Hidden Services should be able to use both old and new keypairs for a while to be able to point their clients to the new address.

Unfortunately, while design work has started on [strengthening some](https://gitweb.torproject.org/torspec.git/tree/proposals/ideas/xxx-crypto-migration.txt) [parts of Tor's cryptography](https://gitweb.torproject.org/torspec.git/tree/proposals/ideas/xxx-new-crypto-sketch.txt), there are no proposals on improving the cryptography of Hidden Services yet.

  

### Attacks by Hidden Service Directory Servers

  

Hidden Services upload their descriptor to Tor nodes called *Hidden Service Directory Servers* (HSDirs). Clients then fetch that descriptor and use it to connect to the Hidden Service.

In the current system, HSDirs are in an interesting position which allows them to perform the following actions:

-   Learn the .onion address of a Hidden Service and connect to it
-   Evaluate the popularity of a Hidden Service by tracking the number of clients who do a lookup for that Hidden Service
-   Refuse to answer a client, and if enough HSDirs do this then the Hidden Service is temporarily unreachable

These scenarios are explored in the upcoming IEEE S&P paper titled *"Trawling for Tor Hidden Services: Detection, Measurement, Deanonymization"* from Alex Biryukov, Ivan Pustogarov and Ralf-Philipp Weinmann. Be sure to check it out (once they publish it)!

Let's look at some suggested fixes for the attacks that Hidden Service Directory Servers can perform:

  

#### Defences against enumeration of onion addresses

Hidden Services use a [hash ring](http://www.martinbroadhurst.com/Consistent-Hash-Ring.html) to choose which HSDirs will host their descriptor; this means that HSDirs can just wait to get picked by Hidden Services and then collect their descriptors and onion addresses. Also, since the hash ring is rotating, HSDirs get new Hidden Service descriptors in every rotation period.

One possible solution to this issue would be to append a symmetric key to the onion address and use it to encrypt the descriptor before sending it to HSDirs (similar to how [descriptor-cookie authentication](https://gitweb.torproject.org/torspec.git/tree/proposals/121-hidden-service-authentication.txt) works currently). A client that knows the onion address can decrypt the descriptor, but an HSDir who doesn't know the onion address can't derive the Hidden Service name. The drawback of this scheme is that the size of onion addresses will increase without increasing the security of their [self-authentication property](https://trac.torproject.org/projects/tor/wiki/doc/HiddenServiceNames#Whyare.onionnamescreatedthatway). Furthermore, HSDirs will still be able to extract the Hidden Service public key from the descriptor, which allows HSDirs to track the descriptors of specific Hidden Services.

A [different solution](https://trac.torproject.org/projects/tor/ticket/8106#comment:1) was proposed by Robert Ransom:

Robert's scheme uses the long-term keypair of a Hidden Service to derive (in a one-way fashion) a second keypair, which is used to encrypt and sign the descriptor that is uploaded to the HSDirs. This construction allows the HSDir, without knowing the long-term keypair of the Hidden Service or the contents of its descriptor, to validate that the entity who uploaded the descriptor had possession of the long-term private key of the Hidden Service. A client who knows the long-term public key of the Hidden Service can fetch the descriptor from the HSDir and verify that it was created by the Hidden Service itself. See the [relevant trac ticket](https://trac.torproject.org/projects/tor/ticket/8106) for a more robust analysis of the idea.

Robert's idea increases the size of onion addresses, but also makes them more resistant to impersonation attacks (the current 80-bit security of onion addresses does not inspire confidence against impresonation attacks). Furthermore, his idea does not allow HSDirs to track Hidden Service descriptors across time.

While Robert's scheme is fairly straightforward, a proper security evaluation is in order and a Tor proposal needs to be written. For extra fun, his idea requires the long-term keypair of the Hidden Service to use a discrete-log cryptosystem, which means that a keypair migration will be needed if we want to proceed with this plan.

  

#### Block tracking of popularity of Hidden Services

HSDirs can track the number of users who do a lookup for a Hidden Service, thereby learning how popular they are. We can make it harder for HSDirs to track the popularity of a Hidden Service, by utilizing a [Private Information Retrieval (PIR) protocol](https://en.wikipedia.org/wiki/Private_information_retrieval) for Hidden Service descriptor fetches. Of course, this won't stop the Introduction Points of a Hidden Service from doing the tracking, but since the Introduction Points were picked by the Hidden Service itself, the threat is smaller.

If we wanted to block Introduction Points from tracking the popularity of Hidden Services, we could attempt hiding the identity of the Hidden Service from its Introduction Points by using a cookie scheme, similar to how the Rendezvous is currently done, or by using Robert's keypair derivation trick and signing the introduction establishment with the new keypair. A careful security evaluation of these ideas is required.

  

#### Make it harder to become an adversarial HSDir

Because of the security implications that HSDirs have for a Hidden Services, [we started working](https://trac.torproject.org/projects/tor/ticket/8243) on making it harder for a Tor relay to become an HSDir node.

Also, currently, an adversary can predict the identity keys it will need in the future to target a *specific* Hidden Service. [We started thinking of ways](https://trac.torproject.org/projects/tor/ticket/8244) to avoid this attack.

  

### Performance improvements

  

Hidden services are slooooowwww and we don't even understand why. They might be slow because of the expensive setup process of creating a Hidden Service circuit, or because Hidden Service circuits have 6 hops, or because of something else. Many suggestions have been proposed to reduce the latency of Hidden Services, ranging from [Hidden Service protocol hacks](https://gitweb.torproject.org/torspec.git/tree/proposals/155-four-hidden-service-improvements.txt) to [Javascript hacks](https://github.com/hellais/latenza.js), and to radically changing how the Hidden Service circuit is formed.

Let's investigate some of these proposals:

  

#### Reducing Hidden Service Circuit Setup complexity

During PETS 2007 Syverson and Øverlier presented "*Improving Efficiency and Simplicity of Tor circuit establishment and hidden services*" which simplifies Hidden Service circuit establishmentby eliminating the need of a separate rendezvous connection.

They noticed that by using *Valet nodes*, the concept of Rendezvous Points is redundant and that a Hidden Service circuit can be formed by just using *Valet nodes* and Introduction Points. Karsten Loesing [wrote a Tor proposal](https://gitweb.torproject.org/torspec.git/tree/proposals/142-combine-intro-and-rend-points.txt) for a variant of this idea.

The reason this scheme is not implemented is that the security trade-offs introduced are not well understood, and there are also some technical obstacles (like the fact that sharing of circuits between multiple clients is not currently supported).

  

#### Analyze Hidden Service Circuit Establishment Timing With Torperf

Establishing a connection to a hidden service currently involves two Tor relays, the introduction and rendezvous point, and 10 more relays distributed over four circuits to connect to them. No one has really researched how much time Tor spends in each step of that complicated process. It wouldn't be surprising if a large amount of time is spent in an unexpected part of the process.

To investigate this properly, one should use [Torperf](https://gitweb.torproject.org/torperf.git) to analyze the timing delta between the steps of the process. Unfortunately, Torperf uses controller events to distinguish between Tor protocol phases but not all steps of the Hidden Service circuit setup have controller events assigned to them. Implementing this involves [adding the control port triggers](https://trac.torproject.org/projects/tor/ticket/8510) to the Tor codebase, running Torperf and then collecting and analyzing the results.

  

#### Hidden Services should reuse old Introduction Points

Currently, Hidden Services stop establishing circuits to old Introduction Points after they break. While this behavior makes sense, it means that clients who have old hidden service descriptors will keep introducing themselves to the wrong introduction points. This is especially painful in roaming situations where users frequently change networks (and lose existing circuits).

[A solution to this](https://trac.torproject.org/projects/tor/ticket/8239) would be for Hidden Services to reestablish failed circuits to old Introduction Points (if the circuits were destroyed because of network failures). We should explore the security consequences of such a move, and also what's the exact time period that Introduction Points are considered "old" but still "worth reestablishing circuits to".

  

### Encrypted Services

  

[Encrypted Services](https://gitweb.torproject.org/torspec.git/tree/proposals/ideas/xxx-encrypted-services.txt) is the correct way of implementing the now-defunct [Exit Enclaves](https://trac.torproject.org/projects/tor/wiki/doc/ExitEnclave).

Encrypted Services allow you to run a non-anonymous Hidden Service where the server-side rendezvous circuit is only one hop. This makes sense in scenarios where the Hidden Service doesn't care about its anonymity, but still wants to allow its clients to access it anonymously (and with all the other features that self-authenticating names provide). See Roger's [original proposal](https://gitweb.torproject.org/torspec.git/tree/proposals/ideas/xxx-encrypted-services.txt) for more use cases and information.

On this topic, [Robert Ransom proposed](https://lists.torproject.org/pipermail/tor-dev/2012-March/003434.html) to implement Encrypted Services as a program separate from Tor, since it serves a quite different threat model. Furthermore, if done this way, its users won't overload the Tor network and it will also allow greater versatility and easier deployment.

  

### Human Memorable onion addresses

  

[Zooko's triangle](https://en.wikipedia.org/wiki/Zooko%27s_triangle) characterizes onion addresses as *secure* and *global*, but not *human memorable*. By now [a couple](https://gitweb.torproject.org/torspec.git/tree/proposals/ideas/xxx-onion-nyms.txt) [of schemes](http://archives.seul.org/or/dev/Dec-2011/msg00034.html) have been proposed to make hidden services addresses memorable, but for [various reasons](https://lists.torproject.org/pipermail/tor-dev/2012-March/003434.html) none of them has been particularly successful.

  

* * * * *

  

These were just some of the things that must be done in the Hidden Services realm. If you are interested in helping around, please read the links and trac tickets, and hit us back with [proposals](https://gitweb.torproject.org/torspec.git/tree/proposals/001-process.txt), patches and suggestions. Use the [[tor-dev] mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-dev/), or our [IRC channels](https://www.torproject.org/about/contact#irc) for development-related communication.

Finally, note that this blog post only touched issues that involve Tor's codebase or the Hidden Service protocol and its cryptography. However, if we want Hidden Services to be truly successful and influential, it's also important to build a vibrant ecosystem around them. For example, we need privacy-preserving archiving systems and search engines (and technologies and rules on how they should work), we need easy-to-use publishing platforms, Internet service daemons and protocols optimized for high-latency connections, anonymous file sharing, chat systems and social networks.

Thanks go to Roger, Robert and other people for the helpful comments and suggestions on this blog post.

PS: Don't forget to use [anonbib](http://freehaven.net/anonbib/) to find and download any research papers mentioned in this blog post.
