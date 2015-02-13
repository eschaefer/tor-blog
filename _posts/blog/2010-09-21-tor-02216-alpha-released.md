---
layout: post
title: "Tor 0.2.2.16-alpha released"
permalink: tor-02216-alpha-released
date: 2010-09-21 19:08:41
author: phobos
category: blog
status: closed
tags: ["alpha release", "enhancements"]
---

Tor 0.2.2.16-alpha fixes a variety of old stream fairness bugs (most  
 evident at exit relays), and also continues to resolve all the little  
 bugs that have been filling up the bug tracker lately.

[https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

Packages will be appearing over the next few days or weeks (except  
 on Windows, which apparently doesn't build -- stay tuned for an  
 0.2.2.17-alpha in that case).

Changes in version 0.2.2.16-alpha - 2010-09-17  
 o Major bugfixes (stream-level fairness):  
 - When receiving a circuit-level SENDME for a blocked circuit, try  
 to package cells fairly from all the streams that had previously  
 been blocked on that circuit. Previously, we had started with the  
 oldest stream, and allowed each stream to potentially exhaust  
 the circuit's package window. This gave older streams on any  
 given circuit priority over newer ones. Fixes bug 1937. Detected [**read more »**](https://blog.torproject.org/blog/tor-02216-alpha-released)
