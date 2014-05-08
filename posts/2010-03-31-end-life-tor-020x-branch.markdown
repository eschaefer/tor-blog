---
layout: post
title: "End of Life for Tor 0.2.0.x branch"
permalink: end-life-tor-020x-branch
date: 03/31/2010
author: phobos
category: blog
tags: ["end of life", "old-stable", "tor 0.2.0"]
---

We have declared end-of-life for Tor 0.2.0.x. Those Tor versions have  
several known flaws, and nobody should be using them. You should upgrade.

Specifically, the big flaw in Tor <= 0.2.0.35 is that its list of  
directory authorities is out of date, so you'll find it hard to learn  
about the network. We're signing the network status consensus with the  
old signatures for now, but we're going to stop doing that in a few weeks,  
which means your Tor 0.2.0.x will fail to find the current network.

The only exception is people using Debian Lenny -- our nice Debian  
packager is trying to keep that package maintained for you.

As a bonus, if you move to a newer Tor you'll get significant performance  
boosts as a client, and you'll improve the performance for others as  
a relay.

The original message is archived at [http://archives.seul.org/or/announce/Mar-2010/msg00001.html](http://archives.seul.org/or/announce/Mar-2010/msg00001.html "http://archives.seul.org/or/announce/Mar-2010/msg00001.html")

