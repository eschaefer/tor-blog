---
layout: post
title: "Tor Browser Bundle 3.0beta1 Released"
permalink: tor-browser-bundle-30beta1-released
date: 2013-11-06
author: mikeperry
category: blog
tags: ["deterministic builds", "gitian", "security", "tbb", "tbb-3.0", "tor browser", "tor browser bundle", "tor-browser-bundle"]
---

The first beta release in the [3.0 series](https://blog.torproject.org/category/tags/tbb-30) of the Tor Browser Bundle is now available from the Tor Package Archive:  
 [https://archive.torproject.org/tor-package-archive/torbrowser/3.0b1/](https://archive.torproject.org/tor-package-archive/torbrowser/3.0b1/ "https://archive.torproject.org/tor-package-archive/torbrowser/3.0b1/")

This release includes [important security updates to Firefox](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox17.0.10), as well as a fix for a startup crash bug on Windows XP.

This release also reorganizes the bundle directory structure to simplify implementation of the FIrefox updater in future releases. This means that extracting the bundle over previous installation will likely not preserve your preferences or bookmarks, and may cause other issues.

This release has also introduced a [build reproducibility issue on Windows](https://trac.torproject.org/projects/tor/ticket/10102), hence it is signed only by two keys. We should have this issue fixed by the next beta.

Here is the complete ChangeLog:

- All Platforms:
  - Update Firefox to 17.0.10esr
  - Update NoScript to 2.6.8.2
  - Update HTTPS-Everywhere to 3.4.2
  - Bug #9114: Reorganize the bundle directory structure to ease future autoupdates
  - Bug #9173: Patch Tor Browser to auto-detect profile directory if launched without the wrapper script.
  - Bug #9012: Hide Tor Browser infobar for missing plugins.
  - Bug #8364: Change the default entry page for the addons tab to the installed addons page.
  - Bug #9867: Make flash objects really be click-to-play if flash is enabled.
  - Bug #8292: Make getFirstPartyURI log+handle errors internally to simplify caller usage of the API
  - Bug #3661: Remove polipo and privoxy from the banned ports list.
  - misc: Fix a potential memory leak in the Image Cache isolation
  - misc: Fix a potential crash if OS theme information is ever absent
  - Update Tor-Launcher to 0.2.3.1-beta
    - Bug #9114: Handle new directory structure
    - misc: Tor Launcher now supports Thunderbird 

  - Update Torbutton to 1.6.4
    - Bug #9224: Support multiple Tor socks ports for about:tor status check
    - Bug #9587: Add TBB version number to about:tor
    - Bug #9144: Workaround to handle missing translation properties 

- Windows:
  - Bug #9084: Fix startup crash on Windows XP. 

- Linux:
  - Bug #9487: Create detached debuginfo files for Linux Tor and Tor Browser binaries. 

