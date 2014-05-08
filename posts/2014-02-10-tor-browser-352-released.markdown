---
layout: post
title: "Tor Browser 3.5.2 is released"
permalink: tor-browser-352-released
date: 02/10/2014
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.5", "tor browser", "tor browser bundle"]
---

The 3.5.2 release of the Tor Browser Bundle is now available on the [Download page](https://www.torproject.org/download/download-easy.html). You can also download the bundles directly from the [distribution directory](https://www.torproject.org/dist/torbrowser/3.5.2/).

This release includes [important security updates to Firefox.](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.3)

Please see the [TBB FAQ listing](https://www.torproject.org/docs/faq.html.en#TBBGeneral) for any issues you may have before contacting support or filing tickets. In particular, the [TBB 3.x section](https://www.torproject.org/docs/faq.html.en#TBB3.x) lists common issues specific to the Tor Browser 3.x series.

Here is the list of changes since 3.5.1. The [3.x ChangeLog](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/refs/heads/master:/Bundle-Data/Docs/ChangeLog.txt) is also available.

- Rebase Tor Browser to Firefox 24.3.0ESR
- Bug [10419](https://bugs.torproject.org/10419): Block content window connections to localhost
- Update Torbutton to 1.6.6.0
  - Bug [10800](https://bugs.torproject.org/10800): Prevent findbox exception and popup in New Identity
  - Bug [10640](https://bugs.torproject.org/10640): Fix about:tor's update pointer position for RTL languages.
  - Bug [10095](https://bugs.torproject.org/10095): Fix some cases where resolution is not a multiple of 200x100
  - Bug [10374](https://bugs.torproject.org/10374): Clear site permissions on New Identity
  - Bug [9738](https://bugs.torproject.org/9738): Fix for auto-maximizing on browser start
  - Bug [10682](https://bugs.torproject.org/10682): Workaround to really disable updates for Torbutton
  - Bug [10419](https://bugs.torproject.org/10419): Don't allow connections to localhost if Torbutton is toggled
  - Bug [10140](https://bugs.torproject.org/10140): Move Japanese to extra locales (not part of TBB dist)
  - Bug [10687](https://bugs.torproject.org/10687): Add Basque (eu) to extra locales (not part of TBB dist) 

- Update Tor Launcher to 0.2.4.4
  - Bug [10682](https://bugs.torproject.org/10682): Workaround to really disable updates for Tor Launcher 

- Update NoScript to 2.6.8.13 

