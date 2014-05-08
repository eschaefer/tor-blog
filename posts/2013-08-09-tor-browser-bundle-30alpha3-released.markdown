---
layout: post
title: "Tor Browser Bundle 3.0alpha3 Released"
permalink: tor-browser-bundle-30alpha3-released
date: 08/09/2013
author: mikeperry
category: blog
tags: ["deterministic builds", "gitian", "security", "tbb", "tbb-3.0", "tor browser", "tor browser bundle", "tor-browser-bundle"]
---

The third alpha release in the [3.0 series](https://blog.torproject.org/category/tags/tbb-30) of the Tor Browser Bundle is now available from the Tor Package Archive:

[https://archive.torproject.org/tor-package-archive/torbrowser/3.0a3](https://archive.torproject.org/tor-package-archive/torbrowser/3.0a3 "https://archive.torproject.org/tor-package-archive/torbrowser/3.0a3")

This release includes [important security updates to Firefox](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox17.0.8). Here is the complete ChangeLog:

- **All Platforms:**

  - Update Firefox to 17.0.8esr

[https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#f...](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox17.0.8 "https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox17.0.8")

  - Update Tor to 0.2.4.15-rc
  - Update HTTPS-Everywhere to 3.3.1
  - Update NoScript to 2.6.6.9
  - Improve build input fetching and authentication
  - Bug #9283: Update NoScript prefs for usability.
  - Bug #6152 (partial): Disable JSCtypes support at compile time
  - Update Torbutton to 1.6.1

    - Bug 8478: Change when window resize code fires to avoid rounding errors
    - Bug 9331: Hack a correct download URL for the next TBB release
    - Bug 9144: Change an aboutTor.dtd string so transifex will accept it
  - Update Tor-Launcher to 0.2.1-alpha

    - Bug #9128: Remove dependency on JSCtypes
- **Windows:**

  - Bug #9195: Disable download manager AV scanning (to prevent cloud  
 reporting+scanning of downloaded files)
- **Mac:**

Bug #9173 (partial): Launch firefox-bin on MacOS instead of TorBrowser.app  
 (improves dock behavior).

As usual these binaries should be exactly reproducible by anyone with Ubuntu and KVM support (though there are some issues in LXC).  
To build your own identical copies of these bundles from source code, check out [the official repository](https://gitweb.torproject.org/builders/tor-browser-bundle.git) and use git tag `tbb-3.0alpha3-release` (commit `49db54d147bd0bccc26f1d4f859cf9fe97e5f14c`).

These instructions should explain things from there. If you notice any differences from the official bundles, I would love to hear about it!

