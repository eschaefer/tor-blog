---
layout: post
title: "Tor 0.2.2.11-alpha and 0.2.2.12-alpha are out"
permalink: tor-02211-alpha-and-02212-alpha-are-out
date: 2010-04-23 22:26:03
author: phobos
category: blog
status: closed
tags: ["alpha releases", "bug fixes", "performance improvements"]
---

Tor 0.2.2.12-alpha fixes a critical bug in how directory authorities  
 handle and vote on descriptors. It was causing relays to drop out of  
 the consensus.

Tor 0.2.2.11-alpha fixes yet another instance of broken OpenSSL libraries  
 that was causing some relays to drop out of the consensus.

(Windows bundles will be available whenever Andrew gets around to making  
 them; we're trying to stick to a policy of announcing alphas on time  
 rather than waiting for every package.)

[https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

Original announcement is at [http://archives.seul.org/or/talk/Apr-2010/msg00174.html](http://archives.seul.org/or/talk/Apr-2010/msg00174.html "http://archives.seul.org/or/talk/Apr-2010/msg00174.html")

Changes in version 0.2.2.12-alpha - 2010-04-20  
 o Major bugfixes:  
 - Many relays have been falling out of the consensus lately because  
 not enough authorities know about their descriptor for them to get  
 a majority of votes. When we deprecated the v2 directory protocol,  
 we got rid of the only way that v3 authorities can hear from each [**read more »**](https://blog.torproject.org/blog/tor-02211-alpha-and-02212-alpha-are-out)
