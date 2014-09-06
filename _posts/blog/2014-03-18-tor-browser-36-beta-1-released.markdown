---
layout: post
title: "Tor Browser 3.6-beta-1 is released"
permalink: blog/tor-browser-36-beta-1-released
date: 2014-03-18
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.6", "tor browser", "tor browser bundle"]
---

The Tor Browser team is proud to release the first beta in the 3.6 series. Packages are available from the [Tor Browser Project page](https://www.torproject.org/projects/torbrowser.html.en#downloads-beta) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/3.6-beta-1/).

This beta features fully integrated Pluggable Transport support, including an improved Tor Launcher UI for configuring Pluggable Transport bridges. The Pluggable Transport code is also fully disabled for users who do not configure them.

We believe that this approach will allow us to quickly turn 3.6 into a stable release, perhaps as soon as the next point release of TBB.

This release also changes the MacOS archive format from zip to DMG, which should improve installation usability for Mac users.

This release also includes [important security updates to Firefox](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.4).

Please see the [TBB FAQ listing](https://www.torproject.org/docs/faq.html.en#TBBGeneral) for any issues you may have before contacting support or filing tickets. In particular, the [TBB 3.x section](https://www.torproject.org/docs/faq.html.en#TBB3.x) lists common issues specific to the Tor Browser 3.x series.

Here is the complete changelog:

- All Platforms
  - Update Firefox to 24.4.0esr
  - Include Pluggable Transports by default:
  - Obfsproxy3 0.2.4, Flashproxy 1.6, and FTE 0.2.6 are now included
  - Update Tor Launcher to 0.2.5.1

    - Bug [10418](https://trac.torproject.org/projects/tor/ticket/10418): Provide UI configuration for Pluggable Transports
    - Bug [10604](https://trac.torproject.org/projects/tor/ticket/10604): Allow Tor status & error messages to be translated
    - Bug [10894](https://trac.torproject.org/projects/tor/ticket/10894): Make bridge UI clear that helpdesk is a last resort for bridges
    - Bug [10610](https://trac.torproject.org/projects/tor/ticket/10610): Clarify wizard UI text describing obstacles/blocking
    - Bug [11074](https://trac.torproject.org/projects/tor/ticket/11074): Support Tails use case (XULRunner and optional customizations)
  - Update Torbutton to 1.6.7.0:

    - Bug [9901](https://trac.torproject.org/projects/tor/ticket/9901): Fix browser freeze due to content type sniffing
    - Bug [10611](https://trac.torproject.org/projects/tor/ticket/10611): Add Swedish (sv) to extra locales to update
  - Update NoScript to 2.6.8.17
  - Update Tor to 0.2.4.21
  - Backport Pending Tor Patches:

    - Bug [5018](https://trac.torproject.org/projects/tor/ticket/5018): Don't launch Pluggable Transport helpers if not in use
    - Bug [9229](https://trac.torproject.org/projects/tor/ticket/9229): Eliminate 60 second stall during bootstrap with some PTs
    - Bug [11069](https://trac.torproject.org/projects/tor/ticket/11069): Detect and report Pluggable Transport bootstrap failures
    - Bug [11156](https://trac.torproject.org/projects/tor/ticket/11156): Prevent spurious warning about missing pluggable transports
  - Bug [10237](https://trac.torproject.org/projects/tor/ticket/10237): Disable the media cache to prevent disk leaks for videos
  - Bug [10703](https://trac.torproject.org/projects/tor/ticket/10703): Force the default charset to avoid locale fingerprinting
  - Bug [10104](https://trac.torproject.org/projects/tor/ticket/10104): Update gitian to fix LXC build issues (for non-KVM/VT builders)

- Mac:
  - Bug [4261](https://trac.torproject.org/projects/tor/ticket/4261): Use DMG instead of ZIP for Mac packages

- Linux:
  - Bug [9353](https://trac.torproject.org/projects/tor/ticket/9353): Fix keyboard input on Ubuntu 13.10
  - Bug [9896](https://trac.torproject.org/projects/tor/ticket/9896): Provide debug symbols for Tor Browser binary
  - Bug [10472](https://trac.torproject.org/projects/tor/ticket/10472): Pass arguments to the browser from Linux startup script

A list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) with the Tor Browser can be found on our bugtracker. Please check that list and help us diagnose and arrive at solutions for those issues before contacting support.

