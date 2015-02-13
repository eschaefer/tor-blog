---
layout: post
title: "Tor 0.2.2.4-alpha released"
permalink: tor-0224-alpha-released
date: 2009-10-12 09:56:02
author: phobos
category: blog
status: closed
tags: ["alpha release", "bug fixes", "circuit building fixes", "code refactoring", "IP Address changes", "memory leaks", "tinytest framework"]
---

On October 10, we released Tor version 0.2.2.4-alpha.

This release can be found at [https://www.torproject.org/download/](https://www.torproject.org/download/ "https://www.torproject.org/download/")

It contains the following:  
 **Major bugfixes:**

-   Fix several more asserts in the circuit\_build\_times code, for  
     example one that causes Tor to fail to start once we have  
     accumulated 5000 build times in the state file. Bugfixes on  
     0.2.2.2-alpha; fixes bug 1108.

**New directory authorities:**

-   Move moria1 and Tonga to alternate IP addresses.

**Minor features:** [**read more »**](https://blog.torproject.org/blog/tor-0224-alpha-released)

Log SSL state transitions at debug level during handshake, and  
 include SSL states in error messages. This may help debug future  
 SSL handshake issues.

Add a new "Handshake" log domain for activities that happen  
 during the TLS handshake.

Revert to the "June 3 2009" ip-to-country file. The September one  

