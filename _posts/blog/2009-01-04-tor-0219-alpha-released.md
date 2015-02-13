---
layout: post
title: "Tor 0.2.1.9-alpha released"
permalink: tor-0219-alpha-released
date: 2009-01-04 21:55:25
author: phobos
category: blog
status: closed
tags: ["alpha release", "bug fixes", "deprecated features", "security fixes"]
---

Tor 0.2.1.9-alpha fixes many more bugs, some of them security-related.

[https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

Changes in version 0.2.1.9-alpha - 2008-12-25  
 **New directory authorities:**

-   gabelmoo (the authority run by Karsten Loesing) now has a new  
     IP address.

**Security fixes:**

-   Never use a connection with a mismatched address to extend a  
     circuit, unless that connection is canonical. A canonical  
     connection is one whose address is authenticated by the router's  
     identity key, either in a NETINFO cell or in a router descriptor.
-   Avoid a possible memory corruption bug when receiving hidden service  
     descriptors. Bugfix on 0.2.1.6-alpha.

**Major bugfixes:** [**read more »**](https://blog.torproject.org/blog/tor-0.2.1.9-alpha-released)
