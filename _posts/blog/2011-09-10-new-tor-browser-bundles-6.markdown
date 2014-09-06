---
layout: post
title: "New Tor Browser Bundles"
permalink: blog/new-tor-browser-bundles-6
date: 2011-09-10
author: erinn
category: blog
tags: ["bug fixes", "tbb", "torbrowser"]
---

The Tor Browser Bundles have been updated with a bunch of bug fixes.

**Important note to Windows users:** in the last release we enabled automatic port selection for Tor and this had very unexpected side effects on many Windows machines. It turns out that there are a number of consumer firewalls that don't like things connecting on high ports, which was the default. We're looking into [smarter](https://trac.torproject.org/projects/tor/ticket/3943) [ways](https://trac.torproject.org/projects/tor/ticket/3948) to handle this failure mode, but until we find one, we have reverted the behavior to using the previous static port. We're very sorry for the huge inconvenience this caused and hope you will find these bundles more bug-free! As ever, if you don't, please [let us know](https://trac.torproject.org/).
 [https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Tor Browser Bundle (2.2.32-4)**

**Windows fixes**
  - Disable automatic port selection to accommodate Windows users with
 firewalls that don't allow connections or traffic on high ports (closes: #3952, #3945)

**Linux fixes**

  - Fix Makefile to allow for automatic retrieval of Qt and libpng (closes: #2255)
  - Remove symlinks from tarball (closes: #2312)

**General fixes and updates**

  - New Firefox patches

    - Prevent Firefox from loading all system plugins besides Flash (closes: #2826, #3547)
    - Prevent content-preferences service from writing website urls and their settings to disk (closes: #3229)
  - Update Torbutton to 1.4.3

    - Don't let Torbutton inadvertently enable automatic updating in Firefox (closes: #3933)
    - Fix auto-scroll on Twitter (closes: #3960)
    - Allow site zoom information to be stored (closes: #3928)
    - Make permissions and disk errors human-readable (closes: #3649)

