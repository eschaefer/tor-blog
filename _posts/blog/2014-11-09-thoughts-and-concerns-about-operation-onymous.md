---
layout: post
title: "Thoughts and Concerns about Operation Onymous"
permalink: thoughts-and-concerns-about-operation-onymous
date: 2014-11-09 09:54:45
author: phobos
category: blog
status: closed
tags: ["hidden services", "operation onymous", "seizures", "tor project"]
---

What happened
=============

Recently it was [announced](https://www.europol.europa.eu/content/global-action-against-dark-markets-tor-network) that a coalition of government agencies took control of many Tor hidden services. We were as surprised as most of you. Unfortunately, we have very little information about how this was accomplished, but we do have some thoughts which we want to share.

Over the last few days, we received and read reports saying that several Tor relays were seized by government officials. We do not know why the systems were seized, nor do we know anything about the methods of investigation which were used. Specifically, there are [reports that three systems of Torservers.net disappeared](https://blog.torservers.net/20141109/three-servers-offline-likely-seized.html) and there is another [](https://raided4tor.wordpress.com)report by an independent relay operator. If anyone has more details, please get in contact with us. If your relay was seized, please also tell us its identity so that we can request that the directory authorities reject it from the network.

But, more to the point, the recent publications call the targeted hidden services seizures "Operation Onymous" and they say it was coordinated by Europol and other government entities. Early reports say 17 people were arrested, and 400 hidden services were seized. [Later reports](http://www.dailydot.com/politics/oops-we-counted-wrong-silk-road-dark-net-tor/) have clarified that it was hundreds of URLs hosted on roughly 27 web sites offering hidden services. We have not been contacted directly or indirectly by Europol nor any other agency involved.

Tor is most interested in understanding how these services were located, and if this indicates a security weakness in Tor hidden services that could be exploited by criminals or secret police repressing dissents. We are also interested in learning why the authorities seized Tor relays even though their operation was targetting hidden services. Were these two events related?

How did they locate the hidden services?
========================================

So we are left asking "How did they locate the hidden services?". We don't know. In liberal democracies, we should expect that when the time comes to prosecute some of the seventeen people who have been arrested, the police would have to explain to the judge how the suspects came to be suspects, and that as a side benefit of the operation of justice, Tor could learn if there are security flaws in hidden services or other critical internet-facing services. We know through recent leaks that the US DEA and others have constructed a system of organized and sanctioned perjury which they refer to as "parallel construction."

Unfortunately, the authorities did not specify how they managed to locate the hidden services. Here are some plausible scenarios:

Operational Security
--------------------

The first and most obvious explanation is that the operators of these hidden services failed to use adequate operational security. For example, there are reports of one of the websites being infiltrated by undercover agents and the [affidavit](https://www.documentcloud.org/documents/1354808-blake-benthall-complaint.html) states various [operational security errors](https://pbs.twimg.com/media/B1xhq32CIAAuc8y.png).

SQL injections
--------------

Another explanation is exploitation of common web bugs like SQL injections or RFIs (remote file inclusions). Many of those websites were likely quickly-coded e-shops with a big attack surface. Exploitable bugs in web applications are a common problem.

Bitcoin deanonymization
-----------------------

Ivan Pustogarov et al. have [recently](https://crypto.stanford.edu/seclab/sem-14-15/pustogarov.html) been conducting interesting [research on Bitcoin anonymity](http://arxiv.org/abs/1405.7418).

Apparently, there are ways to link transactions and deanonymize Bitcoin clients even if they use Tor. Maybe the seized hidden services were running Bitcoin clients themselves and were victims of similar attacks.

Attacks on the Tor network
--------------------------

The [number of takedowns](https://lists.torproject.org/pipermail/tor-talk/2014-November/035606.html) and the fact that Tor relays were seized could also mean that the Tor network was attacked to reveal the location of those hidden services. We received some [interesting information](https://lists.torproject.org/pipermail/tor-dev/2014-November/007731.html) from an operator of a now-seized hidden service which may indicate this, as well. Over the past few years, researchers have discovered various attacks on the Tor network. We've implemented some [defenses](http://www.nrl.navy.mil/itd/chacs/overlier-locating-hidden-servers) against these attacks, but these defenses do not solve all known issues and there may even be attacks unknown to us.

For example, some months ago, someone was launching [non-targetted deanonymization attacks](https://blog.torproject.org/blog/tor-security-advisory-relay-early-traffic-confirmation-attack) on the live Tor network. People suspect that those attacks were carried out by [CERT researchers](https://freedom-to-tinker.com/blog/felten/why-were-cert-researchers-attacking-tor/). While the bug was fixed and the fix quickly deployed in the network, it's [possible](https://www.reddit.com/r/TOR/comments/2lip12/silk_road_as_well_as_others_were_likely/) that as part of their attack, they managed to deanonymize some of those hidden services.

Another possible Tor attack vector could be the *Guard Discovery attack*. This attack doesn't reveal the identity of the hidden service, but allows an attacker to discover the guard node of a specific hidden service. The guard node is the only node in the whole network that knows the actual IP address of the hidden service. Hence, if the attacker then manages to compromise the guard node or somehow obtain access to it, she can launch a traffic confirmation attack to learn the identity of the hidden service. We've been  
 [discussing](https://lists.torproject.org/pipermail/tor-dev/2014-July/007122.html) [various](https://lists.torproject.org/pipermail/tor-dev/2014-September/007472.html) [solutions](https://lists.torproject.org/pipermail/tor-dev/2014-November/007726.html) to the [guard discovery attack](https://trac.torproject.org/projects/tor/ticket/9001) for the past many months but it's [not an easy problem to fix properly](https://lists.torproject.org/pipermail/tor-dev/2014-November/007730.html). Help and feedback on the proposed designs is appreciated.

\*Similarly, there exists the attack where the hidden service selects the attacker's relay as its guard node. This may happen randomly or this could occur if the hidden service selects another relay as its guard and the attacker renders that node unusable, by a [denial of service attack](http://www.robgjansen.com/publications/sniper-ndss2014.pdf) or similar. The hidden service will then be forced to select a new guard. Eventually, the hidden service will select the attacker.

Furthermore, denial of service attacks on relays or clients in the Tor network can often be leveraged into full de-anonymization attacks. These techniques go back many years, in research such as ["From a Trickle to a Flood"](http://freehaven.net/anonbib/cache/trickle02.pdf), ["Denial of Service or Denial of Security?"](http://freehaven.net/anonbib/cache/ccs07-doa.pdf), ["Why I'm not an Entropist"](http://www.syverson.org/entropist-final.pdf), and even the more recent Bitcoin attacks above. In the Hidden Service protocol there are more vectors for DoS attacks, such as the set of HSDirs and the Introduction Points of a Hidden Service.

Finally, remote code execution exploits against Tor software are also always a possibility, but we have zero evidence that such exploits exist. Although the Tor source code gets continuously reviewed by our security-minded developers and community members, we would like more focused auditing by experienced bug hunters. Public-interest initiatives like Project Zero could help out a lot here. Funding to launch a bug bounty program of our own could also bring real benefit to our codebase. If you can help, please get in touch.

Advice to concerned hidden service operators
============================================

As you can see, we still don't know what happened, and it's hard to give concrete suggestions blindly.

If you are a concerned hidden service operator, we suggest you read the cited resources to get a better understanding of the security that hidden services can offer and of the limitations of the current system. When it comes to anonymity, it's clear that the tighter your threat model is, the more informed you need to be about the technologies you use.

If your hidden service lacks sufficient processor, memory, or network resources the DoS based de-anonymization attacks may be easy to leverage against your service. Be sure to review the [Tor performance tuning guide](https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/TUNING) to optimize your relay or client.

\*Another possible suggestion we can provide is manually selecting the guard node of a hidden service. By configuring the EntryNodes option in Tor's [configuration file](https://www.torproject.org/docs/tor-manual.html.en#EntryNodes) you can select a relay in the Tor network you trust. Keep in mind, however, that a determined attacker will still be able to determine this relay is your guard and all other attacks still apply.

Final words
===========

The task of hiding the location of **low-latency** web services is a very hard problem and we still don't know how to do it correctly. It seems that there are various issues that none of the current anonymous publishing designs have really solved.

In a way, it's even surprising that hidden services have survived so far. [The attention they have received is minimal](https://blog.torproject.org/blog/hidden-services-need-some-love) compared to their social value and compared to the size and determination of their adversaries.

It would be great if there were more people reviewing our designs and code. For example, we would really appreciate feedback on the [upcoming hidden service revamp](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/224-rend-spec-ng.txt) or help with the research on guard discovery attacks (see links above).

Also, it's important to note that Tor currently doesn't have funding for improving the security of hidden services. If you are interested in funding hidden services research and development, please get in touch with us. We hope to find time to organize a crowdfunding campaign to acquire independent and focused hidden service funding.

Finally, if you are a relay operator and your server was recently compromised or you lost control of it, [please let us know](https://blog.torproject.org/blog/how-report-bad-relays) by sending an email to [bad-relays@lists.torproject.org](mailto:bad-relays@lists.torproject.org).

Thanks to Griffin, Matt, Adam, Roger, David, George, Karen, and Jake for contributions to this post.

Updates:  
 \* Added information about guard node DoS and EntryNodes option - 2014/11/09 18:16 UTC
