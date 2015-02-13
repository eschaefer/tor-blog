---
layout: post
title: "Tor 0.2.2.7-alpha released"
permalink: tor-0227-alpha-released
date: 2010-01-23 07:48:28
author: phobos
category: blog
status: closed
tags: ["bug fixes", "deprecated features", "feature enhancements", "performance enhancements", "security critical", "security fixes"]
---

alpha fixes a huge client-side performance bug, as well  
 as laying the groundwork for further relay-side performance fixes. It  
 also starts cleaning up client behavior with respect to the EntryNodes,  
 ExitNodes, and StrictNodes config options.

This release also rotates two directory authority keys, due to a security  
 breach of some of the Torproject servers:  
 [http://archives.seul.org/or/talk/Jan-2010/msg00161.html](http://archives.seul.org/or/talk/Jan-2010/msg00161.html "http://archives.seul.org/or/talk/Jan-2010/msg00161.html")

Everybody should upgrade:  
 [https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

Changes in version 0.2.2.7-alpha - 2010-01-19  
 o Directory authority changes:  
 - Rotate keys (both v3 identity and relay identity) for moria1  
 and gabelmoo.

o Major features (performance):  
 - We were selecting our guards uniformly at random, and then weighting  
 which of our guards we'd use uniformly at random. This imbalance  
 meant that Tor clients were severely limited on throughput (and  
 probably latency too) by the first hop in their circuit. Now we [**read more »**](https://blog.torproject.org/blog/tor-0227-alpha-released)
