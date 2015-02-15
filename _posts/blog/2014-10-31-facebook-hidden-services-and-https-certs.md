---
layout: post
title: "Facebook, hidden services, and https certs"
permalink: facebook-hidden-services-and-https-certs
date: 2014-10-31 20:09:20
author: arma
category: blog
comments: closed
tags: ["advocacy", "hidden services", "research"]
---

Today Facebook unveiled its [hidden service](https://facebookcorewwwi.onion/) that lets users access their website more safely. Users and journalists have been asking for our response; here are some points to help you understand our thinking.

Part one: yes, visiting Facebook over Tor is not a contradiction
----------------------------------------------------------------

I didn't even realize I should include this section, until I heard from a journalist today who hoped to get a quote from me about why Tor users wouldn't ever use Facebook. Putting aside the (still very important) questions of Facebook's privacy habits, their harmful real-name policies, and whether you should or shouldn't tell them anything about you, the key point here is that **anonymity isn't just about hiding from your destination**.

There's no reason to let your ISP know when or whether you're visiting Facebook. There's no reason for Facebook's upstream ISP, or some agency that surveils the Internet, to learn when and whether you use Facebook. And if you do choose to tell Facebook something about you, there's still no reason to let them automatically discover what city you're in today while you do it.

Also, we should remember that there are some places in the world that can't reach Facebook. Long ago I talked to a Facebook security person who told me a fun story. When he first learned about Tor, he hated and feared it because it "clearly" intended to undermine their business model of learning everything about all their users. Then suddenly Iran blocked Facebook, a good chunk of the Persian Facebook population switched over to reaching Facebook via Tor, and he became a huge Tor fan because otherwise those users would have been cut off. Other countries like China followed a similar pattern after that. This switch in his mind between "Tor as a privacy tool to let users control their own data" to "Tor as a communications tool to give users freedom to choose what sites they visit" is a great example of the [diversity of uses for Tor](https://www.torproject.org/about/torusers): whatever it is you think Tor is for, I guarantee there's a person out there who uses it for something you haven't considered.

Part two: we're happy to see broader adoption of hidden services
----------------------------------------------------------------

I think it is great for Tor that Facebook has added a .onion address. There are some compelling use cases for hidden services: see for example the ones described at [using Tor hidden services for good](https://blog.torproject.org/blog/using-tor-good), as well as upcoming decentralized chat tools like Ricochet where every user is a hidden service, so there's no central point to tap or lean on to retain data. But we haven't really publicized these examples much, especially compared to the publicity that the "I have a website that the man wants to shut down" examples have gotten in recent years.

[Hidden services](https://www.torproject.org/docs/hidden-services) provide a variety of useful security properties. First — and the one that most people think of — because the design uses [Tor circuits](https://www.torproject.org/about/overview#thesolution), it's hard to discover where the service is located in the world. But second, because the address of the service is [the hash of its key](https://gitweb.torproject.org/torspec.git/blob/HEAD:/rend-spec.txt#l527), they are self-authenticating: if you type in a given .onion address, your Tor client guarantees that it really is talking to the service that knows the private key that corresponds to the address. A third nice feature is that the rendezvous process provides end-to-end encryption, even when the application-level traffic is unencrypted.

So I am excited that this move by Facebook will help to continue opening people's minds about why they might want to offer a hidden service, and help other people think of further novel uses for hidden services.

Another really nice implication here is that Facebook is committing to taking its Tor users seriously. Hundreds of thousands of people have been successfully using Facebook over Tor for years, but in today's era of services like Wikipedia [choosing not to accept contributions from users who care about privacy](https://blog.torproject.org/blog/call-arms-helping-internet-services-accept-anonymous-users), it is refreshing and heartening to see a large website decide that it's ok for their users to want more safety.

As an addendum to that optimism, I would be really sad if Facebook added a hidden service, had a few problems with trolls, and decided that they should prevent Tor users from using their old [https://www.facebook.com/](https://www.facebook.com/ "https://www.facebook.com/") address. So we should be vigilant in helping Facebook continue to allow Tor users to reach them through either address.

Part three: their vanity address doesn't mean the world has ended
-----------------------------------------------------------------

Their hidden service name is "facebookcorewwwi.onion". For a hash of a public key, that sure doesn't look random. Many people have been wondering how they [brute forced](https://en.wikipedia.org/wiki/Brute-force_attack) the entire name.

The short answer is that for the first half of it ("facebook"), which is only 40 bits, they generated keys over and over until they got some keys whose first 40 bits of the hash matched the string they wanted.

Then they had some keys whose name started with "facebook", and they looked at the second half of each of them to pick out the ones with pronouncable and thus memorable syllables. The "corewwwi" one looked best to them — meaning they could come up with a [story](http://en.wikipedia.org/wiki/Backronym) about why that's a reasonable name for Facebook to use — [so they went with it](https://lists.torproject.org/pipermail/tor-talk/2014-October/035413.html).

So to be clear, they would not be able to produce exactly this name again if they wanted to. They could produce other hashes that start with "facebook" and end with pronouncable syllables, but that's not brute forcing all of the hidden service name (all 80 bits).

For those who want to explore the math more, read about the ["birthday attack"](https://en.wikipedia.org/wiki/Birthday_attack). And for those who want to learn more (please help!) about the improvements we'd like to make for hidden services, including stronger keys and stronger names, see [hidden services need some love](https://blog.torproject.org/blog/hidden-services-need-some-love) and [Tor proposal 224](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/224-rend-spec-ng.txt).

Part four: what do we think about an https cert for a .onion address?
---------------------------------------------------------------------

Facebook didn't just set up a hidden service. They also got an https certificate for their hidden service, and it's signed by Digicert so your browser will accept it. This choice has produced some [feisty discussions](https://cabforum.org/pipermail/public/2014-October/thread.html#4210) in the CA/Browser community, which decides what kinds of names can get official certificates. That discussion is still ongoing, but here are my early thoughts on it.

In favor: we, the Internet security community, have taught people that https is necessary and http is scary. So it makes sense that users want to see the string "https" in front of them.

Against: Tor's .onion handshake basically gives you all of that for free, so by encouraging people to pay Digicert we're reinforcing the CA business model when maybe we should be continuing to demonstrate an alternative.

In favor: Actually https does give you a little bit more, in the case where the service (Facebook's webserver farm) isn't in the same location as the Tor program. Remember that there's no requirement for the webserver and the Tor process to be on the same machine, and in a complicated set-up like Facebook's they probably shouldn't be. One could argue that this last mile is inside their corporate network, so who cares if it's unencrypted, but I think the simple phrase "ssl added and removed here" will kill that argument.

Against: if one site gets a cert, it will further reinforce to users that it's "needed", and then the users will start asking other sites why they don't have one. I worry about starting a trend where you need to pay Digicert money to have a hidden service or your users think it's sketchy — especially since hidden services that value their anonymity could have a hard time getting a certificate.

One alternative would be to teach Tor Browser that https .onion addresses don't deserve a scary pop-up warning. A more thorough approach in that direction is to have a way for a hidden service to generate its own signed https cert using its onion private key, and teach Tor Browser how to verify them — basically a decentralized CA for .onion addresses, since they are self-authenticating anyway. Then you don't have to go through the nonsense of pretending to see if they could read email at the domain, and generally furthering the current CA model.

We could also imagine a [pet name](https://en.wikipedia.org/wiki/Petname) model where the user can tell her Tor Browser that this .onion address "is" Facebook. Or the more direct approach would be to ship a bookmark list of "known" hidden services in Tor Browser — like being our own CA, using the old-fashioned /etc/hosts model. That approach would raise the political question though of which sites we should endorse in this way.

So I haven't made up my mind yet about which direction I think this discussion should go. I'm sympathetic to "we've taught the users to check for https, so let's not confuse them", but I also worry about the slippery slope where getting a cert becomes a required step to having a reputable service. Let us know if you have other compelling arguments for or against.

Part five: what remains to be done?
-----------------------------------

In terms of both design and security, [hidden services still need some love](https://blog.torproject.org/blog/hidden-services-need-some-love). We have plans for improved designs (see [Tor proposal 224](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/224-rend-spec-ng.txt)) but we don't have enough funding and developers to make it happen. We've been talking to some Facebook engineers this week about hidden service reliability and scalability, and we're excited that Facebook is thinking of putting development effort into helping improve hidden services.

And finally, speaking of teaching people about the security features of .onion sites, I wonder if "hidden services" is no longer the best phrase here. Originally we called them "location-hidden services", which was quickly shortened in practice to just "hidden services". But protecting the location of the service is just one of the security features you get. Maybe we should hold a contest to come up with a new name for these protected services? Even something like "onion services" might be better if it forces people to learn what it is.
