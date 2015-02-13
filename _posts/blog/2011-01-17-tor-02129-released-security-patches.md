---
layout: post
title: "Tor 0.2.1.29 is released (security patches)"
permalink: tor-02129-released-security-patches
date: 2011-01-17 11:21:36
author: erinn
category: blog
status: closed
tags: ["security fixes", "stable releases", "tor"]
---

Tor 0.2.1.29 continues our recent code security audit work. The main  
 fix resolves a remote heap overflow vulnerability that can allow remote  
 code execution. Other fixes address a variety of assert and crash bugs,  
 most of which we think are hard to exploit remotely.

**All Tor users should upgrade.**

[https://www.torproject.org/download/download](https://www.torproject.org/download/download "https://www.torproject.org/download/download")

Changes in version 0.2.1.29 - 2011-01-15  
 **Major bugfixes (security):** [**read more »**](https://blog.torproject.org/blog/tor-02129-released-security-patches)

Fix a heap overflow bug where an adversary could cause heap  
 corruption. This bug probably allows remote code execution  
 attacks. Reported by "debuger". Fixes CVE-2011-0427. Bugfix on  
 0.1.2.10-rc.

Prevent a denial-of-service attack by disallowing any  
 zlib-compressed data whose compression factor is implausibly  
 high. Fixes part of bug 2324; reported by "doorss".

Zero out a few more keys in memory before freeing them. Fixes  

