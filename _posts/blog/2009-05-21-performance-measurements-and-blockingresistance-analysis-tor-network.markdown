---
layout: post
title: "Performance measurements and blocking-resistance analysis in the Tor network"
permalink: blog/performance-measurements-and-blockingresistance-analysis-tor-network
date: 2009-05-21
author: karsten
category: blog
tags: ["censorship circumvention", "performance", "research"]
---

The Tor network has grown to more than one thousand relays and millions of casual users over the past few years. We are proud of our network's popularity, but with growth has come increasing [performance problems](https://blog.torproject.org/blog/why-tor-is-slow) and attempts by some countries to block access to the Tor network. In order to address these problems, we need to learn more about the Tor network. In this post, I describe the current state of network measurements in Tor and some proposed additions to help us understand the network better.

Right now, relays, [bridges](https://www.torproject.org/bridges), and directories gather the following data for statistical purposes:

- Relays and bridges count the number of bytes that they have pushed in 15-minute intervals over the past 24 hours. They include these data in extra-info documents that they send to the directory authorities whenever they publish their server descriptor. See Figure 3 in the [analysis of directory archives](http://git.torproject.org/checkout/metrics/master/report/dirarch/dirarch-2009-03-31.pdf) that shows that roughly half of the available bandwidth capacity is utilized.
- Bridges further include a rough number of clients per country that they have seen in the past 48 hours in their extra-info documents. We [added this feature](http://git.torproject.org/checkout/tor/master/doc/spec/proposals/126-geoip-reporting.txt) in [version 0.2.0.13-alpha](http://git.torproject.org/checkout/tor/master/ChangeLog) to help us learn when a given country is trying to block connections to bridges. It also lets us understand bridge adoption better: see for an example an analysis of [bridge users by countries](http://git.torproject.org/checkout/metrics/master/report/bridges/bridges-2009-04-04.pdf).
- Directories since version [0.2.1.1-alpha](http://git.torproject.org/checkout/tor/master/ChangeLog) can be configured to count the number of clients they see per country in the past 24 hours and to write them to a local file. We have used these data in the past to [estimate](http://git.torproject.org/checkout/tor/master/doc/spec/proposals/ideas/xxx-geoip-survey-plan.txt) total [numbers](http://git.torproject.org/checkout/metrics/master/report/dirreq/directory-requests-2009-04-23.2.pdf) and [origins of clients](http://git.torproject.org/checkout/metrics/master/report/dirreq/dirreq-report-2009-04-30.pdf).

It turns out that we need to learn more about the Tor network to make it more useful for everyone. In particular, we are trying to identify performance bottlenecks and want to be ready to notice if any countries start blocking access to the Tor network. Therefore, I am planning to extend network measurements by the following kinds of data:

- Entry guards should count the number of clients per country seen in the past 24 hours and include these numbers in their extra-info documents. These data are similar to what bridges already gather about their clients as well as directories if configured accordingly. (Remember, because Tor paths are more than one hop, the entry guard knows you are using Tor but does not know anything about your destinations.) We need country counts from entry guards to learn how many clients are connected to a single entry guard and if there are or start to be any restrictions for clients connecting from specific countries.
- Relays should determine statistics about the number of bytes and cells waiting in their local queues and report them to the directory authorities in their extra-info documents. We need to [learn more](http://archives.seul.org/or/dev/Apr-2009/msg00007.html) about buffer sizes of relays at various loads to identify current and future performance problems and fix them.
- Exit nodes should include the number of bytes and streams they pushed over the past 24 hours broken down by exiting port in their extra-info documents. These data are important for us to identify load-balancing problems with respect to [exit policies](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#RunARelayBut).

These approaches have been designed so that none of the network data can be used to deanonymize our users. All network data are aggregated before being uploaded to the directory authorities: client addresses are resolved to countries, added up over at least 24 hours, and rounded up to the next multiple of a fixed number (currently 8). All network data should be made available via the directories just as the current statistical data can be obtained from downloading extra-info documents. The details of the network measurements as outlined here will be specified in [proposals](http://git.torproject.org/checkout/tor/master/doc/spec/proposals/001-process.txt) and discussed on the [developer mailing list](http://archives.seul.org/or/dev/). You can check out our results on the [metrics project page](https://www.torproject.org/projects/metrics) as we make progress.

We are excited to finally start tackling the performance problems and to prepare ourselves to notice when countries start blocking access to the Tor network. We would love to have help from the rest of the research community in discussing safe ways to measure the described network data and to analyze them later on.

