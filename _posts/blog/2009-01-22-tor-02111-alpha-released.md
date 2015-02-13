---
layout: post
title: "Tor 0.2.1.11-alpha released"
permalink: tor-02111-alpha-released
date: 2009-01-22 14:08:54
author: phobos
category: blog
status: closed
tags: ["alpha release", "bugfixes", "security fixes"]
---

Tor 0.2.1.11-alpha finishes fixing the "if your Tor is off for a week it  
 will take a long time to bootstrap again" bug. It also fixes an important  
 security-related bug reported by Ilja van Sprundel. You should upgrade.  
 (We'll send out more details about the bug once people have had some  
 time to upgrade.)

[https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

Changes in version 0.2.1.11-alpha - 2009-01-20  
 **Security fixes:**

-   Fix a heap-corruption bug that may be remotely triggerable on  
     some platforms. Reported by Ilja van Sprundel.

**Major bugfixes:**

-   Discard router descriptors as we load them if they are more than  
     five days old. Otherwise if Tor is off for a long time and then  
     starts with cached descriptors, it will try to use the onion  
     keys in those obsolete descriptors when building circuits. Bugfix  
     on 0.2.0.x. Fixes bug 887.

**Minor features:** [**read more »**](https://blog.torproject.org/blog/tor-0.2.1.11-alpha-released)
