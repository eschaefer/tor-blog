---
layout: post
title: "Tor Browser 3.6.6 is released"
permalink: tor-browser-366-released
date: 2014-09-25
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.6", "tor browser", "tor browser bundle"]
---

The sixth pointfix release of the 3.6 series is available from the [Tor Browser Project page](https://www.torproject.org/download/download-easy.html) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/3.6.6/).

This release features [important security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.8.1) to Firefox.

Here is the complete changelog for 3.6.6:

- All Platforms
  - Update Tor to tor-0.2.4.24
  - Update Firefox to 24.8.1esr
  - Update NoScript to 2.6.8.42
  - Update HTTPS Everywhere to 4.0.1
  - Bug 12998: Prevent intermediate certs from being written to disk
  - Update Torbutton to 1.6.12.3
    - Bug 13091: Use "Tor Browser" everywhere
    - Bug 10804: Workaround fix for some cases of startup hang 

- Linux
  - Bug 9150: Make RPATH unavailable on Tor binary. 

The list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) is also available in our bug tracker.

