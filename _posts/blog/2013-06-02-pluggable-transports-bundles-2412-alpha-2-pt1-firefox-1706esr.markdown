---
layout: post
title: "Pluggable transports bundles 2.4.12-alpha-2-pt1 with Firefox 17.0.6esr"
permalink: pluggable-transports-bundles-2412-alpha-2-pt1-firefox-1706esr
date: 2013-06-02
author: dcf
category: blog
tags: ["flashproxy", "obfsbundle", "obfsproxy", "pluggable transports"]
---

We've updated the Pluggable Transports Tor Browser Bundles with Firefox 17.0.6esr and Tor 0.2.4.11-alpha. These correspond to the [Tor Browser Bundle release](https://blog.torproject.org/blog/new-tor-browser-bundles-firefox-1706esr) of May 14.

- [Windows](https://www.torproject.org/dist/torbrowser/tor-pluggable-transports-browser-2.4.12-alpha-2-pt1_en-US.exe) ( [sig](https://www.torproject.org/dist/torbrowser/tor-pluggable-transports-browser-2.4.12-alpha-2-pt1_en-US.exe.asc))
- [Mac OS X](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-Pluggable-Transports-2.4.12-alpha-2-pt1-osx-i386-en-US.zip) ( [sig](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-Pluggable-Transports-2.4.12-alpha-2-pt1-osx-i386-en-US.zip.asc))
- [GNU/Linux 32-bit](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-i686-2.4.12-alpha-2-pt1-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-i686-2.4.12-alpha-2-pt1-dev-en-US.tar.gz.asc))
- [GNU/Linux 64-bit](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-x86_64-2.4.12-alpha-2-pt1-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-x86_64-2.4.12-alpha-2-pt1-dev-en-US.tar.gz.asc))

These bundles contain contain flash proxy and obfsproxy configured to run by default. Flash proxy has a new faster registration method, [flashproxy-reg-appspot](https://trac.torproject.org/projects/tor/ticket/8860). The existing flashproxy-reg-email and flashproxy-reg-http will be tried if flashproxy-reg-appspot doesn't work.

If you want to use flash proxy, you will have to take the extra steps listed in the [flash proxy howto](https://trac.torproject.org/projects/tor/wiki/FlashProxyHowto).

These bundles contain the same hardcoded obfs2 bridge addresses as the previous bundles which may work for some jurisdictions but you are strongly advised to get new bridge addresses from BridgeDB: [https://bridges.torproject.org/?transport=obfs2](https://bridges.torproject.org/?transport=obfs2 "https://bridges.torproject.org/?transport=obfs2") [https://bridges.torproject.org/?transport=obfs3](https://bridges.torproject.org/?transport=obfs3 "https://bridges.torproject.org/?transport=obfs3").

These bundles are signed by David Fifield (0x5CD388E5) with [this fingerprint](https://crypto.stanford.edu/flashproxy/#verify-sig).

