---
layout: post
title: "Tor 0.2.2.18-alpha available"
permalink: tor-02218-alpha-available
date: 2010-11-17 17:30:21
author: phobos
category: blog
status: closed
tags: ["alpha release", "bug fixes", "feature enhancements"]
---

Tor 0.2.2.18-alpha fixes several crash bugs that have been nagging us lately, makes unpublished bridge relays able to detect their IP address, and fixes a wide variety of other bugs to get us much closer to a stable release.

[https://www.torproject.org/download/download](https://www.torproject.org/download/download "https://www.torproject.org/download/download")

Packages will be appearing over the next few days. The original version of this announcement is at [http://archives.seul.org/or/talk/Nov-2010/msg00082.html](http://archives.seul.org/or/talk/Nov-2010/msg00082.html "http://archives.seul.org/or/talk/Nov-2010/msg00082.html").

Changes in version 0.2.2.18-alpha - 2010-11-16  
 o Major bugfixes:  
 - Do even more to reject (and not just ignore) annotations on  
 router descriptors received anywhere but from the cache. Previously  
 we would ignore such annotations at first, but cache them to disk  
 anyway. Bugfix on 0.2.0.8-alpha. Found by piebeer.  
 - Do not log messages to the controller while shrinking buffer  
 freelists. Doing so would sometimes make the controller connection  
 try to allocate a buffer chunk, which would mess up the internals [**read more »**](https://blog.torproject.org/blog/tor-02218-alpha-available)
