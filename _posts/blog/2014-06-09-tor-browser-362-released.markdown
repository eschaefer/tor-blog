---
layout: post
title: "Tor Browser 3.6.2 is released"
permalink: tor-browser-362-released
date: 2014-06-09
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.6", "tor browser", "tor browser bundle"]
---

The second pointfix release of the 3.6 series is available from the [Tor Browser Project page](https://www.torproject.org/download/download-easy.html) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/3.6.2/).

This release features a fix to allow the configuration of a local HTTP or SOCKS proxy with all included Pluggable Transports.

In addition, this release also features [important security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.6) to Firefox, as well as an update to OpenSSL 1.0.1h to address the latest round of [OpenSSL security issues](https://www.openssl.org/news/secadv_20140605.txt).

This release also updates the Tor client software to version 0.2.4.22, which blacklists directory authority keys that were created prior to fixing the [Heartbleed attack](https://blog.torproject.org/blog/openssl-bug-cve-2014-0160).

- All Platforms
  - Update Firefox to 24.6.0esr
  - Update OpenSSL to 1.0.1h
  - Update NoScript to 2.6.8.28
  - Update Tor to 0.2.4.22
  - Update Tor Launcher to 0.2.5.5
    - Bug [10425](https://trac.torproject.org/projects/tor/ticket/10425): Provide geoip6 file location to Tor process
    - Bug [11754](https://trac.torproject.org/projects/tor/ticket/11754): Remove untranslated locales that were dropped from Transifex
    - Bug [11772](https://trac.torproject.org/projects/tor/ticket/11772): Set Proxy Type menu correctly after restart
    - Bug [11699](https://trac.torproject.org/projects/tor/ticket/11699): Change &amp;#160 to &#160; in UI elements 

  - Update Torbutton to 1.6.10.0
    - Bug [11510](https://trac.torproject.org/projects/tor/ticket/11510): about:tor should not report success if tor proxy is unreachable
    - Bug [11783](https://trac.torproject.org/projects/tor/ticket/11783): Avoid b.webProgress error when double-clicking on New Identity
    - Bug [11722](https://trac.torproject.org/projects/tor/ticket/11722): Add hidden pref to force remote Tor check
    - Bug [11763](https://trac.torproject.org/projects/tor/ticket/11763): Fix pref dialog double-click race that caused settings to be reset 

  - Bug [11629](https://trac.torproject.org/projects/tor/ticket/11629): Support proxies with Pluggable Transports
    - Updates FTEProxy to 0.2.15
    - Updates obfsproxy to 0.2.9 

  - Backported Tor Patches:
    - Bug [11654](https://trac.torproject.org/projects/tor/ticket/11654): Fix malformed log message in bug11156 patch. 

  - Bug [10425](https://trac.torproject.org/projects/tor/ticket/10425): Add in Tor's geoip6 files to the bundle distribution
  - Bugs [11834](https://trac.torproject.org/projects/tor/ticket/11834) and [11835](https://trac.torproject.org/projects/tor/ticket/11835): Include Pluggable Transport documentation
  - Bug [9701](https://trac.torproject.org/projects/tor/ticket/9701): Prevent ClipBoardCache from writing to disk.
  - Bug [12146](https://trac.torproject.org/projects/tor/ticket/12146): Make the CONNECT Host header the same as the Request-URI.
  - Bug [12212](https://trac.torproject.org/projects/tor/ticket/12212): Disable deprecated webaudio API
  - Bug [11253](https://trac.torproject.org/projects/tor/ticket/11253): Turn on TLS 1.1 and 1.2.
  - Bug [11817](https://trac.torproject.org/projects/tor/ticket/11817): Don't send startup time information to Mozilla. 

The list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) is also available in our bug tracker.

