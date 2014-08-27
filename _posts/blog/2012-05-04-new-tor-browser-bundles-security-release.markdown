---
layout: post
title: "New Tor Browser Bundles (security release)"
permalink: new-tor-browser-bundles-security-release
date: 2012-05-04
author: erinn
category: blog
tags: ["osx", "security fixes", "tbb", "tor browser bundle", "torbrowser"]
---

The Tor Browser Bundles have been updated with a very important security fix. As explained in the previous blog post, [a user discovered a severe security bug in Firefox related to websockets bypassing the SOCKS proxy DNS configuration](https://blog.torproject.org/blog/firefox-security-bug-proxy-bypass-current-tbbs). This is now fixed and we **strongly encourage** all users to update. There are a few other bugfixes in this release, including really fixing (for real this time!) the problem with the Mac OS X bundles crashing.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Tor Browser Bundle (2.2.35-11)**

- Security release to stop TorBrowser from bypassing SOCKS proxy DNS configuration
- New Firefox patches:

  - Prevent WebSocket DNS leak (closes: [#5741](https://trac.torproject.org/projects/tor/ticket/5741))
  - Fix a race condition that could be used to link browsing sessions together when using new identity from Tor Browser (closes: [#5715](https://trac.torproject.org/projects/tor/ticket/5715))
- Remove extraneous BetterPrivacy settings from prefs.js (closes: [#5722](https://trac.torproject.org/projects/tor/ticket/))
- Fix the mozconfig options for OS X so that it really builds everything with clang instead of llvm-gcc (closes: [#5740](https://trac.torproject.org/projects/tor/ticket/))

