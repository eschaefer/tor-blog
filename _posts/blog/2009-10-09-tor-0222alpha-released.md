---
layout: post
title: "Tor 0.2.2.2-alpha released"
permalink: tor-0222alpha-released
date: 2009-10-09 22:49:19
author: phobos
category: blog
status: closed
tags: ["alpha release", "bug fixes", "performance improvements"]
---

On September 21st, we released Tor version 0.2.2.2-alpha.

**Major features:** [**read more »**](https://blog.torproject.org/blog/tor-0222alpha-released)

Tor now tracks how long it takes to build client-side circuits  
 over time, and adapts its timeout to local network performance.  
 Since a circuit that takes a long time to build will also provide  
 bad performance, we get significant latency improvements by  
 discarding the slowest 20% of circuits. Specifically, Tor creates  
 circuits more aggressively than usual until it has enough data  
 points for a good timeout estimate. Implements proposal 151.  
 We are especially looking for reports (good and bad) from users with  
 both EDGE and broadband connections that can move from broadband  
 to EDGE and find out if the build-time data in the .tor/state gets  
 reset without loss of Tor usability. You should also see a notice  
 log message telling you that Tor has reset its timeout.
