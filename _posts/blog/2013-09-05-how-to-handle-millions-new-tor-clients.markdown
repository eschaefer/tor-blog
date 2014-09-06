---
layout: post
title: "How to handle millions of new Tor clients"
permalink: blog/how-to-handle-millions-new-tor-clients
date: 2013-09-05
author: arma
category: blog
tags: []
---

[**tl;dr** : if you want your Tor to be more stable, upgrade to a Tor Browser Bundle with Tor 0.2.4.x in it, and then wait for enough relays to upgrade to today's 0.2.4.17-rc release.]

Starting around August 20, we started to see a sudden spike in the number of Tor clients. By now it's unmistakable: there are millions of new Tor clients and the numbers continue to rise:

![Tor users in summer 2013](https://people.torproject.org/~arma/direct-users-2013-07-07-2013-09-04.png)

Where do these new users come from? My current best answer is a botnet.

Some people have speculated that the growth in users comes from activists in Syria, Russia, the United States, or some other country that has good reason to have activists and journalists adopting Tor en masse lately. Others have speculated that it's due to massive adoption of the Pirate Browser (a Tor Browser Bundle fork that discards most of Tor's security and privacy features), but we've talked to the Pirate Browser people and the downloads they've seen can't account for this growth. The fact is, with a growth curve like this one, there's basically no way that there's a new human behind each of these new Tor clients. These Tor clients got bundled into some new software which got installed onto millions of computers pretty much overnight. Since no large software or operating system vendors have come forward to tell us they just bundled Tor with all their users, that leaves me with one conclusion: somebody out there infected millions of computers and as part of their plan they installed Tor clients on them.

It doesn't look like the new clients are using the Tor network to send traffic to external destinations (like websites). Early indications are that they're accessing hidden services — fast relays see "Received an ESTABLISH\_RENDEZVOUS request" many times a second in their info-level logs, but fast exit relays don't report a significant growth in exit traffic. One plausible explanation (assuming it is indeed a botnet) is that it's running its [Command and Control (C&C)](http://en.wikipedia.org/wiki/Botnet#Organization) point as a hidden service.

My first observation is "holy cow, the network is still working." I guess all that work we've been doing on scalability was a good idea. The second observation is that these new clients actually aren't adding that much traffic to the network. Most of the pain we're seeing is from all the new circuits they're making — Tor clients build circuits preemptively, and millions of Tor clients means millions of circuits. Each circuit requires the relays to do expensive public key operations, and many of our relays are now maxed out on CPU load.

There's a possible dangerous cycle here: when a client tries to build a circuit but it fails, it tries again. So if relays are so overwhelmed that they each drop half the requests they get, then more than half the attempted circuits will fail (since all the relays on the circuit have to succeed), generating even more circuit requests.

So, how do we survive in the face of millions of new clients?

Step one was to see if there was some simple way to distinguish them from other clients, like checking [if they're using an old version of Tor](https://trac.torproject.org/projects/tor/ticket/9653), and have entry nodes refuse connections from them. Alas, it looks like they're running 0.2.3.x, which is the current recommended stable.

Step two is to get more users using the [NTor circuit-level handshake](https://gitweb.torproject.org/tor.git/blob/refs/tags/tor-0.2.4.17-rc:/ChangeLog#l769), which is new in Tor 0.2.4 and offers stronger security with lower processing overhead (and thus less pain to relays). Tor 0.2.4.17-rc comes with an added twist: we [prioritize](https://trac.torproject.org/projects/tor/ticket/9574) NTor create cells over the old [TAP](http://freehaven.net/anonbib/date.html#tap:pet2006) create cells that 0.2.3 clients send, which a) means relays will get the cheap computations out of the way first so they're more likely to succeed, and b) means that Tor 0.2.4 users will jump the queue ahead of the botnet requests. The Tor 0.2.4.17-rc release also comes with some new log messages to [help relay operators track how many of each handshake type they're handling](https://trac.torproject.org/projects/tor/ticket/9658).

(There's some tricky calculus to be done here around whether the botnet operator will upgrade his bots in response. Nobody knows for sure. But hopefully not for a while, and in any case the new handshake is a lot cheaper so it would still be a win.)

Step three is to temporarily disable some of the client-side performance features that build extra circuits. In particular, our [circuit build timeout](https://gitweb.torproject.org/tor.git/blob/tor-0.2.4.17-rc:/ReleaseNotes#l1764) feature estimates network performance for each user individually, so we can tune which circuits we use and which we discard. First, in a world where successful circuits are rare, discarding some — even the slow ones — might be unwise. Second, to arrive at a good estimate faster, clients make a series of throwaway measurement circuits. And if the network is ever flaky enough, clients discard that estimate and go back and measure it again. These are all fine approaches in a network where most relays can handle traffic well; but they can contribute to the above vicious cycle in an overloaded network. The next step is to [slow down these exploratory circuits](https://trac.torproject.org/projects/tor/ticket/9670) in order to reduce the load on the network. (We would temporarily disable the circuit build timeout feature entirely, but it turns out we had a [bug where things get worse in that case](https://trac.torproject.org/projects/tor/ticket/9671).)

Step four is longer-term: there remain some [NTor handshake performance improvements](https://trac.torproject.org/projects/tor/ticket/9662) that will make them faster still. It would be nice to get circuit handshakes on the relay side to be really cheap; but it's an open research question how close we can get to that goal while still providing strong handshake security.

Of course, the above steps aim only to get our head back above water for this particular incident. For the future we'll need to explore further options. For example, we could rate-limit circuit create requests at entry guards. Or we could learn to recognize the circuit building signature of a bot client (maybe it triggers a new hidden service rendezvous every n minutes) and refuse or [tarpit](http://en.wikipedia.org/wiki/Tarpit_%28networking%29) connections from them. Maybe entry guards should demand that clients solve captchas before they can build more than a threshold of circuits. Maybe we rate limit TAP handshakes at the relays, so we leave more CPU available for other crypto operations like TLS and AES. Or maybe we should immediately refuse all TAP cells, effectively shutting 0.2.3 clients out of the network.

In parallel, it would be great if botnet researchers would identify the particular characteristics of the botnet and start looking at ways to shut it down (or at least get it off of Tor). Note that getting rid of the C&C point may not really help, since it's the rendezvous attempts from the bots that are hurting so much.

And finally, I still maintain that if you have a multi-million node botnet, it's silly to try to hide it behind the 4000-relay Tor network. These people should be using their botnet as a peer-to-peer anonymity system for itself. So I interpret this incident as continued exploration by botnet developers to try to figure out what resources, services, and topologies integrate well for protecting botnet communications. Another facet of solving this problem long-term is helping them to understand that Tor isn't a great answer for their problem.

