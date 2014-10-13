---
layout: post
title: "Tor Browser 3.6.5 and 4.0-alpha-2 are released"
permalink: tor-browser-365-and-40-alpha-2-are-released
date: 2014-09-03
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.6", "tor browser", "tor browser bundle"]
---

# Tor Browser 3.6.5

The fifth pointfix release of the 3.6 series is available from the [Tor Browser Project page](https://www.torproject.org/download/download-easy.html) and also from our [distribution directory](https://www.torproject.org/dist/torbrowser/3.6.5/).

This release features [important security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.8) to Firefox.

This release also features improvements to the canvas image extraction permissions prompt, and will now log offending script urls to the browser console. It also restores the missing RELRO hardening option to the Linux bundles, and disables NTLM and Negotiate HTTP auth (which can leak sensitive information about the computer). To avoid resolution fingerprinting, popups are also opened in new tabs by default.

Here is the complete changelog for 3.6.5:

- All Platforms
  - Update Firefox to 24.8.0esr
  - Update NoScript to 2.6.8.39
  - Update HTTPS Everywhere to 4.0.0
  - Update Torbutton to 1.6.12.1
    - Bug 12684: New strings for canvas image extraction message
    - Bug 8940: Move RecommendedTBBVersions file to [www.torproject.org](http://www.torproject.org "www.torproject.org")
    - Bug 9531: Workaround to avoid rare hangs during New Identity 

  - Bug 12684: Improve Canvas image extraction permissions prompt
  - Bug 7265: Only prompt for first party canvas access. Log all scripts  
 that attempt to extract canvas images to Browser console.
  - Bug 12974: Disable NTLM and Negotiate HTTP Auth
  - Bug 2874: Remove Components.\* from content access (regression)
  - Bug 9881: Open popups in new tabs by default 

- Linux:
  - Bug 12103: Adding RELRO hardening back to browser binaries. 

# Tor Browser 4.0-alpha-2

In addition, we are also releasing the second alpha in the 4.0 series, available for download on the [extended downloads page](https://www.torproject.org/projects/torbrowser.html.en#downloads-alpha).

This release also includes [important security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.8) to Firefox.

In addition to including the changes in 3.6.5, this release also is the first Tor Browser release to enable the in-browser Firefox-based updater. This means that if all goes well, 4.0-alpha-2 users will notified of an available update via a notification similar to that in Firefox. You will then be able to download and install it directly via the browser UI. By default, neither the download nor the update will happen automatically, so if you are not feeling adventurous, you need not allow it to update in this way. Even if you are feeling adventurous, you should probably back up your Tor Browser directory before updating.

In addition to the updater, this release should also re-enable the basic hardening features on Windows, including ASLR, DEP, and SSP.

Furthermore, the NoScript behavior in this release has changed. Selecting "Temporarily allow scripts" will now automatically allow all scripts in a page. This was done for usability reasons, to make it easier for novice users to run Tor Browser with scripting disabled most of the time. This will also hopefully make it possible for more people to use the "High Security" setting in our upcoming [Security Slider](https://trac.torproject.org/projects/tor/ticket/9387), which will have Javascript disabled globally via NoScript by default.

Here is the complete changelog for 4.0-alpha-2:

- All Platforms
  - Update Firefox to 24.8.0esr
  - Update NoScript to 2.6.8.39
  - Update Tor Launcher to 0.2.7.0
    - Bug 11405: Remove firewall prompt from wizard.
    - Bug 12895: Mention @riseup.net as a valid bridge request email address
    - Bug 12444: Provide feedback when “Copy Tor Log” is clicked.
    - Bug 11199: Improve error messages if Tor exits unexpectedly 

  - Update Torbutton to 1.6.12.1
    - Bug 12684: New strings for canvas image extraction message
    - Bug 8940: Move RecommendedTBBVersions file to [www.torproject.org](http://www.torproject.org "www.torproject.org")

  - Bug 12684: Improve Canvas image extraction permissions prompt
  - Bug 7265: Only prompt for first party canvas access. Log all scripts  
 that attempt to extract canvas images to Browser console.
  - Bug 12974: Disable NTLM and Negotiate HTTP Auth
  - Bug 2874: Remove Components.\* from content access (regression)
  - Bug 4234: Automatic Update support (off by default)
  - Bug 9881: Open popups in new tabs by default
  - Meek Pluggable Transport:
    - Bug 12766: Use TLSv1.0 in meek-http-helper to blend in with Firefox 24 

- Windows:
  - Bug 10065: Enable DEP, ASLR, and SSP hardening options 

- Linux:
  - Bug 12103: Adding RELRO hardening back to browser binaries. 

The list of [frequently encountered known issues](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) is also available in our bug tracker.

