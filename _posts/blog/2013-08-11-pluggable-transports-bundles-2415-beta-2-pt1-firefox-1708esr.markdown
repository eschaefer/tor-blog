---
layout: post
title: "Pluggable transports bundles 2.4.15-beta-2-pt1 with Firefox 17.0.8esr"
permalink: pluggable-transports-bundles-2415-beta-2-pt1-firefox-1708esr
date: 2013-08-11
author: dcf
category: blog
tags: ["flashproxy", "obfsproxy", "pluggable transports"]
---

We've updated the Pluggable Transports Tor Browser Bundles with Firefox 17.0.8esr and Tor 0.2.4.15-beta-2. These correspond to the [Tor Browser Bundle release](https://blog.torproject.org/blog/new-tor-browser-bundles-firefox-1708esr) of August 9 and contain important security fixes.

- [Windows](https://www.torproject.org/dist/torbrowser/tor-pluggable-transports-browser-2.4.15-beta-2-pt1_en-US.exe) ( [sig](https://www.torproject.org/dist/torbrowser/tor-pluggable-transports-browser-2.4.15-beta-2-pt1_en-US.exe.asc))
- [Mac OS X](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-Pluggable-Transports-2.4.15-beta-2-pt1-osx-i386-en-US.zip) ( [sig](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-Pluggable-Transports-2.4.15-beta-2-pt1-osx-i386-en-US.zip.asc))
- [GNU/Linux 32-bit](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-i686-2.4.15-beta-2-pt1-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-i686-2.4.15-beta-2-pt1-dev-en-US.tar.gz.asc))
- [GNU/Linux 64-bit](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-x86_64-2.4.15-beta-2-pt1-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-x86_64-2.4.15-beta-2-pt1-dev-en-US.tar.gz.asc))

These bundles contain flash proxy and obfsproxy configured to run by default. If you want to use flash proxy, you will have to take the extra steps listed in the [flash proxy howto](https://trac.torproject.org/projects/tor/wiki/FlashProxyHowto).

These bundles contain the same hardcoded obfs2 bridge addresses as the previous bundles which may work for some jurisdictions but you are strongly advised to get new bridge addresses from [BridgeDB](https://bridges.torproject.org).

These bundles are signed by David Fifield (0x5CD388E5) with [this fingerprint](https://crypto.stanford.edu/flashproxy/#verify-sig).

