---
layout: post
title: "Tor Browser 4.0.1 is released"
permalink: tor-browser-401-released
date: 2014-10-31 20:42:00
author: gk
category: blog
comments: closed
tags: ["tbb", "tbb-4.0", "tor browser", "tor browser bundle"]
---

A bugfix release for the latest stable Tor Browser is available from the [Tor Browser Project page](https://www.torproject.org/download/download-easy.html) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/4.0.1/).

Most notably, Tor Browser 4.0.1 fixes a crash bug affecting many users on Windows (see: [bug 13443](https://trac.torproject.org/projects/tor/ticket/13443) for the details). Furthermore, the latest stable version of Tor (0.2.5.10) is included and a [bug in our updater code](https://trac.torproject.org/projects/tor/ticket/13301) got fixed.

This is not a security update, and we will not be deploying update notification or automatic upgrades for all platforms for this release. We may provide automatic updates just for Windows users later in the week, but we are hesitant to do this immediately due to [Bug 13594](https://trac.torproject.org/projects/tor/ticket/13594).

Here is the changelog since 4.0:

-   All Platforms
    -   Update Tor to 0.2.5.10
    -   Update NoScript to 2.6.9.3
        -   Bug 13301: Prevent extensions incompatibility error after upgrades
        -   Bug 13460: Fix MSVC compilation issue
-   Windows
    -   Bug 13443: Disable DirectShow to prevent crashes on many sites
    -   Bug 13091: Make app name "Tor Browser" instead of "Tor"

