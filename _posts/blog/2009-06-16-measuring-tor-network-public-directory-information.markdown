---
layout: post
title: "Measuring the Tor Network from Public Directory Information"
permalink: blog/measuring-tor-network-public-directory-information
date: 2009-06-16
author: karsten
category: blog
tags: ["censorship circumvention", "performance", "research"]
---

On this year's [HotPETs workshop](http://petsymposium.org/2009/hotpets.php) (August 5-7 in Seattle, WA, USA) I'm going to present some results on [Measuring the Tor Network from Public Directory Information](http://freehaven.net/~karsten/metrics/measuring-tor-public-dir-info-final.pdf). The main idea is to observe trends in the Tor network without having to measure any data other than [public directory information](https://git.torproject.org/checkout/tor/master/doc/spec/dir-spec.txt). These data are there anyway as they are required for clients to make good path selection decisions and build circuits. The results of this paper reveal problems in the current Tor network that need to be addressed, e.g., by [lowering requirements for assigning certain flags](https://git.torproject.org/checkout/metrics/master/report/dirarch/flagrequirements-2009-04-11.pdf), facilitating the upgrade process, improving support for dynamic IP addresses, possibly calculating bandwidth capacity more reliably, and clarifying legal issues for running relays in view of data retention laws. The next step in understanding the problems of the Tor network requires an [extension of network measurements](https://blog.torproject.org/blog/performance-measurements-and-blockingresistance-analysis-tor-network) to improve [performance](https://blog.torproject.org/blog/why-tor-is-slow) and blocking-resistance of Tor.

