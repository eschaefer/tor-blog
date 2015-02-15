---
layout: post
title: "Tor Browser 4.0-alpha-3 is released"
permalink: tor-browser-40-alpha-3-released
date: 2014-09-26 03:12:14
author: mikeperry
category: blog
comments: closed
tags: ["tbb", "tbb-4.0", "tor browser", "tor browser bundle"]
---

The third alpha release of the 4.0 series is available from the [extended downloads page](https://www.torproject.org/projects/torbrowser.html.en#downloads-alpha) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/4.0-alpha-3/).

The individual bundles of this release are signed by Georg Koppen. You can find his key fingerprint on the [Signing Keys](https://www.torproject.org/docs/signing-keys.html.en) page. It is:

      pub   4096R/4B7C3223 2013-07-30  Fingerprint = 35CD74C24A9B15A19E1A81A194373AA94B7C3223 

  
  
 **IMPORTANT UPDATER ISSUES**:

-   We discovered [Bug 13245](https://trac.torproject.org/projects/tor/ticket/13245) will cause non-English Tor Browsers to update to the English version. This bug has been fixed in this release, but 4.0a2 users will still be updated to the English version if they use the in-browser updater.
-   Meek Transport users will need to restart their browser a second time after upgrade if they use the in-browser updater. We are still trying to get to the bottom of [this issue.](https://trac.torproject.org/projects/tor/ticket/13247)

This release also features [important security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.8.1) to Firefox.

Here is the complete changelog:

-   All Platforms
    -   Update Tor to 0.2.5.8-rc
    -   Update Firefox to 24.8.1esr
    -   Update meek to 0.11
    -   Update NoScript to 2.6.8.42
    -   Update Torbutton to 1.6.12.3
        -   Bug 13091: Use "Tor Browser" everywhere
        -   Bug 10804: Workaround fix for some cases of startup hang
    -   Bug 13091: Use "Tor Browser" everywhere
    -   Bug 13049: Browser update failure (self.update is undefined)
    -   Bug 13047: Updater should not send Kernel and GTK version
    -   Bug 12998: Prevent intermediate certs from being written to disk
    -   Bug 13245: Prevent non-english TBBs from upgrading to english version.
-   Linux:
    -   Bug 9150: Make RPATH unavailable on Tor binary.
    -   Bug 13031: Add full RELRO protection.

  
  
 The list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) is also available in our bug tracker.
