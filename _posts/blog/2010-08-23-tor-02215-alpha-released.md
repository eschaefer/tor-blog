---
layout: post
title: "Tor 0.2.2.15-alpha released"
permalink: tor-02215-alpha-released
date: 2010-08-23 03:44:28
author: erinn
category: blog
status: closed
tags: ["alpha releases", "hidden services", "memory leaks", "performance improvements", "tor"]
---

Tor 0.2.2.15-alpha fixes a big bug in hidden service availability, fixes a variety of other bugs that were preventing performance experiments from moving forward, fixes several bothersome memory leaks, and generally closes a lot of smaller bugs that have been filling up trac lately.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

[Changes in version 0.2.2.15-alpha - 2010-08-18](https://gitweb.torproject.org/tor.git/blob_plain/eba3f37f17a2af4ff628dd5cbc653441e6dce6eb:/ChangeLog)  
 o Major bugfixes:  
 - Stop assigning the HSDir flag to relays that disable their  
 DirPort (and thus will refuse to answer directory requests). This  
 fix should dramatically improve the reachability of hidden services:  
 hidden services and hidden service clients pick six HSDir relays  
 to store and retrieve the hidden service descriptor, and currently  
 about half of the HSDir relays will refuse to work. Bugfix on  
 0.2.0.10-alpha; fixes part of bug 1693. [**read more »**](https://blog.torproject.org/blog/tor-02215-alpha-released)
