---
layout: post
title: "Tor Browser 3.6-beta-2 is released"
permalink: tor-browser-36-beta-2-released
date: 2014-04-12
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.6", "tor browser", "tor browser bundle"]
---

The Tor Browser Team is proud to announce the second beta in the 3.6 series. Packages are available from the [Tor Browser Project page](https://www.torproject.org/projects/torbrowser.html.en#downloads-beta) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/3.6-beta-2/).

This release is an important security update over 3.6-beta-1. This release updates OpenSSL to version 1.0.1g, to address potential client-side vectors for [CVE-2014-0160](https://blog.torproject.org/blog/openssl-bug-cve-2014-0160).

The browser itself does not use OpenSSL, and is not vulnerable to this CVE. However, this release is still considered an important security update, because it is theoretically possible to extract sensitive information from the Tor client sub-process.

This beta also features a Turkish language bundle, experimental Javascript hardening options, fixes for pluggable transport issues, and a fix for improper update notification while extracting the bundle over an already existing copy.

Here is the complete changelog since 3.6-beta-1:

- All Platforms
  - Update OpenSSL to 1.0.1g
  - Bug [9010](https://trac.torproject.org/projects/tor/ticket/9010): Add Turkish language support.
  - Bug [9387](https://trac.torproject.org/projects/tor/ticket/9387) testing: Disable JS JIT, type inference, asmjs, and ion.
  - Update fte transport to 0.2.12
  - Update NoScript to 2.6.8.19
  - Update Torbutton to 1.6.8.1
    - Bug [11242](https://trac.torproject.org/projects/tor/ticket/11242): Fix improper "update needed" message after in-place upgrade.
    - Bug [10398](https://trac.torproject.org/projects/tor/ticket/10398): Ease translation of about:tor page elements 

  - Update Tor Launcher to 0.2.5.3
    - Bug [9665](https://trac.torproject.org/projects/tor/ticket/9665): Localize Tor's unreachable bridges bootstrap error 

  - Backport Pending Tor Patches:
    - Bug [9665](https://trac.torproject.org/projects/tor/ticket/9665): Report a bootstrap error if all bridges are unreachable
    - Bug [11200](https://trac.torproject.org/projects/tor/ticket/11200): Prevent spurious error message prior to enabling network. 

- Linux:
  - Bug [11190](https://trac.torproject.org/projects/tor/ticket/11190): Switch linux PT build process to python2
  - Bug [10383](https://trac.torproject.org/projects/tor/ticket/10383): Enable NIST P224 and P256 accel support for 64bit builds. 

- Windows:
  - Bug [11286](https://trac.torproject.org/projects/tor/ticket/11286): Fix fte transport launch error 

A list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) with the Tor Browser can be found on our bugtracker. Please check that list and help us diagnose and arrive at solutions for those issues before contacting support.

