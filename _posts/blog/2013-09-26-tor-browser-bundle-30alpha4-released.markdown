---
layout: post
title: "Tor Browser Bundle 3.0alpha4 Released"
permalink: blog/tor-browser-bundle-30alpha4-released
date: 2013-09-26
author: mikeperry
category: blog
tags: ["deterministic builds", "gitian", "security", "tbb", "tbb-3.0", "tor browser", "tor browser bundle", "tor-browser-bundle"]
---

The third alpha release in the [3.0 series](https://blog.torproject.org/category/tags/tbb-30) of the Tor Browser Bundle is now available from the Tor Package Archive:
 [https://archive.torproject.org/tor-package-archive/torbrowser/3.0a4/](https://archive.torproject.org/tor-package-archive/torbrowser/3.0a4/ "https://archive.torproject.org/tor-package-archive/torbrowser/3.0a4/")

This release includes [important security updates to Firefox](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox17.0.9). Here is the complete ChangeLog:

- **All Platforms:**

  - Bug #8751: Randomize TLS HELLO timestamp in HTTPS connections
  - Bug #9790 (workaround): Temporarily re-enable JS-Ctypes for cache
 isolation and SSL Observatory
  - Update Firefox to 17.0.9esr
  - Update Tor to 0.2.4.17-rc
  - Update NoScript to 2.6.7.1
  - Update Tor-Launcher to 0.2.2-alpha
    - Bug #9675: Provide feedback mechanism for clock-skew and other early
 startup issues
    - Bug #9445: Allow user to enter bridges with or without 'bridge' keyword
    - Bug #9593: Use UTF16 for Tor process launch to handle unicode paths.
    - misc: Detect when Tor exits and display appropriate notification

  - Update Torbutton to 1.6.2.1
    - Bug 9492: Fix Torbutton logo on OSX and Windows (and related
 initialization code)
    - Bug 8839: Disable Google/Startpage search filters using Tor-specific urls

As usual these binaries should be exactly reproducible by anyone with Ubuntu and KVM support. To build your own identical copies of these bundles from source code, check out [the official repository](https://gitweb.torproject.org/builders/tor-browser-bundle.git) and use git tag `tbb-3.0alpha4-build1` (commit `d1fad5a54345d9dad8f8997f2f956d3f4fdeb0f4`).

[These instructions](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/README.build) should explain things from there. If you notice any differences from the official bundles, I would love to hear about it!

