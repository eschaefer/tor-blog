---
layout: post
title: "Tor Browser Bundle 3.5 is released"
permalink: tor-browser-bundle-35-released
date: 12/19/2013
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.0", "tbb-3.5", "tor browser", "tor browser bundle", "tor-browser-bundle"]
---

 **Update 12/20:** Test builds of Pluggable Transport bundles are now available. See inline and see the FAQ link for more details.

The 2.x stable series of the Tor Browser Bundle has officially been deprecated, and all users are encouraged to upgrade to the [3.5 series](https://blog.torproject.org/category/tags/tbb-35).

Packages are now available from the [Tor download page](https://www.torproject.org/download/download-easy.html) as well as the [Tor Package archive](https://archive.torproject.org/tor-package-archive/torbrowser/3.5/).

For now, the Pluggable Transports-capable TBB is still a separate package, maintained by David Fifield. Download them here: [https://people.torproject.org/~dcf/pt-bundle/3.5-pt20131217/](https://people.torproject.org/~dcf/pt-bundle/3.5-pt20131217/). We hope to have combined packages available in a beta soon.

For people already using TBB 3.5rc1, the changes are not substantial, and are included below.

However, for users of TBB 2.x and 3.0, this release includes [important security updates to Firefox](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.2). All users are strongly encouraged to update immediately, as we will not be making further releases in the 2.x or 3.0 series.

In terms of user-facing changes from TBB 2.x, the 3.x series primarily features the replacement of Vidalia with a Firefox-based Tor controller called Tor Launcher. This has resulted in a vast decrease in startup times, and a vast increase in usability. We have also begun work on an [FAQ page](https://trac.torproject.org/projects/tor/wiki/doc/TorBrowserBundle3FAQ) to handle common questions arising from this transition -- where Vidalia went, how to disable JavaScript, how to check signatures, etc.

The [complete changelog](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/refs/heads/master:/Bundle-Data/Docs/ChangeLog.txt) for the 3.x series describes the changes since 2.x.

The set of changes since the 3.5rc1 release is:

- All Platforms
  - Update Tor to 0.2.4.19
  - Update Tor Launcher to 0.2.4.2
    - Bug 10382: Fix a Tor Launcher hang on TBB exit 

  - Update Torbutton to 1.6.5.2
    - Misc: Switch update download URL back to download-easy 

