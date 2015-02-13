---
layout: post
title: "Tor Browser Bundle 3.5rc1 Released"
permalink: tor-browser-bundle-35rc1-released
date: 2013-12-12 22:51:33
author: mikeperry
category: blog
status: closed
tags: ["tbb", "tbb-3.0", "tbb-3.5", "tor browser", "tor browser bundle", "tor-browser-bundle"]
---

The first release candidate in the [3.5 series](https://blog.torproject.org/category/tags/tbb-35) of the Tor Browser Bundle is now available from the Tor Package Archive:  
 [https://archive.torproject.org/tor-package-archive/torbrowser/3.5rc1/](https://archive.torproject.org/tor-package-archive/torbrowser/3.5rc1/).

This release includes [important security updates to Firefox.](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.2)

Moreover, the Firefox 17esr release series has been deprecated by Mozilla. This means the imminent end of life for our 2.x and 3.0 bundle series. All 3.0 users are strongly encourage to update immediately, as we will not be making further releases in that series. If this release candidate survives the next few days without issue, this release candidate will be declared stable, and we will officially deprecate the current stable 2.x Tor Browser Bundles and declare their versions out of date as well.

Here is the [complete changelog](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/refs/heads/master:/Bundle-Data/Docs/ChangeLog.txt):

-   All Platforms
    -   Update Firefox to 24.2.0esr
    -   Update NoScript to 2.6.8.7
    -   Update HTTPS-Everywhere to 3.4.4tbb (special TBB tag)
        -   Tag includes a patch to handle enabling/disabling Mixed Content Blocking
    -   Bug 5060: Disable health report service
    -   Bug 10367: Disable prompting about health report and Mozilla Sync
    -   Misc Prefs: Disable HTTPS-Everywhere first-run tooltips
    -   Misc Prefs: Disable layer acceleration to avoid crashes on Windows
    -   Misc Prefs: Disable Mixed Content Blocker pending backport of Mozilla Bug 878890
    -   Update Tor Launcher to 0.2.4.1
        -   Bug 10147: Adblock Plus interferes w/Tor Launcher dialog
        -   Bug 10201: FF ESR 24 hangs during exit on Mac OS
        -   Bug 9984: Support running Tor Launcher from InstantBird
        -   Misc: Support browser directory location API changes in Firefox 24
    -   Update Torbutton to 1.6.5.1
        -   Bug 10352: Clear FF24 Private Browsing Mode data during New Identity
        -   Bug 8167: Update cache isolation for FF24 API changes
        -   Bug 10201: FF ESR 24 hangs during exit on Mac OS
        -   Bug 10078: Properly clear crypto tokens during New Identity on FF24
        -   Bug 9454: Support changes to Private Browsing Mode and plugin APIs in FF24
-   Linux
    -   Bug 10213; Use LD\_LIBRARY\_PATH (fixes launch issues on old Linux distros)

