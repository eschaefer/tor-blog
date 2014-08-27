---
layout: post
title: "Tor security advisory: Old Tor Browser Bundles vulnerable"
permalink: tor-security-advisory-old-tor-browser-bundles-vulnerable
date: 2013-08-05
author: arma
category: blog
tags: ["security", "tbb", "tor browser"]
---

An attack that exploits a [Firefox vulnerability in JavaScript](https://www.mozilla.org/security/announce/2013/mfsa2013-53.html) has been observed in the wild. Specifically, Windows users using the Tor Browser Bundle (which includes Firefox [plus privacy patches](https://www.torproject.org/projects/torbrowser/design/)) appear to have been targeted.

This vulnerability was [fixed in Firefox 17.0.7 ESR](https://blog.mozilla.org/security/2013/08/04/investigating-security-vulnerability-report/). The following versions of the Tor Browser Bundle include this fixed version:

- 2.3.25-10 (released [June 26 2013](https://blog.torproject.org/blog/new-tor-browser-bundles-and-tor-02414-alpha-packages))
- 2.4.15-alpha-1 (released [June 26 2013](https://blog.torproject.org/blog/new-tor-browser-bundles-and-tor-02414-alpha-packages))
- 2.4.15-beta-1 (released [July 8 2013](https://blog.torproject.org/blog/tor-02415-rc-packages-available))
- 3.0alpha2 (released [June 30 2013](https://blog.torproject.org/blog/tor-browser-bundle-30alpha2-released))

Tor Browser Bundle users should ensure they're running a recent enough bundle version, and consider taking further security precautions.

Read the full advisory here:  
 [https://lists.torproject.org/pipermail/tor-announce/2013-August/000089.h...](https://lists.torproject.org/pipermail/tor-announce/2013-August/000089.html "https://lists.torproject.org/pipermail/tor-announce/2013-August/000089.html")

