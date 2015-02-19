---
layout: post
title: "Tor Browser 4.5-alpha-2 is released"
permalink: blog/tor-browser-45-alpha-2-released
date: 2014-12-05 02:03:01
author: gk
category: blog
comments: open
tags: ["tbb", "tbb-4.5", "tor browser", "tor browser bundle"]
---

The second alpha release of the 4.5 series is available from the [extended downloads page](https://www.torproject.org/projects/torbrowser.html.en#downloads-alpha) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/4.5-alpha-2/).

Tor Browser 4.5-alpha-2 is based on Firefox ESR 31.3.0, which features [important security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox31.3.0) to Firefox. Additionally, it fixes a regression which caused third party authentication credentials to remain undeleted and contains smaller improvements to the circuit UI and the security slider.

Here is the changelog since 4.5-alpha-1:

-   All Platforms
    -   Update Firefox to 31.3.0esr
    -   Update NoScript to 2.6.9.5
    -   Update HTTPS Everywhere to 5.0developement.1
    -   Update Torbutton to 1.8.1.2
        -   Bug 13672: Make circuit display optional
        -   Bug 13671: Make bridges visible on circuit display
        -   Bug 9387: Incorporate user feedback
        -   Bug 13784: Remove third party authentication tokens
    -   Bug 13435: Remove our custom POODLE fix (fixed by Mozilla in 31.3.0esr)

