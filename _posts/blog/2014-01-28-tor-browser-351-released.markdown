---
layout: post
title: "Tor Browser 3.5.1 is released"
permalink: blog/tor-browser-351-released
date: 2014-01-28
author: mikeperry
category: blog
tags: ["tbb-3.0", "tbb-3.5", "tor-browser-bundle"]
---

The 3.5.1 release of the Tor Browser Bundle is now available on the [Download page](https://www.torproject.org/download/download-easy.html). You can also download the bundles directly from the [distribution directory](https://www.torproject.org/dist/torbrowser/3.5.1/).

Please see the [FAQ listing](https://www.torproject.org/docs/faq.html.en#TBBFlash) for any issues you may have before contacting support or filing tickets.

This release features an update to OpenSSL to fix a denial of service condition, and to fix the NoScript whitelist to remove addons.mozilla.org.

This release also features Tor 0.2.4.20, as well as a support for screen readers for the blind on Windows.

Here is the list of changes since 3.5.1. The [3.x ChangeLog](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/refs/heads/master:/Bundle-Data/Docs/ChangeLog.txt) is also available.

- All Platforms
  - Bug 10447: Remove SocksListenAddress to allow multiple socks ports.
  - Bug 10464: Remove addons.mozilla.org from NoScript whitelist
  - Bug 10537: Build an Arabic version of TBB 3.5
  - Update Torbutton to 1.6.5.5
    - Bug 9486: Clear NoScript Temporary Permissions on New Identity
    - Include Arabic translations

  - Update Tor Launcher to 0.2.4.3
    - Include Arabic translations

  - Update Tor to 0.2.4.20
  - Update OpenSSL to 1.0.1f
  - Update NoScript to 2.6.8.12
  - Update HTTPS-Everywhere to 3.4.5

- Windows
  - Bug 9259: Enable Accessibility (screen reader) support

- Mac
  - misc: Update bundle version field in Info.plist (for MacUpdates service)

