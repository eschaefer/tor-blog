---
layout: post
title: "Tor Browser 3.5.3 is released"
permalink: tor-browser-353-released
date: 2014-03-19
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.5", "tor browser", "tor browser bundle"]
---

The 3.5.3 stable release of the Tor Browser Bundle is now available on the [Download page](https://www.torproject.org/download/download-easy.html). You can also download the bundles directly from the [distribution directory](https://www.torproject.org/dist/torbrowser/3.5.3/).

This release also includes [important security updates to Firefox](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.4).

As a reminder, this is the stable series of the Tor Browser Bundle. It does not include the Pluggable Transport support mentioned in the [3.6 release post](https://blog.torproject.org/blog/tor-browser-36-beta-1-released), and in this release MacOS archives are still in zip format. If you would like those features, we encourage you to use 3.6-beta-1 instead, and report any issues you encounter.

Here is the complete changelog for 3.5.3:

- All Platforms
  - Update Firefox to 24.4.0esr
  - Update Torbutton to 1.6.7.0:
    - Bug [9901](https://trac.torproject.org/projects/tor/ticket/9901): Fix browser freeze due to content type sniffing
    - Bug [10611](https://trac.torproject.org/projects/tor/ticket/10611): Add Swedish (sv) to extra locales to update 

  - Update NoScript to 2.6.8.17
  - Update Tor to 0.2.4.21
  - Bug [10237](https://trac.torproject.org/projects/tor/ticket/10237): Disable the media cache to prevent disk leaks for videos
  - Bug [10703](https://trac.torproject.org/projects/tor/ticket/10703): Force the default charset to avoid locale fingerprinting
  - Bug [10104](https://trac.torproject.org/projects/tor/ticket/10104): Update gitian to fix LXC build issues (for non-KVM/VT builders) 

- Linux:
  - Bug [9353](https://trac.torproject.org/projects/tor/ticket/9353): Fix keyboard input on Ubuntu 13.10
  - Bug [9896](https://trac.torproject.org/projects/tor/ticket/9896): Provide debug symbols for Tor Browser binary
  - Bug [10472](https://trac.torproject.org/projects/tor/ticket/10472): Pass arguments to the browser from Linux startup script 

A list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) with the Tor Browser can be found on our bugtracker. Please check that list and help us diagnose and arrive at solutions for those issues before contacting support.

