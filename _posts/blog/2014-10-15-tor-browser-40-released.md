---
layout: post
title: "Tor Browser 4.0 is released"
permalink: tor-browser-40-released
date: 2014-10-15 10:50:49
author: mikeperry
category: blog
status: closed
tags: ["tbb", "tbb-4.0", "tor browser", "tor browser bundle"]
---

**Update (Oct 22 13:15 UTC):** Windows users that are affected by Tor Browser [crashes](https://bugs.torproject.org/13443) might try to avoid this problem by opening "about:config" and setting the preference "media.directshow.enabled" to "false". This is a workaround reported to help while the investigation is still on-going.

**Update (Oct 25 02:32 UTC):** If you are unhappy with the new Firefox 31 UI, please check out [Classic Theme Restorer](https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/).

**Update (Oct 16 20:35 UTC):** The meek transport still needs performance tuning before it matches other more conventional transports. Ticket numbers are now listed in the post.

The first release of the 4.0 series is available from the [Tor Browser Project page](https://www.torproject.org/download/download-easy.html) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/4.0/).

This release features [important security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox31.2.0) to Firefox. Additionally, due to the [POODLE attack](https://poodle.io/), we have also disabled SSLv3 in this release.

The primary user-facing change since the 3.6 series is the transition to Firefox 31-ESR.

More importantly for censored users who were using 3.6, the 4.0 series also features the addition of three versions of the [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek) pluggable transport. **In fact, we believe that both meek-amazon and meek-azure will work in China today, without the need to obtain bridge addresses.** Note though that we still need to improve meek's performance to match other transports, though. so adjust your expectations accordingly. See tickets [\#12428](https://trac.torproject.org/projects/tor/ticket/12428), [\#12778](https://trac.torproject.org/projects/tor/ticket/12778), and [\#12857](https://trac.torproject.org/projects/tor/ticket/12857) for details.

This release also features an in-browser updater, and a completely reorganized bundle directory structure to make this updater possible. This means that simply extracting a 4.0 Tor Browser over a 3.6.6 Tor Browser will not work. Please also be aware that the security of the updater depends on the specific CA that issued the [www.torproject.org](http://www.torproject.org "www.torproject.org") HTTPS certificate (Digicert), and so it still must be activated manually through the Help ("?") "*about browser*" menu option. Very soon, we will support both strong HTTPS site-specific certificate pinning (ticket [\#11955](https://trac.torproject.org/projects/tor/ticket/11955)) and update package signatures (ticket [\#13379](https://trac.torproject.org/projects/tor/ticket/13379)). Until then, we do not recommend using this updater if you need stronger security and normally verify GPG signatures.

There are also a couple behavioral changes relating to NoScript since 3.6. In particular, by default it now enforces script enable/disable for all sub-elements of a page, so you only need to enable scripts once for a page to work, rather than enabling many sub-scripts. This will hopefully make it possible for more people to use the "High Security" setting in our upcoming [Security Slider](https://trac.torproject.org/projects/tor/ticket/9387), which will have Javascript disabled globally via NoScript by default. While we do not recommend per-element whitelisting due to fingerprinting, users who insist on keeping this functionality may wish to check out [RequestPolicy](https://addons.mozilla.org/en-US/firefox/addon/requestpolicy/).

**Note to MacOS users**: We intend to deprecate 32bit OSX bundles very soon. If you are still using 32bit OSX 10.6, you soon will need to either update your OS to a later version, or begin using the [Tails](https://tails.boum.org/) live operating system.

Here is the changelog since 4.0-alpha-3:

-   All Platforms
    -   Update Firefox to 31.2.0esr
    -   Update Torbutton to 1.7.0.1
        -   Bug 13378: Prevent addon reordering in toolbars on first-run.
        -   Bug 10751: Adapt Torbutton to ESR31's Australis UI.
        -   Bug 13138: ESR31-about:tor shows "Tor is not working"
        -   Bug 12947: Adapt session storage blocker to ESR 31.
        -   Bug 10716: Take care of drag/drop events in ESR 31.
        -   Bug 13366: Fix cert exemption dialog when disk storage is enabled.
    -   Update Tor Launcher to 0.2.7.0.1
        -   Translation updates only
    -   Udate fteproxy to 0.2.19
    -   Update NoScript to 2.6.9.1
    -   Bug 13027: Spoof window.navigator useragent values in JS WebWorker threads
    -   Bug 13016: Hide CSS -moz-osx-font-smoothing values.
    -   Bug 13356: Meek and other symlinks missing after complete update.
    -   Bug 13025: Spoof screen orientation to landscape-primary.
    -   Bug 13346: Disable Firefox "slow to start" warnings and recordkeeping.
    -   Bug 13318: Minimize number of buttons on the browser toolbar.
    -   Bug 10715: Enable WebGL on Windows (still click-to-play via NoScript)
    -   Bug 13023: Disable the gamepad API.
    -   Bug 13021: Prompt before allowing Canvas isPointIn\*() calls.
    -   Bug 12460: Several cross-compilation and gitian fixes (see child tickets)
    -   Bug 13186: Disable DOM Performance timers
    -   Bug 13028: Defense-in-depth checks for OCSP/Cert validation proxy usage
    -   Bug 13416: Defend against new SSLv3 attack (poodle).

  
Here is the list of all changes in the 4.0 series since 3.6.6:

-   All Platforms
    -   Update Firefox to 31.2.0esr
    -   Udate fteproxy to 0.2.19
    -   Update Tor to 0.2.5.8-rc (from 0.2.4.24)
    -   Update NoScript to 2.6.9.1
    -   Update Torbutton to 1.7.0.1 (from 1.6.12.3)
        -   Bug 13378: Prevent addon reordering in toolbars on first-run.
        -   Bug 10751: Adapt Torbutton to ESR31's Australis UI.
        -   Bug 13138: ESR31-about:tor shows "Tor is not working"
        -   Bug 12947: Adapt session storage blocker to ESR 31.
        -   Bug 10716: Take care of drag/drop events in ESR 31.
        -   Bug 13366: Fix cert exemption dialog when disk storage is enabled.
    -   Update Tor Launcher to 0.2.7.0.1 (from 0.2.5.6)
        -   Bug 11405: Remove firewall prompt from wizard.
        -   Bug 12895: Mention @riseup.net as a valid bridge request email address
        -   Bug 12444: Provide feedback when “Copy Tor Log” is clicked.
        -   Bug 11199: Improve error messages if Tor exits unexpectedly
        -   Bug 12451: Add option to hide TBB's logo
        -   Bug 11193: Change "Tor Browser Bundle" to "Tor Browser"
        -   Bug 11471: Ensure text fits the initial configuration dialog
        -   Bug 9516: Send Tor Launcher log messages to Browser Console
    -   Bug 13027: Spoof window.navigator useragent values in JS WebWorker threads
    -   Bug 13016: Hide CSS -moz-osx-font-smoothing values.
    -   Bug 13356: Meek and other symlinks missing after complete update.
    -   Bug 13025: Spoof screen orientation to landscape-primary.
    -   Bug 13346: Disable Firefox "slow to start" warnings and recordkeeping.
    -   Bug 13318: Minimize number of buttons on the browser toolbar.
    -   Bug 10715: Enable WebGL on Windows (still click-to-play via NoScript)
    -   Bug 13023: Disable the gamepad API.
    -   Bug 13021: Prompt before allowing Canvas isPointIn\*() calls.
    -   Bug 12460: Several cross-compilation and gitian fixes (see child tickets)
    -   Bug 13186: Disable DOM Performance timers
    -   Bug 13028: Defense-in-depth checks for OCSP/Cert validation proxy usage
    -   Bug 4234: Automatic Update support (off by default)
    -   Bug 11641: Reorganize bundle directory structure to mimic Firefox
    -   Bug 10819: Create a preference to enable/disable third party isolation
    -   Bug 13416: Defend against new SSLv3 attack (poodle).
-   Windows:
    -   Bug 10065: Enable DEP, ASLR, and SSP hardening options
-   Linux:
    -   Bug 13031: Add full RELRO hardening protection.
    -   Bug 10178: Make it easier to set an alternate Tor control port and password
    -   Bug 11102: Set Window Class to "Tor Browser" to aid in Desktop navigation
    -   Bug 12249: Don't create PT debug files anymore

The list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) is also available in our bug tracker.
