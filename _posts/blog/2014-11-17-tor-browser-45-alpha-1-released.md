---
layout: post
title: "Tor Browser 4.5-alpha-1 is released"
permalink: tor-browser-45-alpha-1-released
date: 2014-11-17 22:15:53
author: mikeperry
category: blog
status: closed
tags: ["tbb", "tbb-4.5", "tor browser", "tor browser bundle"]
---

The first alpha release of the 4.5 series is available from the [extended downloads page](https://www.torproject.org/projects/torbrowser.html.en#downloads-alpha) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/4.5-alpha-1/).

This release features a circuit status reporting UI (visible on the green Tor onion button menu), as well as isolation for circuit use. All content elements for a website will use a single circuit, and different websites should use different circuits, even when viewed at the same time. The Security Slider is also present in this release, and can be configured from the green Tor onion's Preferences menu, under the Privacy and Security settings tab. It also features HTTPS certificate pinning for selected sites (including our updater), which was backported from Firefox 32.

This release also features a rewrite of the obfs3 pluggable transport, and the introduction of the new obfs4 transport. Please test these transports and report any issues!

**Note to Mac users**: As part of [our planned end-of-life for supporting 32 bit Macs](https://blog.torproject.org/blog/end-life-plan-tor-browser-32-bit-macs), the Mac edition of this release is 64 bit only, which also means that the updater will not work for Mac users on the alpha series release channel for this release. Once you transition to this 64 bit release, the updater should function correctly after that.

Here is the complete changelog since 4.0.1:

-   All Platforms
    -   Bug 3455: Patch Firefox SOCKS and proxy filters to allow user+pass isolation
    -   Bug 11955: Backport HTTPS Certificate Pinning patches from Firefox 32
    -   Bug 13684: Backport Mozilla bug \#1066190 (pinning issue fixed in Firefox 33)
    -   Bug 13019: Make JS engine use English locale if a pref is set by Torbutton
    -   Bug 13301: Prevent extensions incompatibility error after upgrades
    -   Bug 13460: Fix MSVC compilation issue
    -   Bug 13504: Remove stale bridges from default bridge set
    -   Bug 13742: Fix domain isolation for content cache and disk-enabled browsing mode
    -   Update Tor to 0.2.6.1-alpha
    -   Update NoScript to 2.6.9.3
    -   Bug 13586: Make meek use TLS session tickets (to look like stock Firefox).
    -   Bug 12903: Include obfs4proxy pluggable transport
    -   Update Torbutton to 1.8.1.1
        -   Bug 9387: Provide a "Security Slider" for vulnerability surface reduction
        -   Bug 13019: Synchronize locale spoofing pref with our Firefox patch
        -   Bug 3455: Use SOCKS user+pass to isolate all requests from the same url domain
        -   Bug 8641: Create browser UI to indicate current tab's Tor circuit IPs
        -   Bug 13651: Prevent circuit-status related UI hang.
        -   Bug 13666: Various circuit status UI fixes
        -   Bug 13742+13751: Remove cache isolation code in favor of direct C++ patch
        -   Bug 13746: Properly update third party isolation pref if disabled from UI
-   Windows
    -   Bug 13443: Re-enable DirectShow; fix crash with mingw patch.
    -   Bug 13558: Fix crash on Windows XP during download folder changing
    -   Bug 13091: Make app name "Tor Browser" instead of "Tor"
    -   Bug 13594: Fix update failure for Windows XP users
-   Mac
    -   Bug 10138: Switch to 64bit builds for MacOS

