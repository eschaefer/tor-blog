---
layout: post
title: "New Stable Version 0.2.1.24 released"
permalink: new-stable-version-02124-released
date: 2010-03-03 15:14:34
author: phobos
category: blog
status: closed
tags: ["apple osx love", "bug fixes", "enhancements", "performance enhancements", "stable release", "tor update"]
---

Tor 0.2.1.23 fixes a huge client-side performance bug, makes Tor work again on the latest OS X, and updates the location of a directory authority.

Tor 0.2.1.24 makes Tor work again on the latest OS X -- this time for sure!

The Windows and OS X bundles also come with a newer version of Polipo that fixes some stability and security problems.

People using Tor as a client should upgrade:  
 [https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

Changes in version 0.2.1.23 - 2010-02-13  
 **Major bugfixes (performance):** [**read more »**](https://blog.torproject.org/blog/new-stable-version-02124-released)

We were selecting our guards uniformly at random, and then weighting which of our guards we'd use uniformly at random. This imbalance meant that Tor clients were severely limited on throughput (and probably latency too) by the first hop in their circuit. Now we select guards weighted by currently advertised bandwidth. We also automatically discard guards picked using the old algorithm. Fixes bug 1217; bugfix on 0.2.1.3-alpha. Found by Mike Perry.
