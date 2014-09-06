---
layout: post
title: "New Tor Browser Bundles"
permalink: blog/new-tor-browser-bundles-5
date: 2011-09-05
author: erinn
category: blog
tags: ["firefox privacy", "firefox updates", "security fixes", "tbb", "tor browser"]
---

The Tor Browser Bundles have been updated again, this time with Firefox 6.0.2, Torbutton 1.4.2, and more privacy-enhancing patches. **Windows users:** if you had problems running the last bundles, please try this. We believe the problem is fixed, but let us [know](https://trac.torproject.org/) if it's not.

[https://www.torproject.org/download/download-easy](https://www.torproject.org/download/download-easy "https://www.torproject.org/download/download-easy")

**Tor Browser Bundle (2.2.32-3)**

- Update Firefox to 6.0.2
- New Firefox patches:

  - Improve cache APIs to enable better isolation (closes: #3666)
  - Provide auth headers to on-modify-request (closes: #3907)
  - Randomize HTTP pipelining as an experimental website traffic fingerprinting defense (closes: #3914)
  - Enable HTTP pipelining in TBB prefs.js (closes: #3913)
- Update Torbutton to 1.4.2

  - bug 3879: Fix broken framed sites (yopmail, gmane, gmaps, etc)
  - bug 3337: Fetch check.tp.o page to check versions (TBB only)
  - Bug 3754: Fix SafeCache OCSP errors (fix for TBB only)
- Update NoScript to 2.1.2.7

**Windows fixes**

- Add missing C runtime libraries so WinXP users can use TBB again. Fix found by velope.

**Linux fixes**

- Update libpng to 1.4.8 (closes: #3906)
- Make the TBB launch script work when using a relative symlink (closes: #2525)

