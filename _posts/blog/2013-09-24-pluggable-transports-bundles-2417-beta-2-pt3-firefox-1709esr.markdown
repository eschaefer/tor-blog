---
layout: post
title: "Pluggable transports bundles 2.4.17-beta-2-pt3 with Firefox 17.0.9esr"
permalink: pluggable-transports-bundles-2417-beta-2-pt3-firefox-1709esr
date: 2013-09-24
author: dcf
category: blog
tags: ["flashproxy", "obfsproxy", "pluggable transports"]
---

There are new Pluggable Transports Tor Browser Bundles with Firefox 17.0.9esr. They are made from the [Tor Browser Bundle release](https://blog.torproject.org/blog/new-tor-browser-bundles-firefox-1709esr) of September 20 and contain important security fixes.

- [Windows](https://www.torproject.org/dist/torbrowser/tor-pluggable-transports-browser-2.4.17-beta-2-pt3_en-US.exe) ( [sig](https://www.torproject.org/dist/torbrowser/tor-pluggable-transports-browser-2.4.17-beta-2-pt3_en-US.exe.asc))
- [Mac OS X](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-Pluggable-Transports-2.4.17-beta-2-pt3-osx-i386-en-US.zip) ( [sig](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-Pluggable-Transports-2.4.17-beta-2-pt3-osx-i386-en-US.zip.asc))
- [GNU/Linux 32-bit](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-i686-2.4.17-beta-2-pt3-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-i686-2.4.17-beta-2-pt3-dev-en-US.tar.gz.asc))
- [GNU/Linux 64-bit](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-x86_64-2.4.17-beta-2-pt3-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-x86_64-2.4.17-beta-2-pt3-dev-en-US.tar.gz.asc))

The bundles contain flash proxy and obfsproxy configured to run by default. If you want to use flash proxy, you will have to take the extra steps listed in the [flash proxy howto](https://trac.torproject.org/projects/tor/wiki/FlashProxyHowto).

These bundles contain the same hardcoded obfs2 bridge addresses as the previous bundles which may work for some jurisdictions but you are strongly advised to get new bridge addresses from [BridgeDB](https://bridges.torproject.org).

