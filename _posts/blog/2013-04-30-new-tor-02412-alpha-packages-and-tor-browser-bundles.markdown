---
layout: post
title: "New Tor 0.2.4.12-alpha packages and Tor Browser Bundles"
permalink: blog/new-tor-02412-alpha-packages-and-tor-browser-bundles
date: 2013-04-30
author: erinn
category: blog
tags: ["tbb", "tor alpha", "tor browser bundle", "tor release"]
---

There is a new alpha-release of Tor Browser, based on tor 0.2.4.12-alpha. Alpha versions of Vidalia Bundles and Expert bundles are also updated.

This release also includes a patch to enable [optimistic data](https://thunk.cs.uwaterloo.ca/optimistic-data-pets2010-rump.pdf) (PDF) which should significantly speed up your browsing experience. Please give them a try and let us know how they work for you.

You can download the alpha Tor Browser Bundles [here](https://www.torproject.org/projects/torbrowser.html.en#Download-torbrowserbundlealpha).

**Tor Browser Bundle (2.4.12-alpha-1)**

- Update Tor to 0.2.4.12-alpha
- Update Torbutton to 1.5.2
- Update libpng to 1.5.15
- Update NoScript to 2.6.6
- Update PDF.js to 0.8.1
- Firefox patch changes:

  - Apply font limits to @font-face local() fonts and disable fallback
 rendering for @font-face. (closes: #8455)
  - Use Optimistic Data SOCKS handshake (improves page load performance).
 (closes: #3875)
  - Honor the Windows theme for inverse text colors (without leaking those
 colors to content). (closes: #7920)
  - Increase pipeline randomization and try harder to batch pipelined
 requests together. (closes: #8470)
  - Fix an image cache isolation domain key misusage. May fix several image
 cache related crash bugs with New Identity, exit, and certain websites.
 (closes: #8628)
- Torbutton changes:

  - Allow session restore if the user allows disk actvity (closes: #8457)
  - Remove the Display Settings panel and associated locales (closes: #8301)
  - Fix "Transparent Torification" option. (closes: #6566)
  - Fix a hang on New Identity. (closes: #8642)
- Build changes:

  - Fetch our source deps from an https mirror (closes: #8286)
  - Create watch scripts for syncing mirror sources and monitoring mirror
 integrity (closes: #8338)

