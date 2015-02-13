---
layout: post
title: "Tor 0.2.0.30 is released as stable"
permalink: tor-02030-released-stable
date: 2008-08-25 21:48:37
author: phobos
category: blog
status: closed
tags: ["dns proxy", "rate limiting", "stable release", "tor"]
---

Tor 0.2.0.30 is released. A better formatted version of this report can be found [at gmane.org](http://permalink.gmane.org/gmane.network.onion-routing.announce/21)

Tor 0.2.0.30 switches to a more efficient directory distribution design,  
 adds features to make connections to the Tor network harder to block,  
 allows Tor to act as a DNS proxy, adds separate rate limiting for relayed  
 traffic to make it easier for clients to become relays, fixes a variety  
 of potential anonymity problems, and includes the usual huge pile of  
 other features and bug fixes.

[https://www.torproject.org/download.html](https://www.torproject.org/download.html "https://www.torproject.org/download.html")

Changes in version 0.2.0.30 - 2008-07-15  
 o New v3 directory design:  
 - Tor now uses a new way to learn about and distribute information  
 about the network: the directory authorities vote on a common  
 network status document rather than each publishing their own  
 opinion. Now clients and caches download only one networkstatus [**read more »**](https://blog.torproject.org/blog/tor-02030-released-stable)
