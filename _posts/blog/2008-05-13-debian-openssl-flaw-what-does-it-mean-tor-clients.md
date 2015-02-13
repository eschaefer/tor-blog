---
layout: post
title: "The Debian OpenSSL flaw: what does it mean for Tor clients?"
permalink: debian-openssl-flaw-what-does-it-mean-tor-clients
date: 2008-05-13 20:22:24
author: arma
category: blog
status: closed
tags: ["openssl", "security advisory"]
---

There have been a lot of questions today about just what [the  
 recent Debian OpenSSL](http://lists.debian.org/debian-security-announce/2008/msg00152.html) flaw means for Tor clients. Here's an attempt to  
 explain it in a bit more detail. (Go read [the Tor security advisory](http://archives.seul.org/or/announce/May-2008/msg00000.html) before  
 reading this post.)

First, let's look at the security/anonymity implications for users who  
 aren't running on Debian, Ubuntu, or similar. These implications all  
 stem from the fact that some of the Tor relays and v3 directory authorities  
 have weak keys, so the Tor network isn't able to provide as much anonymity  
 as we would like.

The biggest issue is that perhaps 300 Tor relays were running with  
 weak keys and weak crypto, out of the roughly 1500-2000 total running  
 relays. What can an attacker do from this? If you happen to pick three  
 weak relays in a row for your circuit, then somebody watching your local  
 network connection (or watching the first relay you pick) could break all  
 the layers of Tor encryption and read the traffic as if they were watching  
 it at the exit relay. [**read more »**](https://blog.torproject.org/blog/debian-openssl-flaw%3A-what-does-it-mean-tor-clients%3F)
