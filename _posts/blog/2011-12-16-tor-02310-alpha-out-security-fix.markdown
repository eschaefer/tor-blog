---
layout: post
title: "Tor 0.2.3.10-alpha is out (security fix)"
permalink: tor-02310-alpha-out-security-fix
date: 2011-12-16
author: erinn
category: blog
tags: ["alpha releases", "bugfixes", "security critical", "security fixes", "tor"]
---

**Tor 0.2.3.10-alpha fixes a critical heap-overflow security issue in  
 Tor's buffers code. Absolutely everybody should upgrade.**

The bug relied on an incorrect calculation when making data continuous  
 in one of our IO buffers, if the first chunk of the buffer was  
 misaligned by just the wrong amount. The miscalculation would allow an  
 attacker to overflow a piece of heap-allocated memory. To mount this  
 attack, the attacker would need to either open a SOCKS connection to  
 Tor's SocksPort (usually restricted to localhost), or target a Tor  
 instance configured to make its connections through a SOCKS proxy  
 (which Tor does not do by default).

Good security practice requires that all heap-overflow bugs should be  
 presumed to be exploitable until proven otherwise, so we are treating  
 this as a potential code execution attack. Please upgrade immediately!  
 This bug does not affect bufferevents-based builds of Tor. Special  
 thanks to "Vektor" for reporting this issue to us!

This release also contains a few minor bugfixes for issues discovered  
 in 0.2.3.9-alpha.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Changes in version 0.2.3.10-alpha - 2011-12-16**

**Major bugfixes**

- Fix a heap overflow bug that could occur when trying to pull  
 data into the first chunk of a buffer, when that chunk had  
 already had some data drained from it. Fixes CVE-2011-2778;  
 bugfix on 0.2.0.16-alpha. Reported by "Vektor".

**Minor bugfixes**

- If we can't attach streams to a rendezvous circuit when we  
 finish connecting to a hidden service, clear the rendezvous  
 circuit's stream-isolation state and try to attach streams  
 again. Previously, we cleared rendezvous circuits' isolation  
 state either too early (if they were freshly built) or not at all  
 (if they had been built earlier and were cannibalized). Bugfix on  
 0.2.3.3-alpha; fixes bug 4655.
- Fix compilation of the libnatpmp helper on non-Windows. Bugfix on  
 0.2.3.9-alpha; fixes bug 4691. Reported by Anthony G. Basile.
- Fix an assertion failure when a relay with accounting enabled  
 starts up while dormant. Fixes bug 4702; bugfix on 0.2.3.9-alpha.

**Minor features**

- Update to the December 6 2011 Maxmind GeoLite Country database.

