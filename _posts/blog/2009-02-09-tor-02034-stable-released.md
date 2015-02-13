---
layout: post
title: "Tor 0.2.0.34-stable released"
permalink: tor-02034-stable-released
date: 2009-02-09 18:21:20
author: phobos
category: blog
status: closed
tags: ["bug fixes", "security fixes", "stable release"]
---

Tor 0.2.0.34 features several more security-related fixes. You  
 should upgrade, especially if you run an exit relay (remote crash) or  
 a directory authority (remote infinite loop), or you're on an older  
 (pre-XP) or not-recently-patched Windows (remote exploit).

This release marks end-of-life for Tor 0.1.2.x. Those Tor versions have  
 many known flaws, and nobody should be using them. You should upgrade. If  
 you're using a Linux or BSD and its packages are obsolete, stop using  
 those packages and upgrade anyway.

[https://www.torproject.org/download.html](https://www.torproject.org/download.html "https://www.torproject.org/download.html")

Changes in version 0.2.0.34 - 2009-02-08  
 **Security fixes:** [**read more »**](https://blog.torproject.org/blog/tor-0.2.0.34-stable-released)

Fix an infinite-loop bug on handling corrupt votes under certain  
       circumstances. Bugfix on 0.2.0.8-alpha.

Fix a temporary DoS vulnerability that could be performed by  
       a directory mirror. Bugfix on 0.2.0.9-alpha; reported by lark.

Avoid a potential crash on exit nodes when processing malformed  

