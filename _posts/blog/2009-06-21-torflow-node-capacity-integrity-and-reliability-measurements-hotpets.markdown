---
layout: post
title: "TorFlow Node Capacity, Integrity and Reliability Measurements at HotPETS"
permalink: torflow-node-capacity-integrity-and-reliability-measurements-hotpets
date: 2009-06-21
author: mikeperry
category: blog
tags: ["performance", "research"]
---

[Like Karsten](https://blog.torproject.org/blog/measuring-tor-network-public-directory-information), I too am presenting at [HotPETS](http://petsymposium.org/2009/hotpets.php) in Seattle in August. My presentation will cover my work with my [TorFlow suite](https://svn.torproject.org/svn/torflow/trunk/) - a python library and utility set to assist measuring and adjusting performance on the Tor network, and to scan the network for malfunctioning and misbehaving exits.

One of the highlights is a system for [performance feedback](https://git.torproject.org/checkout/tor/master/doc/spec/proposals/160-bandwidth-offset.txt): a set of [training wheels of sorts](https://git.torproject.org/checkout/tor/master/doc/spec/proposals/161-computing-bandwidth-adjustments.txt) for Tor's load balancing algorithms that once deployed, should greatly improve the performance of the network for 0.2.1 clients. I am very much excited about this and am looking forward to throwing the switch on it in the coming weeks.

Also of note is the discovery that nodes that use Tor's built in rate-limiting are far less likely to fail circuits than those that do not, especially for Windows nodes. So if you are a Windows node operator, please rate limit your node slightly below your connection's capacity using either the Vidalia GUI or the BandwidthRate torrc config option.. I will be emailing the contact info addresses of nodes that are most affected by this soon.

The [paper for the presentation](http://fscked.org/talks/TorFlow-HotPETS-final.pdf) describes the library, utilities, and their results in much further detail.

