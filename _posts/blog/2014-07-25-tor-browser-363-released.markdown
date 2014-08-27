---
layout: post
title: "Tor Browser 3.6.3 is released"
permalink: tor-browser-363-released
date: 2014-07-25
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.6", "tor browser", "tor browser bundle"]
---

The third pointfix release of the 3.6 series is available from the [Tor Browser Project page](https://www.torproject.org/download/download-easy.html) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/3.6.3/).

This release features [important security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.7) to Firefox.

Here is the complete changelog:

- All Platforms

  - Update Firefox to 24.7.0esr
  - Update obfsproxy to 0.2.12
  - Update FTE to 0.2.17
  - Update NoScript to 2.6.8.33
  - Update HTTPS Everywhere to 3.5.3
  - Bug 12673: Update FTE bridges
  - Update Torbutton to 1.6.11.0

    - Bug 12221: Remove obsolete Javascript components from the toggle era
    - Bug 10819: Bind new third party isolation pref to Torbutton security UI
    - Bug 9268: Fix some window resizing corner cases with DPI and taskbar size.
- Linux:
  - Bug 11102: Set Window Class to "Tor Browser" to aid in Desktop navigation
  - Bug 12249: Don't create PT debug files anymore

The list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) is also available in our bug tracker.

