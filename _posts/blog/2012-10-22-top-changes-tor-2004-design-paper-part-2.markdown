---
layout: post
title: "Top changes in Tor since the 2004 design paper (Part 2)"
permalink: top-changes-tor-2004-design-paper-part-2
date: 2012-10-22
author: nickm
category: blog
tags: []
---

This is part 2 of Nick Mathewson and Steven Murdoch's series on what has changed in Tor's design since the original design paper in 2004. [Part one is back over here.](https://blog.torproject.org/blog/top-changes-tor-2004-design-paper-part-1)

In this installment, we cover changes in how we pick and use nodes in our circuits, and general anticensorship features.

## 5. Guard nodes

We assume, based on a fairly large body of research, that if an attacker controls or monitors the first hop and last hop of a circuit, then the attacker can de-anonymize the user by correlating timing and volume information. Many of the security improvements to path selection discussed in this post concentrate on reducing the probability that an attacker can be in this position, but no reasonably efficient proposal can eliminate the possibility.

Therefore, each time a user creates a circuit, there is a small chance that the circuit will be compromised. However, most users create a large number of Tor circuits, so with the original path selection algorithm, these small chances would build up into a potentially large chance that at least one of their circuits will be compromised.

To help improve this situation, in Tor 0.1.1.2-alpha, the guard node feature was implemented (initially called "helper nodes", invented by [Wright, Adler, Levine, and Shields](http://people.cs.umass.edu/~mwright/papers/wright-passive.pdf) and proposed for use in Tor by [Øverlier and Syverson](http://www.onion-router.net/Publications/locating-hidden-servers.pdf)). In Tor 0.1.1.11-alpha it was enabled by default. Now, the Tor client picks a few Tor nodes as its "guards", and uses one of them as the first hop for all circuits (as long as those nodes remain operational).

This doesn't affect the probability that the first circuit is compromised, but it does mean that if the guard nodes chosen by a user are not attacker-controlled all their future circuits will be safe. On the other hand, users who choose attacker-controlled guards will have about M/N of their circuits compromised, where M is the amount of attacker-controlled network resource and N is the total network resource. Without guard nodes every circuit has a (M/N)<sup>2</sup> probability of being compromised.

Essentially, the guard node approach recognises that some circuits are going to be compromised, but it's better to increase your probability of having **no** compromised circuits at the expense of also increasing the proportion of your circuits that will be compromised if any of them are. This is because compromising a fraction of a user's circuits—sometimes even just one—can be enough to compromise a user's anonymity. For users who have good guard nodes, the situation is much better, and for users with bad guard nodes the situation is not much worse than before.

## 6. Bridges, censorship resistance, and pluggable transports

While Tor was originally designed as an anonymous communication system, more and more users need to circumvent censorship rather than to just preserve their privacy. The two goals are closely linked – to prevent a censor from blocking access to certain websites, it is necessary to hide where a user is connecting to. Also, many censored Internet users live in repressive regimes which might punish people who access banned websites, so here anonymity is also of critical importance.

However, anonymity is not enough. Censors can't block access to certain websites browsed over Tor, but it was easy for censors to block access to the whole of the Tor network in the original design. This is because there were a handful of directory authorities which users needed to connect to before they could discover the addresses of Tor nodes, and indeed some censors blocked the directory authorities. Even if users could discover the current list of Tor nodes, censors also blocked the IP addresses of all Tor nodes too.

Therefore, the [Tor censorship resistance design](https://svn.torproject.org/svn/projects/design-paper/blocking.html) introduced bridges – special Tor nodes which were not published in the directory, and could be used as entry points to the network (both for downloading the directory and also for building circuits). Users need to find out about these somehow, so the bridge authority collects the IP addresses and gives them out via email, on the web, and via personal contacts, so as to make it difficult for the censor to enumerate them all.

That's not enough to provide censorship resistance though. Preventing the censor from knowing all the IP addresses they need to block to block access to the Tor network will be enough to defeat some censors. But others have the capability to block not only by IP address but also by content (deep packet inspection). Some censors have tried to do this already and Tor has, in response, gradually changed its TLS handshake to better imitate web browsers.

Impersonating web browsers is difficult, and even if Tor perfectly impersonated one, some censors could just block encrypted web browsing (like Iran did, for some time). So it would be better if Tor could impersonate multiple protocols. Even better would be if other people could contribute to this goal, rather than the Tor developers being a bottleneck. This is the motivation of the [pluggable transports](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/180-pluggable-transport.txt) design which allows Tor to manage an external program which transforms Tor traffic into some hard-to-fingerprint obfuscation.

## 7. Changes and complexities in our path selection algorithms

The original Tor paper never specified how clients should pick which nodes to use when constructing a circuit through the network. This question has proven unexpectedly complex.

### Weighting node selection by bandwidth

The simplest possible approach to path construction, which we used in the earliest versions of Tor, is simply to pick uniformly at random from all advertised nodes that could be used for a given position in the path. But this approach creates terrible bandwidth bottlenecks: a server that would allow 10x as many bytes per second as another would still get the same number of circuits constructed through it.

Therefore, Tor 0.0.8rc1 started to have clients weight their choice of nodes by servers' advertised bandwidths, so that a server with 10x as much bandwidth would get 10x as many circuits, and therefore (probabilistically) 10x as much of the traffic.

(In the original paper, we imagined that we might take Morphmix's approach, and divide nodes into "bandwidth classes", such that clients would choose only from among nodes having at least the same approximate bandwidth as the clients. This may be a good design for peer-to-peer anonymity networks, but it doesn't seem to work for the Tor network: the most useful high-capacity nodes have more capacity than nearly any typical client.)

Later, it proved that weighting by bandwidth was also suboptimal, because of nonuniformity in path selection rules. Consider that if node A is suitable for use at any point in a circuit, but node B is suitable only as the middle node, then node A will be considered for use three times as often as B. If the two nodes have equal bandwidth, node A will be chosen three times as often, leading to it being overloaded in comparison with B. So eventually, in Tor 0.2.2.10-alpha, we moved to a more sophisticated approach, where nodes are chosen proportionally to their bandwidth, as weighted by an algorithm to optimize load-balancing between nodes of different capabilities.

### Bandwidth authorities

Of course, once you choose nodes with unequal probability, you open the possibility of an attacker trying to see a disproportionate number of circuits -- not by running an extra-high number of nodes -- but by claiming to have a very large bandwidth.

For a while, we tried to limit the impact of this attack by limiting the maximum bandwidth that a client would believe, so that a single rogue node couldn't just claim to have infinite bandwidth.

In 0.2.1.17-rc, clients switched from using bandwidth values advertised by nodes themselves to using values published in the network status consensus document. A subset of the authorities measure and vote on nodes' observed bandwidth, to prevent misbehaving nodes from claiming (intentionally or accidentally) to have too much capacity.

### Avoiding duplicate families in a single circuit

As mentioned above, if the first and last node in a circuit are controlled by an adversary, they can use traffic correlation attacks to notice that the traffic entering the network at the first hop matches traffic leaving the circuit at the last hop, and thereby trace a client's activity with high probability. Research on preventing this attack has not yet come up with any affordable, effective defense suitable for use in a low-latency anonymity network. Therefore, the most promising mitigation strategies seem to involve lowering the attacker's chances of controlling both ends of a circuit.

To this end, clients do not use any two nodes in a circuit whose IP addresses are in the same /16 – when we designed the network, it was marginally more difficult to acquire a large number of disparate addresses than it was to get a large number of concentrated addresses. (Roger and Nick may have been influenced by their undergraduacy at MIT, where their dormitory occupied the entirety of 18.244.0.0/16.) This approach is imperfect, but possibly better than nothing.

To allow honest node operators to run more than one server without inadvertently giving themselves the chance to see more traffic than they should, we also allow nodes to declare themselves to be members of the same "family", such that a client won't use two nodes in the same family in the same circuit. (Clients only believe mutual family declarations, so that an adversary can't capture routes by having his nodes claim unilaterally to be in a family with every node the adversary _doesn't_ control.)

## 8. Stream isolation

Building a circuit is fairly expensive (in terms of computation and bandwidth) for the network, and the setup takes time, so the Tor client tries to re-use existing circuits if possible, by sending multiple TCP streams down them. Streams which share a circuit are linkable, because the exit node can tell that they have the same circuit ID. If the user sends some information on one stream which gives their identity away, the other streams on the same circuit will be de-anonymized.

To reduce the risk of this occurring, Tor will not re-use a circuit which the client first used more than 10 minutes ago. Users can also use their Tor controller to send the "NEWNYM" signal, preventing any old circuits being used for new streams. As long as users don't mix anonymous and non-anoymous tasks at the same time, this form of circuit re-use is probably a good tradeoff.

However, [Manils et al.](http://hal.inria.fr/docs/00/47/15/56/PDF/TorBT.pdf) discovered that some Tor users simultaneously ran BitTorrent over the same Tor client as they did web browsing. Running BitTorrent over Tor is a bad idea because the network can't handle the load, and because BitTorrent packets include the user's real IP address in the payload, so it isn't anonymous. But running BitTorrent while doing anonymous web browsing is an especially bad idea. An exit node can find the user's IP address in the BitTorrent payload then trivially de-anonymize all streams sharing the circuit.

Running BitTorrent over Tor is still strongly discouraged, but this paper did illustrate some potential problems with circuit reuse so [proposal 171](https://gitweb.torproject.org/torspec.git/blob/master:/proposals/171-separate-streams.txt) was written, and implemented in Tor 0.2.3.3-alpha, to help isolate streams which shouldn't share the same circuit. By default streams which were initiated by different clients, which came from SOCKS connections with different authentication credentials, or which came to a different SOCKS port on the Tor client, are separated. In this way, a user can isolate applications by either setting up multiple SOCKS ports on Tor and using one per application, or by setting up a single SOCKS port but using different username/passwords for each application. Tor can also be configured to isolate streams based on destination address and/or port.

