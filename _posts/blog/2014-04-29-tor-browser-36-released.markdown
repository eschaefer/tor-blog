---
layout: post
title: "Tor Browser 3.6 is released"
permalink: blog/tor-browser-36-released
date: 2014-04-29
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.6", "tor browser", "tor browser bundle"]
---

The Tor Browser Team is proud to announce the first stable release of the 3.6 series. Packages are available from the [Tor Browser Project page](https://www.torproject.org/download/download-easy.html) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/3.6/).

For users upgrading from Tor Browser 3.5.x, the 3.6 series features fully integrated Pluggable Transport support, including an improved Tor Launcher UI for configuring Pluggable Transport bridges. The Pluggable Transport code is also fully disabled for users who do not configure them. The 3.6 series also changes the MacOS archive format from zip to DMG, which should improve installation usability for Mac users.

This release also includes [important security updates to Firefox](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.5).

Please see the [TBB FAQ listing](https://www.torproject.org/docs/faq.html.en#TBBGeneral) for any issues you may have before contacting support or filing tickets. In particular, the [TBB 3.x section](https://www.torproject.org/docs/faq.html.en#TBB3.x) lists common issues specific to the Tor Browser 3.x series. We also maintain a list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) in our bugtracker.

Here is the complete changelog since TBB 3.5.4:

- All Platforms
  - Update Firefox to 24.5.0esr
  - Include Pluggable Transports by default:

    - Obfsproxy3 0.2.4, Flashproxy 1.6, and FTE 0.2.13 are now included
  - Bug [11586](https://trac.torproject.org/projects/tor/ticket/11586): Include license files for component software in Docs directory.
  - Bug [9010](https://trac.torproject.org/projects/tor/ticket/9010): Add Turkish language support.
  - Bug [9387](https://trac.torproject.org/projects/tor/ticket/9387) testing: Disable JS JIT, type inference, asmjs, and ion.
  - Update NoScript to 2.6.8.20
  - Update Tor Launcher to 0.2.5.4

    - Bug [9665](https://trac.torproject.org/projects/tor/ticket/9665): Localize Tor's unreachable bridges bootstrap error
    - Bug [10418](https://trac.torproject.org/projects/tor/ticket/10418): Provide UI configuration for Pluggable Transports
    - Bug [10604](https://trac.torproject.org/projects/tor/ticket/10604): Allow Tor status & error messages to be translated
    - Bug [10894](https://trac.torproject.org/projects/tor/ticket/10894): Make bridge UI clear that helpdesk is a last resort for bridges
    - Bug [10610](https://trac.torproject.org/projects/tor/ticket/10610): Clarify wizard UI text describing obstacles/blocking
    - Bug [11074](https://trac.torproject.org/projects/tor/ticket/11074): Support Tails use case (XULRunner and optional customizations)
    - Bug [11482](https://trac.torproject.org/projects/tor/ticket/11482): Hide bridge settings prompt if no default bridges.
    - Bug [11484](https://trac.torproject.org/projects/tor/ticket/11484): Show help button even if no default bridges.
  - Update Torbutton to 1.6.9.0:

    - Bug [11242](https://trac.torproject.org/projects/tor/ticket/11242): Fix improper "update needed" message after in-place upgrade.
    - Bug [10398](https://trac.torproject.org/projects/tor/ticket/10398): Ease translation of about:tor page elements
    - Bug [9901](https://trac.torproject.org/projects/tor/ticket/9901): Fix browser freeze due to content type sniffing
    - Bug [10611](https://trac.torproject.org/projects/tor/ticket/10611): Add Swedish (sv) to extra locales to update
    - Bug [7439](https://trac.torproject.org/projects/tor/ticket/7439): Improve download warning dialog text.
    - Bug [11384](https://trac.torproject.org/projects/tor/ticket/11384): Completely remove hidden toggle menu item.
  - Backport Pending Tor Patches:

    - Bug [9665](https://trac.torproject.org/projects/tor/ticket/9665): Report a bootstrap error if all bridges are unreachable
    - Bug [11200](https://trac.torproject.org/projects/tor/ticket/11200): Prevent spurious error message prior to enabling network.
    - Bug [5018](https://trac.torproject.org/projects/tor/ticket/5018): Don't launch Pluggable Transport helpers if not in use
    - Bug [9229](https://trac.torproject.org/projects/tor/ticket/9229): Eliminate 60 second stall during bootstrap with some PTs
    - Bug [11069](https://trac.torproject.org/projects/tor/ticket/11069): Detect and report Pluggable Transport bootstrap failures
    - Bug [11156](https://trac.torproject.org/projects/tor/ticket/11156): Prevent spurious warning about missing pluggable transports

- Mac:
  - Bug [4261](https://trac.torproject.org/projects/tor/ticket/4261): Use DMG instead of ZIP for Mac packages
  - Bug [9308](https://trac.torproject.org/projects/tor/ticket/9308): Prevent install path from leaking in some JS exceptions on Mac and Windows

- Linux:
  - Bug [11190](https://trac.torproject.org/projects/tor/ticket/11190): Switch linux PT build process to python2
  - Bug [10383](https://trac.torproject.org/projects/tor/ticket/10383): Enable NIST P224 and P256 accel support for 64bit builds.

- Windows:
  - Bug [9308](https://trac.torproject.org/projects/tor/ticket/9308): Prevent install path from leaking in some JS exceptions on Mac and Windows

Here is the changelog since the 3.6-beta-2:

- All Platforms
  - Update Firefox to 24.5.0esr
  - Update Tor Launcher to 0.2.5.4
    - Bug [11482](https://trac.torproject.org/projects/tor/ticket/11482): Hide bridge settings prompt if no default bridges.
    - Bug [11484](https://trac.torproject.org/projects/tor/ticket/11484): Show help button even if no default bridges.

  - Update Torbutton to 1.6.9.0
    - Bug [7439](https://trac.torproject.org/projects/tor/ticket/7439): Improve download warning dialog text.
    - Bug [11384](https://trac.torproject.org/projects/tor/ticket/11384): Completely remove hidden toggle menu item.

  - Update NoScript to 2.6.8.20
  - Update fte transport to 0.2.13
  - Backport Pending Tor Patches:
    - Bug [11156](https://trac.torproject.org/projects/tor/ticket/11156): Additional obfsproxy startup error message fixes

  - Bug [11586](https://trac.torproject.org/projects/tor/ticket/11586): Include license files for component software in Docs directory.

- Windows and Mac:
  - Bug [9308](https://trac.torproject.org/projects/tor/ticket/9308): Prevent install path from leaking in some JS exceptions on Mac and Windows builds

