---
layout: post
title: "Tor Browser 4.0.2 is released"
permalink: blog/tor-browser-402-released
date: 2014-12-03 09:05:36
author: gk
category: blog
comments: closed
tags: ["tbb", "tbb-4.0", "tor browser", "tor browser bundle"]
---

A new release for the stable Tor Browser is available from the [Tor Browser Project page](https://www.torproject.org/download/download-easy.html) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/4.0.2/).

Tor Browser 4.0.2 is based on Firefox ESR 31.3.0, which features [important security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox31.3.0) to Firefox. Additionally, it fixes a regression in third party cache isolation (tracking protection) that appeared in 4.0, and prevents JavaScript engine locale leaks. Moreover, we believe we have fixed all of the Windows crashes that were due to mingw-w64 compiler bugs. DirectShow is still disabled by default, though, to give the respective mingw-w64 patch another round of testing.

Here is the changelog since 4.0.1:

-   All Platforms
    -   Update Firefox to 31.3.0esr
    -   Update NoScript to 2.6.9.5
    -   Update HTTPS Everywhere to 4.0.2
    -   Update Torbutton to 1.7.0.2
        -   Bug 13019: Synchronize locale spoofing pref with our Firefox patch
        -   Bug 13746: Properly link Torbutton UI to thirdparty pref.
    -   Bug 13742: Fix domain isolation for content cache and disk-enabled  
         browsing mode
    -   Bug 5926: Prevent JS engine locale leaks (by setting the C library  
         locale)
    -   Bug 13504: Remove unreliable/unreachable non-public bridges
    -   Bug 13435: Remove our custom POODLE fix (fixed by Mozilla in 31.3.0esr)
-   Windows
    -   Bug 13443: Fix DirectShow-related crash with mingw patch.
    -   Bug 13558: Fix crash on Windows XP during download folder changing
    -   Bug 13594: Fix update failure for Windows XP users

