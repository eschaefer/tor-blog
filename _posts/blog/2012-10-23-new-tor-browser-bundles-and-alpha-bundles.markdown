---
layout: post
title: "New Tor Browser Bundles and alpha bundles"
permalink: new-tor-browser-bundles-and-alpha-bundles
date: 2012-10-23
author: erinn
category: blog
tags: ["firefox updates", "release candidate", "tbb", "tor browser bundle"]
---

The stable Tor Browser Bundles have been updated to fix a crash bug that existed in the previous version. If you were experiencing problems, please update and [let us know](https://trac.torproject.org) if you have any further problems.

All alpha bundles have also been updated to Tor 0.2.3.23-rc. We've downgraded the Firefox version in the alpha Tor Browser Bundles to 10.0.9esr and will continue to keep the same version of Firefox in both bundles for the foreseeable future. In addition to that, the Linux and OS X versions have automatic port selection re-enabled, so those of you who were experiencing trouble running a concurrent system Tor on those systems should no longer have any issues.

All users who were using Tor 0.2.3.22-rc are strongly encouraged to upgrade.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

Further notes about Tor Browser Bundle updates:

**Tor Browser Bundle (2.2.39-4)**

- Update Firefox patches to prevent crashing (closes: #7128)
- Update HTTPS Everywhere to 3.0.2
- Update NoScript to 2.5.8

**Tor Browser Bundle (2.3.23-alpha-1)**

- Update Tor to 0.2.3.23-rc
- Update Firefox to 10.0.9esr
- Update HTTPS Everywhere to 4.0development.1
- Update NoScript to 2.5.8
- Re-enable automatic Control and SOCKS port selection on Linux and OSX

