---
layout: post
title: "Tor Browser 3.6.4 and 4.0-alpha-1 are released"
permalink: tor-browser-364-and-40-alpha-1-are-released
date: 2014-08-12 16:48:07
author: erinn
category: blog
comments: closed
tags: ["tbb", "tbb-3.6", "tbb-4.0", "tor browser", "tor browser bundle"]
---

The fourth pointfix release of the 3.6 series is available from the [Tor Browser Project page](https://www.torproject.org/download/download-easy.html) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/3.6.4/).

This release features an update to OpenSSL to address the latest round of [OpenSSL security issues](https://www.openssl.org/news/secadv_20140806.txt). Tor Browser should only be vulnerable to one of these issues - the null pointer dereference. As this issue is only a DoS, we are not considering this a critical security update, but users are advised to upgrade anyway. This release also features an update to Tor to alert users of the [RELAY\_EARLY attack](https://blog.torproject.org/blog/tor-security-advisory-relay-early-traffic-confirmation-attack) via a log message, and a fix for a hang that was happening to some users at startup/Tor network bootstrap.

Here is the complete changelog for 3.6.4:

**Tor Browser 3.6.4 -- All Platforms**

Update Tor to 0.2.4.23

Update Tor launcher to 0.2.5.6

Update OpenSSL to 1.0.1i

Backported Tor Patches:

-   Bug 11654: Properly apply the fix for malformed bug11156 log message
-   Bug 11200: Fix a hang during bootstrap introduced in the initial  
     bug11200 patch.

Update NoScript to 2.6.8.36

-   Bug 9516: Send Tor Launcher log messages to Browser Console

Update Torbutton to 1.6.11.1

-   Bug 11472: Adjust about:tor font and logo positioning to avoid overlap
-   Bug 12680: Fix Torbutton about url.

In addition, we are also releasing the first alpha of the 4.0 series, available for download on the [extended downloads page](https://www.torproject.org/projects/torbrowser.html.en#downloads-alpha).

This alpha paves the way to our upcoming autoupdater by reorganizing the directory structure of the browser. This means that in-place upgrades from Tor Browser 3.6 (by extracting/copying over the old directory) will not work.

This release also features Tor 0.2.5.6, and some new defaults for NoScript to make the script permissions for a given url bar domain automatically cascade to all third parties by default (though this may be changed in the NoScript configuration).

**Tor Browser 4.0-alpha-1 -- All Platforms**

Ticket 10935: Include the Meek Pluggable Transport (version 0.10)

-   Two modes of Meek are provided: Meek over Google and Meek over Amazon

Update Firefox to 24.7.0esr

Update Tor to 0.2.5.6-alpha

Update OpenSSL to 1.0.1i

Update NoScript to 2.6.8.36

-   Script permissions now apply based on URL bar

Update HTTPS Everywhere to 5.0development.0

Update Torbutton to 1.6.12.0

-   Bug 12221: Remove obsolete Javascript components from the toggle era
-   Bug 10819: Bind new third party isolation pref to Torbutton security UI
-   Bug 9268: Fix some window resizing corner cases with DPI and taskbar size.
-   Bug 12680: Change Torbutton URL in about dialog.
-   Bug 11472: Adjust about:tor font and logo positioning to avoid overlap
-   Bug 9531: Workaround to avoid rare hangs during New Identity

Update Tor Launcher to 0.2.6.2

-   Bug 11199: Improve behavior if tor exits
-   Bug 12451: Add option to hide TBB's logo
-   Bug 11193: Change "Tor Browser Bundle" to "Tor Browser"
-   Bug 11471: Ensure text fits the initial configuration dialog
-   Bug 9516: Send Tor Launcher log messages to Browser Console

Bug 11641: Reorganize bundle directory structure to mimic Firefox

Bug 10819: Create a preference to enable/disable third party isolation

Backported Tor Patches:

-   Bug 11200: Fix a hang during bootstrap introduced in the initial  
     bug11200 patch.

**Tor Browser 4.0-alpha-1 -- Linux Changes**

-   Bug 10178: Make it easier to set an alternate Tor control port and password
-   Bug 11102: Set Window Class to "Tor Browser" to aid in Desktop navigation
-   Bug 12249: Don't create PT debug files anymore

The list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) is also available in our bug tracker.
