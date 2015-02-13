---
layout: post
title: "Tor 0.2.1.12-alpha is released"
permalink: tor-02112-alpha-released
date: 2009-02-09 18:29:18
author: phobos
category: blog
status: closed
tags: ["alpha release", "bug fixes", "improvements", "security fixes"]
---

Tor 0.2.1.12-alpha features several more security-related fixes. You  
 should upgrade, especially if you run an exit relay (remote crash) or  
 a directory authority (remote infinite loop), or you're on an older  
 (pre-XP) or not-recently-patched Windows (remote exploit). It also  
 includes a big pile of minor bugfixes and cleanups.

[https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

Changes in version 0.2.1.12-alpha - 2009-02-08  
 **Security fixes:**

-   Fix an infinite-loop bug on handling corrupt votes under certain  
     circumstances. Bugfix on 0.2.0.8-alpha.
-   Fix a temporary DoS vulnerability that could be performed by  
     a directory mirror. Bugfix on 0.2.0.9-alpha; reported by lark.
-   Avoid a potential crash on exit nodes when processing malformed  
     input. Remote DoS opportunity. Bugfix on 0.2.1.7-alpha.

**Minor bugfixes:**

Let controllers actually ask for the "clients\_seen" event for [**read more »**](https://blog.torproject.org/blog/tor-0.2.1.12-alpha-released)
