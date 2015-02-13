---
layout: post
title: "Tor 0.2.2.21-alpha is out (security patches)"
permalink: tor-02221-alpha-out-security-patches
date: 2011-01-18 23:25:48
author: erinn
category: blog
status: closed
tags: ["alpha release", "security fixes", "tbb", "tor", "tor browser bundle", "updated packages"]
---

Note to **64-bit Linux Tor Browser Bundle** users: The previous bundles contained Tor 0.2.2.20-alpha. Please upgrade to [1.1.3-1](https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-i686-1.1.3-dev-en-US.tar.gz) ([sig](https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-i686-1.1.3-dev-en-US.tar.gz.asc)).

Tor 0.2.2.21-alpha includes all the patches from Tor 0.2.1.29, which  
 continues our recent code security audit work. The main fix resolves  
 a remote heap overflow vulnerability that can allow remote code  
 execution (CVE-2011-0427). Other fixes address a variety of assert  
 and crash bugs, most of which we think are hard to exploit remotely.

**All Tor users should upgrade.**

[https://www.torproject.org/download/download](https://www.torproject.org/download/download "https://www.torproject.org/download/download")

Changes in version 0.2.2.21-alpha - 2011-01-15  
 **Major bugfixes (security), also included in 0.2.1.29:** [**read more »**](https://blog.torproject.org/blog/tor-02221-alpha-out-security-patches)
