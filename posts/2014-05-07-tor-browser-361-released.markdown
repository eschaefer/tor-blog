---
layout: post
title: "Tor Browser 3.6.1 is released"
permalink: tor-browser-361-released
date: 05/07/2014
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.6", "tor browser", "tor browser bundle"]
---

The first pointfix release of the 3.6 series is available from the [Tor Browser Project page](https://www.torproject.org/download/download-easy.html) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/3.6.1/).

This release features a fix for a regression with using a proxy for normal Tor usage. It does not yet allow the configuration of proxies for pluggable transports. We hope to fix that issue in the following point release.

This is not a security release.

Here is the complete changelog:

- All Platforms
  - Update HTTPS-Everywhere to 3.5.1
  - Update NoScript to 2.6.8.22
  - Bug [11658](https://trac.torproject.org/projects/tor/ticket/11658): Fix proxy configuration for non-Pluggable Transports users
  - Backport Pending Tor Patches:
    - Bug [8402](https://trac.torproject.org/projects/tor/ticket/8402): Allow Tor proxy configuration while PTs are present 

  - Note: The Pluggable Transports themselves have not been updated to support proxy configuration yet. 

