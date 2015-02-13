---
layout: post
title: "Tor 0.2.1.18 and 0.2.1.19 released as stable"
permalink: tor-02118-and-02119-released-stable
date: 2009-08-06 01:44:33
author: phobos
category: blog
status: closed
tags: ["anonymity fixes", "bug fixes", "deprecated features", "feature enhancements", "stable release"]
---

Tor 0.2.1.18 lays the foundations for performance improvements, adds  
 status events to help users diagnose bootstrap problems, adds optional  
 authentication/authorization for hidden services, fixes a variety of  
 potential anonymity problems, and includes a huge pile of other features  
 and bug fixes.

Tor 0.2.1.19 fixes a major bug with accessing and providing hidden  
 services.

[https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

Changes in version 0.2.1.19 - 2009-07-28  
 **Major bugfixes:**

-   Make accessing hidden services on 0.2.1.x work right again.  
     Bugfix on 0.2.1.3-alpha; workaround for bug 1038. Diagnosis and  
     part of patch provided by "optimist".

**Minor features:**

When a relay/bridge is writing out its identity key fingerprint to  
 the "fingerprint" file and to its logs, write it without spaces. Now  
 it will look like the fingerprints in our bridges documentation, [**read more »**](https://blog.torproject.org/blog/tor-02118-and-02119-released-stable)
