---
layout: post
title: "Tor Browser Bundle 3.0rc1 Released"
permalink: tor-browser-bundle-30rc1-released
date: 2013-11-22
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.0", "tor browser", "tor browser bundle", "tor-browser-bundle"]
---

The first release candidate in the [3.0 series](https://blog.torproject.org/category/tags/tbb-30) of the Tor Browser Bundle is now available from the Tor Package Archive:  
 [https://archive.torproject.org/tor-package-archive/torbrowser/3.0rc1/](https://archive.torproject.org/tor-package-archive/torbrowser/3.0rc1/).

This release includes important [security updates to Firefox](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox17.0.11).

Unfortunately, we have decided to remove the PDF.JS addon from this bundle, as the version available for Firefox 17 has stopped receiving updates. Built-in PDF support should return when we transition to Firefox 24 in the coming weeks.

This release should also fix a [build reproducibility](https://trac.torproject.org/projects/tor/ticket/10102) issue on Windows. All platform binaries should once again be identically [reproducible from source by anyone](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/README.build) using git tag tbb-3.0rc1-release.

- All Platforms:
  - Update Firefox to 17.0.11esr
  - Update Tor to 0.2.4.18-rc
  - Remove unsupported PDF.JS addon from the bundle
  - Bug #7277: TBB's Tor client will now omit its timestamp in the TLS handshake.
  - Update Torbutton to 1.6.4.1
    - Bug #10002: Make the TBB3.0 blog tag our update download URL for now 

- Windows
  - Bug #10102: Patch binutils to remove nondeterministic bytes in compiled binaries 

- Linux
  - Bug #10049: Fix architecture check to work from outside TBB's directory
  - Bug #10126: Remove libz and firefox-bin, and strip unstripped binaries
  - Misc: Disable Firefox updater during compile time (in addition to pref) 

