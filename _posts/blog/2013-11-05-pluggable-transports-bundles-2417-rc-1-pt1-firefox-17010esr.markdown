---
layout: post
title: "Pluggable transports bundles 2.4.17-rc-1-pt1 with Firefox 17.0.10esr"
permalink: blog/pluggable-transports-bundles-2417-rc-1-pt1-firefox-17010esr
date: 2013-11-05
author: dcf
category: blog
tags: ["flashproxy", "obfsproxy", "pluggable transports"]
---

There are new Pluggable Transports Tor Browser Bundles with Firefox 17.0.10esr. They are made from the [Tor Browser Bundle release](https://blog.torproject.org/blog/new-tor-browser-bundles-firefox-17010esr) of November 1.

- [Windows](https://www.torproject.org/dist/torbrowser/tor-pluggable-transports-browser-2.4.17-rc-1-pt1_en-US.exe) ( [sig](https://www.torproject.org/dist/torbrowser/tor-pluggable-transports-browser-2.4.17-rc-1-pt1_en-US.exe.asc))
- [Mac OS X](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-Pluggable-Transports-2.4.17-rc-1-pt1-osx-i386-en-US.zip) ( [sig](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-Pluggable-Transports-2.4.17-rc-1-pt1-osx-i386-en-US.zip.asc))
- [GNU/Linux 32-bit](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-i686-2.4.17-rc-1-pt1-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-i686-2.4.17-rc-1-pt1-dev-en-US.tar.gz.asc))
- [GNU/Linux 64-bit](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-x86_64-2.4.17-rc-1-pt1-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-x86_64-2.4.17-rc-1-pt1-dev-en-US.tar.gz.asc))

The OS X bundle won't work in the new OS X Mavericks by default. It is caused by some changes in the new operating system release. [We know about this problem and are working on fixing it.](https://trac.torproject.org/projects/tor/ticket/10030) If you are an affected user, you can try [this workaround](https://trac.torproject.org/projects/tor/ticket/10030#comment:9) of placing absolute paths in the torrc file.

The bundles contain flash proxy and obfsproxy configured to run by default. If you want to use flash proxy, you will have to take the extra steps listed in the [flash proxy howto](https://trac.torproject.org/projects/tor/wiki/FlashProxyHowto).

These bundles contain the same hardcoded obfs2 bridge addresses as the previous bundles which may work for some jurisdictions but you are strongly advised to get new bridge addresses from [BridgeDB](https://bridges.torproject.org).

