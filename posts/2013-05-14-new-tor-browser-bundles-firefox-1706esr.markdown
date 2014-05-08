---
layout: post
title: "New Tor Browser Bundles with Firefox 17.0.6esr"
permalink: new-tor-browser-bundles-firefox-1706esr
date: 05/14/2013
author: erinn
category: blog
tags: ["firefox updates", "tbb", "tor browser bundle"]
---

There is a new Firefox 17.0.6esr out and all of the Tor Browser Bundles (stable and alpha branches) have been updated. The new stable TBBs have a lot of new and updated Firefox patches, so those of you who were experiencing crashes should no longer be seeing that behavior. Please let us know if you do by [opening a ticket](https://trac.torproject.org/projects/tor) with details.

The stable Tor Browser Bundles are available at their [normal location](https://www.torproject.org/download/download-easy.html.en).

The alpha Tor Browser Bundles are available [here](https://www.torproject.org/projects/torbrowser.html.en#Download-torbrowserbundlealpha).

**Tor Browser Bundle (2.3.25-8)**

- Update Firefox to 17.0.6esr
- Update HTTPS Everywhere to 3.2
- Update Torbutton to 1.5.2
- Update libpng to 1.5.15
- Update NoScript to 2.6.6.1
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

**Tor Browser Bundle (2.4.12-alpha-2)**

  - Update Firefox to 17.0.6esr
  - Update NoScript to 2.6.6.1

