---
layout: post
title: "\"One cell is enough to break Tor's anonymity\""
permalink: one-cell-enough
date: 2009-02-19
author: arma
category: blog
tags: ["attacks", "research", "tagging"]
---

Tomorrow there's a talk at Black Hat DC by Xinwen Fu on an active attack that can allow traffic confirmation in Tor. He calls it a " [replay attack](http://www.cs.uml.edu/~xinwenfu/paper/ICC08_Fu.pdf)", whereas we called it a "tagging attack" in the original Tor paper, but let's look at how it actually works.

First, remember the basics of how Tor provides anonymity. Tor clients [route their traffic](https://www.torproject.org/images/htw2.png) over several ( [usually three](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#VariablePathLength)) relays, with the goal that no single relay gets to learn both where the user is (call her Alice) and what site she's reaching (call it Bob).

The Tor design [doesn't try to protect](https://www.torproject.org/svn/trunk/doc/design-paper/tor-design.html#subsec:threat-model) against an attacker who can see or measure both traffic going into the Tor network and also traffic coming out of the Tor network. That's because if you can see both flows, some [simple statistics](http://freehaven.net/anonbib/#danezis:pet2004) let you decide whether they match up.

Because we aim to let people browse the web, we can't afford the extra overhead and hours of additional delay that are used in high-latency mix networks like [Mixmaster](http://freehaven.net/anonbib/#mixmaster-spec) or [Mixminion](http://freehaven.net/anonbib/#minion-design) to slow this attack. That's why Tor's security is all about trying to decrease the chances that an adversary will end up in the right positions to see the traffic flows.

The way we generally explain it is that Tor tries to protect against traffic analysis, where an attacker tries to learn whom to investigate, but Tor can't protect against traffic confirmation (also known as end-to-end correlation), where an attacker tries to confirm a hypothesis by monitoring the right locations in the network and then doing the math.

And the math is really effective. There are simple packet counting attacks ( [Passive Attack Analysis for Connection-Based Anonymity Systems](http://freehaven.net/anonbib/#SS03)) and moving window averages ( [Timing Attacks in Low-Latency Mix-Based Systems](http://freehaven.net/anonbib/#timing-fc2004)), but the more recent stuff is [downright scary](http://www.lightbluetouchpaper.org/2007/05/28/sampled-traffic-analysis-by-internet-exchange-level-adversaries/), like Steven Murdoch's PET 2007 paper about achieving high confidence in a correlation attack despite seeing only 1 in 2000 packets on each side ( [Sampled Traffic Analysis by Internet-Exchange-Level Adversaries](http://freehaven.net/anonbib/#murdoch-pet2007)).

What Fu is presenting in his talk is another instance of the confirmation attack, called the tagging attack. The basic idea is that an adversary who controls both the first (entry) and last (exit) relay that Alice picks can modify the data flow at one end of the circuit ("tag" it), and detect that modification at the other end — thus bridging the circuit and confirming that it really is Alice talking to Bob. This attack has some limitations compared to the above attacks. First, it involves modifying data, which in most cases will break the connection; so there's a lot more risk that he'll be noticed. Second, the attack relies on the adversary actually controlling both relays. The passive variants can be performed by an observer like an ISP or a telco.

Tagging attacks on designs like Tor go back over a decade in the literature. In the 1996 Onion Routing paper ( [Hiding Routing Information](http://freehaven.net/anonbib/#onion-routing:ih96)), they wrote:

> If the responder's proxy [exit node] is compromised, and can determine when the unencrypted data stream has been corrupted, it is possible for compromised nodes earlier in the virtual circuit to corrupt the stream and ask which responder's proxy received uncorrupted data. By working with compromised nodes around a suspected initiator's proxy [Tor client], one can identify the beginning of the virtual circuit.

When we designed Tor, we made a conscious decision to not design against this attack, because the other confirmation attacks are just as effective and we have no fix for them, and because countering the tagging attack doesn't come for free. Here's a quote from [the Tor design paper](https://www.torproject.org/svn/trunk/doc/design-paper/tor-design.html#subsec:integrity-checking) in 2004:

> Because Tor uses TLS on its links, external adversaries cannot modify data. Addressing the insider malleability attack, however, is more complex.
>
> We could do integrity checking of the relay cells at each hop, either by including hashes or by using an authenticating cipher mode like EAX, but there are some problems. First, these approaches impose a message-expansion overhead at each hop, and so we would have to either leak the path length or waste bytes by padding to a maximum path length. Second, these solutions can only verify traffic coming from Alice: ORs would not be able to produce suitable hashes for the intermediate hops, since the ORs on a circuit do not know the other ORs' session keys. Third, we have already accepted that our design is vulnerable to end-to-end timing attacks; so tagging attacks performed within the circuit provide no additional information to the attacker. Thus, we check integrity only at the edges of each stream.

Basically, we chose a design where the tagging attack is no more effective than the passive confirmation attacks, and figured that would have to be good enough.

I should also note here that the correlation attack papers mostly focus on \_observing\_ flows at either end and matching them up. They do great with just that. But think what you could do if you actually control one of the endpoints, and can modulate how much you send, when you send it, etc. Heck, if you're the exit relay, you can spoof a much larger webpage for the user, and then have even more bytes to work with. None of that requires a tagging attack.

So, where does the "one cell is enough" come in? If you can tag a single cell and recognize it on the other end of the circuit, then you can be confident you've got the right flow.

One of the unknowns in the research world is exactly how quickly the timing attack succeeds. How many seconds of traffic (and/or packets) do you need to achieve a certain level of confidence? I'll grant that if you run the entry and exit, tagging is a very simple attack to carry out both conceptually and in practice. But I think Fu underestimates how simple the timing attack can be also. That's probably the fundamental disagreement here.

For example, Bauer et al. in WPES 2007 described a passive timing attack on Tor circuit creation that works before a single relay cell has been transmitted ( [Low-Resource Routing Attacks Against Tor](http://freehaven.net/anonbib/#bauer:wpes2007)).

Fu's paper also cites concern about false positives -- it seems on first glance that a tagging attack should provide much higher confidence than a timing attack, since you'll always be wondering whether the timing attack really matched up the right circuits. Here's a quote from one of the authors of [Locating Hidden Servers](http://freehaven.net/anonbib/#hs-attack06), another paper with a successful timing attack on Tor:

> We were prepared to do parameter tuning, active timing signature insertion, etc. should it be necessary, but it wasn't. In the thousands of circuits we ran we \_never\_ had a false positive. The Bauer et al. paper from WPES'07 extended our work from hidden server circuits to general Tor circuits (although it only ran on a Tor testbed on PlanetLab rather than the public Tor network). The highest false positive rate they got was .0006. This is just a nonissue.

One of the challenges here is that anonymity designs live on the edge. While crypto algorithms aim to be so good that even really powerful attackers still can't succeed, anonymity networks are constantly balancing performance and efficiency against attacks like these. One of the tradeoffs we made in the Tor design is that we accepted end-to-end correlation as an attack that is too expensive to solve, and we're building the best design we can based on that.

If somebody can show us that tagging attacks are actually much more effective than their passive timing counterparts, we should work harder to fix them. If somebody can come up with a cheap way to make them harder, we're all ears. But while they remain on par with passive attacks and remain expensive to fix, then it doesn't seem like a good move to slow down Tor even more without actually making it safer.

Overall, I'm confused why the conference organizers thought this would be a good topic for a Black Hat talk. It's not like there's a shortage of "oh crap" Tor attack papers lately. I guess my take-away message is that I need to introduce Jeff Moss to Nick Hopper et al from Minnesota ( [How Much Anonymity does Network Latency Leak?](http://freehaven.net/anonbib/#tissec-latency-leak)) and Sambuddho Chakravarty et al from Columbia ( [Approximating a Global Passive Adversary against Tor](http://www.google.com/search?q=columbia+global+passive+adversary+tor)).

