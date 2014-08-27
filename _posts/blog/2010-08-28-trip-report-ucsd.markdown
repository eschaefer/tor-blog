---
layout: post
title: "Trip report, UCSD"
permalink: trip-report-ucsd
date: 2010-08-28
author: arma
category: blog
tags: []
---

On Sunday (8/22) through Wednesday (8/25), I visited the Tor research group at [UCSD](http://www-cse.ucsd.edu/) as part of my ongoing plans to help academic research groups [better understand Tor and its research problems](https://www.torproject.org/research). Damon McCoy has a fellowship (postdoc) there for last year and this coming year, and he's brought Kevin Bauer in from UColorado from now until December. They have two systems profs with congestion control background (Stefan Savage and Geoff Voelker) interested in helping them work on Tor and performance.

Kevin is planning to spend the next year on Tor performance work, as the last chapter of his thesis. He's also applied to [Ian Goldberg's postdoc position at Waterloo](https://blog.torproject.org/blog/tor-related-research-positions-university-waterloo). He seems like a smart and dedicated guy; I'd be excited if Ian picks him.

I spent most of my time walking Damon and Kevin through Tor's current congestion control levels -- explaining what Tor does, as well as what I think is actually resulting from each of these components. Kevin has lots of notes, and if all goes well that will seed the core of a "Why else is Tor slow" whitepaper over the coming months, as a sequel to [the original](https://blog.torproject.org/blog/why-tor-is-slow).

Kevin wants to work on figuring out how to better tune all the knobs Tor has, but he also wants to work on a new design for an ipsec-based Tor protocol (we ruled out DTLS as not being in broad enough use; that leaves ipsec). I want both, so I'd be fine with either one. The UCSD systems group has a simulation engine called [ModelNet](https://modelnet.sysnet.ucsd.edu/) that is apparently really good at simulating actual networks. Kevin is going to try to get a separate Tor network going with modelnet as its glue, and then he'll be in a better position to do more controlled experiments.

At the same time I think he'd be in better shape thinking about Tor performance if he messes around with a live Tor relay enough to figure out where its bottlenecks are. I gave him a list of 10 or so potential problems, and each of them is probably a big problem in some contexts (e.g. under certain amounts of load) but maybe not in others. The current intuition is that Tor has grown a lot of knobs that may be orthogonal to whether we are using TCP or something else as transport, and analyzing the performance of a naive design that uses something else as transport but doesn't consider the knobs will likely result in a bad comparison. To say it differently, some of the knobs we have now (e.g. circuit priorities) would still be useful even if we change our transport, but others might no longer be needed, or might need to be different. Many fine open research questions.

I also got a chance to explain enough of Tor to Stefan that he has a good understanding of Tor's overall design. He's still digesting what advice he might have for us, but his initial impression is that it's not clear that end-to-end TCP will perform well for our situation, nor is it clear that thousands of parallel TCP sessions between each pairwise Tor relay over UDP over some datagram link encryption ( [Joel Reardon's design](http://freehaven.net/anonbib/#reardon-thesis)) will perform well either.

While there, I did a CSE symposium talk that went very well:  
 [http://freehaven.net/~arma/slides-ucsd10.pdf](http://freehaven.net/~arma/slides-ucsd10.pdf "http://freehaven.net/~arma/slides-ucsd10.pdf")  
It was scheduled for an hour, but everybody stayed for 90 minutes, and the crowd was really excited. I invited Chris Davis to the talk, plus the lunch afterward, plus some of the brainstorming after that. Hopefully a better-informed Chris will come in handy in some way in the future. :)

I also talked to Mihir Bellare, a well-known crypto prof, for a few hours. He had a postdoc and a grad student who were excited to learn more about our research problems. Maybe they will help Damon and Kevin redesign a packet-based encryption scheme (where you send an IV and checksum in every packet, to tolerate lost packets and out-of-order packets), like what [Freedom](http://freehaven.net/anonbib/#freedom21-security) designed long ago but never shared very well with the rest of the world.

I also had dinner with KC Claffy, one of the people from [CAIDA](http://www.caida.org/home/), a separate org affiliated with UCSD that focuses on Internet data measurement and the privacy/security/policy/analysis issues that go along with that. She was really interested to learn more about our [WECSR workshop paper](http://metrics.torproject.org/papers.html). One of the deliverables they've promised their funders soon is a comparison of various GeoIP databases. I told her about Karsten's [preliminary work there](http://metrics.torproject.org/papers/geoipdbcomp-2009-10-23.pdf), and I should probably follow up.

I met with Harsha Madhyastha, a soon-to-be-first-year-prof at UC Riverside, who wrote "iPlane" as his thesis. [iPlane](http://iplane.cs.washington.edu/) is a database / set of scripts that let you (among other things) predict latency between two points on the Internet. I gave him a big pile of research questions around choosing more efficient paths through the Tor network vs the anonymity implications of even-less-uniform path selection; and the AS-level or country-level path selection questions; and [Nick Hopper's latency attack paper](http://freehaven.net/anonbib/#tissec-latency-leak) and the questions we still have around it. Perhaps one of his grad students will pick up one of the topics.

Overall, it was a good use of a couple of days. I'll plan to follow-up in person sometime in the next 6-12 months, either with a trip to UCSD or a trip to Colorado (where Kevin is returning after his brief stint as research staff).

I should get my act together and answer Nick Hopper's invitation to come spend a similar couple of days at UMN, to get his research group more [up to speed](https://www.torproject.org/research) on what needs doing.

