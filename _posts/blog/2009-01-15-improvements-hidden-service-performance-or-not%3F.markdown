---
layout: post
title: "Improvements on Hidden Service Performance -- or not?"
permalink: blog/improvements-hidden-service-performance-or-not%3F
date: 2009-01-15
author: karsten
category: blog
tags: ["hidden services", "performance"]
---

During the past eight months we have been trying pretty hard to improve hidden service performance. This work was part of the project to [Speed Up Tor Hidden Services](https://www.torproject.org/projects/hidserv.html), generously funded by the NLnet Foundation. As of today, we know that we have succeeded in our attempts -- well, or not?

We started in June 2008 by measuring how long it takes until hidden services are registered in the network, how long it takes for clients to connect to them, and similar metrics. An [analysis](http://freehaven.net/~karsten/hidserv/perfanalysis-2008-06-15.pdf) of these data revealed what problems could be responsible for the experienced delays: First of all, we found in total 10 bugs, some of them delaying hidden services significantly. These bugs are now fixed in the 0.2.1.x series (and the major bugs also in the 0.2.0.x series). Second, we identified certain substeps as the bottlenecks of the hidden service protocol, all of them related to building circuits on demand. We proposed a few design changes to overcome these bottlenecks by reducing circuit-build timeouts or by building circuits in parallel. These design changes have been [discussed](http://freehaven.net/~karsten/hidserv/discussion-2008-07-15.pdf), [evaluated](http://freehaven.net/~karsten/hidserv/design-2008-08-15.pdf), [specified](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/155-four-hidden-service-improvements.txt), and finally implemented in the 0.2.1.x series.

As of today, we know that we were successful in our attempts -- well, at least in parts. In December 2008, we performed a second set of measurements with a Tor version that had all bugfixes and design changes. Today we finished the analysis of these new data by [comparing](http://freehaven.net/~karsten/hidserv/comparison-2009-01-15.pdf) them with the June data. We found that the time until hidden services are advertised in the network halved from 2:12 minutes to 58 seconds in the mean. This improvement is by far better than we had expected. With this improvement we might even think about reducing an internal descriptor stabilization time from 30 seconds to a lower value, which would further reduce service publication time. However, we also found that the time that clients need to wait while connecting to hidden services remained unchanged at 56 seconds in the mean. Even though our design changes were effective, the [distributed storage](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/114-distributed-storage.txt) for hidden service descriptors has counter-balanced all gains achieved here. This deteriorating effect was not expected when we started. In the future, we should therefore focus on speeding up downloads from the distributed hidden service directory, for example by parallelizing requests.

All in all, these improvements are an important step in making hidden services faster. Now we know pretty well what the main problem of hidden services is: on-demand circuit building. Of course, this problem is not specific to hidden services, but a general problem of Tor. Fortunately, hidden services would benefit from all improvements that are made to circuit building in Tor. In the future we are focusing on improvements to circuit building in general.

