---
layout: post
title: "Tor 0.2.1.6-alpha Released"
permalink: tor-0216-alpha-released
date: 2008-10-14 19:25:11
author: phobos
category: blog
status: closed
tags: ["alpha", "bug fixes"]
---

Tor 0.2.1.6-alpha further improves performance and robustness of hidden  
 services, starts work on supporting per-country relay selection, and  
 fixes a variety of smaller issues.

The original announcement can be found at  
 [http://archives.seul.org/or/talk/Oct-2008/msg00093.html](http://archives.seul.org/or/talk/Oct-2008/msg00093.html "http://archives.seul.org/or/talk/Oct-2008/msg00093.html")

Changes in version 0.2.1.6-alpha - 2008-09-30 [**read more »**](https://blog.torproject.org/blog/tor-0.2.1.6-alpha-released)

Major features:

-   Implement proposal 121: make it possible to build hidden services  
     that only certain clients are allowed to connect to. This is  
     enforced at several points, so that unauthorized clients are unable  
     to send INTRODUCE cells to the service, or even (depending on the  
     type of authentication) to learn introduction points. This feature  
     raises the bar for certain kinds of active attacks against hidden  
     services. Code by Karsten Loesing.
-   Relays now store and serve v2 hidden service descriptors by default,  
     i.e., the new default value for HidServDirectoryV2 is 1. This is  
     the last step in proposal 114, which aims to make hidden service  
     lookups more reliable.
-   Start work to allow node restrictions to include country codes. The  
     syntax to exclude nodes in a country with country code XX is  
     "ExcludeNodes {XX}". Patch from Robert Hogan. It still needs some  
     refinement to decide what config options should take priority if  
     you ask to both use a particular node and exclude it.
-   Allow ExitNodes list to include IP ranges and country codes, just  
     like the Exclude\*Nodes lists. Patch from Robert Hogan.

Major bugfixes:  

