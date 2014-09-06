---
layout: post
title: "Tor security advisory: \"relay early\" traffic confirmation attack"
permalink: blog/tor-security-advisory-relay-early-traffic-confirmation-attack
date: 2014-07-30
author: arma
category: blog
tags: ["entry guards", "hidden services", "research", "security advisory"]
---

This advisory was posted on the [tor-announce](https://lists.torproject.org/pipermail/tor-announce/2014-July/000094.html) mailing list.

## SUMMARY:

On July 4 2014 we found a group of relays that we assume were trying to deanonymize users. They appear to have been targeting people who operate or access Tor hidden services. The attack involved modifying Tor protocol headers to do traffic confirmation attacks.

The attacking relays joined the network on January 30 2014, and we removed them from the network on July 4. While we don't know when they started doing the attack, users who operated or accessed hidden services from early February through July 4 should assume they were affected.

Unfortunately, it's still unclear what "affected" includes. We know the attack looked for users who fetched hidden service descriptors, but the attackers likely were not able to see any application-level traffic (e.g. what pages were loaded or even whether users visited the hidden service they looked up). The attack probably also tried to learn who published hidden service descriptors, which would allow the attackers to learn the location of that hidden service. In theory the attack could also be used to link users to their destinations on normal Tor circuits too, but we found no evidence that the attackers operated any exit relays, making this attack less likely. And finally, we don't know how much data the attackers kept, and due to the way the attack was deployed (more details below), their protocol header modifications might have aided other attackers in deanonymizing users too.

Relays should upgrade to a recent Tor release ( [0.2.4.23](https://lists.torproject.org/pipermail/tor-announce/2014-July/000093.html) or [0.2.5.6-alpha](https://lists.torproject.org/pipermail/tor-talk/2014-July/034180.html)), to close the particular protocol vulnerability the attackers used — but remember that preventing traffic confirmation in general remains an open research problem. Clients that upgrade (once new Tor Browser releases are ready) will take another step towards limiting the number of entry guards that are in a position to see their traffic, thus reducing the damage from future attacks like this one. Hidden service operators should consider changing the location of their hidden service.

## THE TECHNICAL DETAILS:

We believe they used a combination of two classes of attacks: a traffic confirmation attack and a Sybil attack.

A traffic confirmation attack is possible when the attacker controls or observes the relays on both ends of a Tor circuit and then compares traffic timing, volume, or other characteristics to conclude that the two relays are indeed on the same circuit. If the first relay in the circuit (called the "entry guard") knows the IP address of the user, and the last relay in the circuit knows the resource or destination she is accessing, then together they can deanonymize her. You can read more about traffic confirmation attacks, including pointers to many research papers, at this blog post from 2009:
 [https://blog.torproject.org/blog/one-cell-enough](https://blog.torproject.org/blog/one-cell-enough "https://blog.torproject.org/blog/one-cell-enough")

The particular confirmation attack they used was an active attack where the relay on one end injects a signal into the Tor protocol headers, and then the relay on the other end reads the signal. These attacking relays were stable enough to get the HSDir ("suitable for hidden service directory") and Guard ("suitable for being an entry guard") [consensus flags](https://gitweb.torproject.org/torspec.git/blob/HEAD:/dir-spec.txt#l1775). Then they injected the signal whenever they were used as a hidden service directory, and looked for an injected signal whenever they were used as an entry guard.

The way they injected the signal was by sending sequences of "relay" vs "relay early" commands down the circuit, to encode the message they want to send. For [background](https://gitweb.torproject.org/torspec.git/blob/HEAD:/tor-spec.txt#l364), Tor has two types of cells: link cells, which are intended for the adjacent relay in the circuit, and relay cells, which are passed to the other end of the circuit. In 2008 we added a new kind of relay cell, called a "relay early" cell, which is used to prevent people from building very long paths in the Tor network. (Very long paths can be used to [induce congestion](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/110-avoid-infinite-circuits.txt%20) and aid in [breaking anonymity](http://freehaven.net/anonbib/#congestion-longpaths)). But the fix for infinite-length paths introduced a [problem with accessing hidden services](https://trac.torproject.org/projects/tor/ticket/1038), and one of the side effects of our fix for bug 1038 was that while we limit the number of outbound (away from the client) "relay early" cells on a circuit, we [don't limit](https://lists.torproject.org/pipermail/tor-commits/2009-July/014679.html) the number of inbound (towards the client) relay early cells.

So in summary, when Tor clients contacted an attacking relay in its role as a Hidden Service Directory to publish or retrieve a hidden service descriptor (steps 2 and 3 on [the hidden service protocol diagrams](https://www.torproject.org/docs/hidden-services)), that relay would send the hidden service name (encoded as a pattern of relay and relay-early cells) back down the circuit. Other attacking relays, when they get chosen for the first hop of a circuit, would look for inbound relay-early cells (since nobody else sends them) and would thus learn which clients requested information about a hidden service.

There are three important points about this attack:

**A)** The attacker encoded the name of the hidden service in the injected signal (as opposed to, say, sending a random number and keeping a local list mapping random number to hidden service name). The encoded signal is encrypted as it is sent over the TLS channel between relays. However, this signal would be easy to read and interpret by anybody who runs a relay and receives the encoded traffic. And we might also worry about a global adversary (e.g. a large intelligence agency) that records Internet traffic at the entry guards and then tries to break Tor's link encryption. The way this attack was performed weakens Tor's anonymity against these other potential attackers too — either while it was happening or after the fact if they have traffic logs. So if the attack was a research project (i.e. not intentionally malicious), it was deployed in an irresponsible way because it puts users at risk indefinitely into the future.

(This concern is in addition to the general issue that it's probably unwise from a legal perspective for researchers to attack real users by modifying their traffic on one end and wiretapping it on the other. Tools like [Shadow](http://shadow.github.io/) are great for testing Tor research ideas out in the lab.)

**B)** This protocol header signal injection attack is actually pretty neat from a research perspective, in that it's a bit different from previous tagging attacks which targeted the application-level payload. Previous tagging attacks modified the payload at the entry guard, and then looked for a modified payload at the exit relay (which can see the decrypted payload). Those attacks don't work in the other direction (from the exit relay back towards the client), because the payload is still encrypted at the entry guard. But because this new approach modifies ("tags") the cell headers rather than the payload, every relay in the path can see the tag.

**C)** We should remind readers that while this particular variant of the traffic confirmation attack allows high-confidence and efficient correlation, the general class of passive (statistical) traffic confirmation attacks remains unsolved and would likely have worked just fine here. So the good news is traffic confirmation attacks aren't new or surprising, but the bad news is that they still work. See [https://blog.torproject.org/blog/one-cell-enough](https://blog.torproject.org/blog/one-cell-enough "https://blog.torproject.org/blog/one-cell-enough") for more discussion.

Then the second class of attack they used, in conjunction with their traffic confirmation attack, was a standard [Sybil attack](http://en.wikipedia.org/wiki/Sybil_attack) — they signed up around 115 fast non-exit relays, all running on 50.7.0.0/16 or 204.45.0.0/16. Together these relays summed to about 6.4% of the Guard capacity in the network. Then, in part because of our current [guard rotation parameters](https://blog.torproject.org/blog/improving-tors-anonymity-changing-guard-parameters), these relays became entry guards for a significant chunk of users over their five months of operation.

We actually noticed these relays when they joined the network, since the [DocTor](https://gitweb.torproject.org/doctor.git) scanner [reported them](https://lists.torproject.org/pipermail/tor-consensus-health/2014-January/004134.html). We considered the set of new relays at the time, and made a decision that it wasn't that large a fraction of the network. It's clear there's room for improvement in terms of how to let the Tor network grow while also ensuring we maintain social connections with the operators of all large groups of relays. (In general having a widely diverse set of relay locations and relay operators, yet not allowing any bad relays in, seems like a hard problem; on the other hand our detection scripts did notice them in this case, so there's hope for a better solution here.)

In response, we've taken the following short-term steps:

**1)** Removed the attacking relays from the network.

**2)** Put out a software update for relays to prevent "relay early" cells from being used this way.

**3)** Put out a software update that will (once enough clients have upgraded) let us tell clients to move to using one entry guard rather than three, to reduce exposure to relays over time.

**4)** Clients can tell whether they've received a relay or relay-cell. For expert users, the new Tor version warns you in your logs if a relay on your path injects any relay-early cells: look for the phrase "Received an inbound RELAY\_EARLY cell".

The following longer-term research areas remain:

**5)** Further growing the Tor network and diversity of relay operators, which will reduce the impact from an adversary of a given size.

**6)** Exploring better mechanisms, e.g. social connections, to limit the impact from a malicious set of relays. We've also formed a group to pay more attention to suspicious relays in the network:
 [https://blog.torproject.org/blog/how-report-bad-relays](https://blog.torproject.org/blog/how-report-bad-relays "https://blog.torproject.org/blog/how-report-bad-relays")

**7)** Further reducing exposure to guards over time, perhaps by extending the guard rotation lifetime:
 [https://blog.torproject.org/blog/lifecycle-of-a-new-relay](https://blog.torproject.org/blog/lifecycle-of-a-new-relay "https://blog.torproject.org/blog/lifecycle-of-a-new-relay")
 [https://blog.torproject.org/blog/improving-tors-anonymity-changing-guard...](https://blog.torproject.org/blog/improving-tors-anonymity-changing-guard-parameters "https://blog.torproject.org/blog/improving-tors-anonymity-changing-guard-parameters")

**8)** Better understanding statistical traffic correlation attacks and whether padding or other approaches can mitigate them.

**9)** Improving the hidden service design, including making it harder for relays serving as hidden service directory points to learn what hidden service address they're handling:
 [https://blog.torproject.org/blog/hidden-services-need-some-love](https://blog.torproject.org/blog/hidden-services-need-some-love "https://blog.torproject.org/blog/hidden-services-need-some-love")

## OPEN QUESTIONS:

**Q1)** Was this the Black Hat 2014 talk that got canceled recently?
**Q2)** Did we find all the malicious relays?
**Q3)** Did the malicious relays inject the signal at any points besides the HSDir position?
**Q4)** What data did the attackers keep, and are they going to destroy it? How have they protected the data (if any) while storing it?

Great questions. We spent several months trying to extract information from the researchers who were going to give the Black Hat talk, and eventually we did get some hints from them about how "relay early" cells could be used for traffic confirmation attacks, which is how we started looking for the attacks in the wild. They haven't answered our emails lately, so we don't know for sure, but it seems likely that the answer to Q1 is "yes". In fact, we hope they \*were\* the ones doing the attacks, since otherwise it means somebody else was. We don't yet know the answers to Q2, Q3, or Q4.

