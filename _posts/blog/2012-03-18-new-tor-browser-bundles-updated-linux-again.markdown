---
layout: post
title: "New Tor Browser Bundles (updated for Linux again)"
permalink: blog/new-tor-browser-bundles-updated-linux-again
date: 2012-03-18
author: erinn
category: blog
tags: ["firefox", "tbb", "tor browser"]
---

The Tor Browser Bundles have all been updated to the latest Firefox 11.0 as well as a number of bugfixes. Because of a very slow uplink, not all of the Mac OS X 64-bit bundles are available yet, but all of the 32-bit bundles are up, and the [Farsi](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-2.2.35-8-osx-x86_64-fa.zip) ( [sig](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-2.2.35-8-osx-x86_64-fa.zip.asc)) and [English](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-2.2.35-8-osx-x86_64-en-US.zip) ( [sig](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-2.2.35-8-osx-x86_64-en-US.zip.asc)) versions of the 64-bit bundles are also available.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Tor Browser Bundle (2.2.35-9), Linux only**

- Fix launch script to prevent Vidalia from running in debug mode all the time (closes: [#5417](https://trac.torproject.org/projects/tor/ticket/5417))

**Tor Browser Bundle (2.2.35-8)**

- Update Firefox to 11.0
- Update OpenSSL to 1.0.0h
- Update NoScript to 2.3.4
- Update HTTPS Everywhere to 2.0.1
- Always build to with warnings enabled (closes: [#4470](https://trac.torproject.org/projects/tor/ticket/4470))
- Disable HTTPS Everywhere SSL Observatory screen (closes: [#5300](https://trac.torproject.org/projects/tor/ticket/5300))

**Windows**

- Remove tor-resolve from the Windows bundle (closes: [#5403](https://trac.torproject.org/projects/tor/ticket/5403))

**Mac OS X**

- Give OS X users below 10.5 an incompatibility message (closes: [#4356](https://trac.torproject.org/projects/tor/ticket/4356))

**Linux**

- Don't attempt to load the default KDE 4 theme from Vidalia, because that fails when the Qt versions don't match (closes: [#5214](https://trac.torproject.org/projects/tor/ticket/5214))

