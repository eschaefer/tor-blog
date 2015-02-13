---
layout: post
title: "\"One cell is enough to break Tor&#039;s anonymity\""
permalink: one-cell-enough
date: 2009-02-19 01:51:21
author: arma
category: blog
status: closed
tags: ["attacks", "research", "tagging"]
---

Tomorrow there's a talk at Black Hat DC by Xinwen Fu on an active attack that can allow traffic confirmation in Tor. He calls it a "[replay attack](http://www.cs.uml.edu/~xinwenfu/paper/ICC08_Fu.pdf)", whereas we called it a "tagging attack" in the original Tor paper, but let's look at how it actually works.

First, remember the basics of how Tor provides anonymity. Tor clients [route their traffic](https://www.torproject.org/images/htw2.png) over several ([usually three](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#VariablePathLength)) relays, with the goal that no single relay gets to learn both where the user is (call her Alice) and what site she's reaching (call it Bob).

The Tor design [doesn't try to protect](https://www.torproject.org/svn/trunk/doc/design-paper/tor-design.html#subsec:threat-model) against an attacker who can see or measure both traffic going into the Tor network and also traffic coming out of the Tor network. That's because if you can see both flows, some [simple statistics](http://freehaven.net/anonbib/#danezis:pet2004) let you decide whether they match up. [**read more »**](https://blog.torproject.org/blog/one-cell-enough)
