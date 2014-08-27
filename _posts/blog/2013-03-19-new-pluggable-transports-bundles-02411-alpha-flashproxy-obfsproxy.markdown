---
layout: post
title: "New Pluggable Transports bundles 0.2.4.11-alpha (flashproxy + obfsproxy)"
permalink: new-pluggable-transports-bundles-02411-alpha-flashproxy-obfsproxy
date: 2013-03-19
author: asn
category: blog
tags: ["flashproxy", "obfsbundle", "obfsproxy", "pluggable transports"]
---

We've updated the Pluggable Transports Tor Browser Bundles with Firefox 17.0.4esr and Tor 0.2.4.11-alpha. These releases have numerous bug fixes and a new Torbutton as well.

- [Windows](https://www.torproject.org/dist/torbrowser/tor-pluggable-transports-browser-2.4.11-alpha-2_en-US.exe) ( [sig](https://www.torproject.org/dist/torbrowser/tor-pluggable-transports-browser-2.4.11-alpha-2_en-US.exe.asc))
- [Mac OS X](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-Pluggable-Transports-2.4.11-alpha-2-osx-i386-en-US.zip) ( [sig](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-Pluggable-Transports-2.4.11-alpha-2-osx-i386-en-US.zip.asc))
- [GNU/Linux 32-bit](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-i686-2.4.11-alpha-2-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-i686-2.4.11-alpha-2-dev-en-US.tar.gz.asc))
- [GNU/Linux 64-bit](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-x86_64-2.4.11-alpha-2-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-pluggable-transports-browser-gnu-linux-x86_64-2.4.11-alpha-2-dev-en-US.tar.gz.asc))

Like the previous bundles, these contain Flashproxy and the Python version of Obfsproxy.

[Flash proxy](http://crypto.stanford.edu/flashproxy/) is a transport that uses proxies running in web browsers as access points into Tor. [Obfsproxy](https://gitweb.torproject.org/pluggable-transports/pyobfsproxy.git) is a pluggable transport that makes network traffic look unlike normal Tor traffic. Both of these technologies make it harder to block access to Tor. If you previously used the obfsproxy bundle, please upgrade to this bundle, which in addition to flash proxy has new obfsproxy bridges.

[Flash proxy works differently](https://trac.torproject.org/projects/tor/wiki/FlashProxyHowto) from other pluggable transports, and you need to take extra steps to make it work. In particular, **you will probably need to configure port forwarding** in order to receive connections from browser proxies. There are instructions and hints on how to do that at this page: [flash proxy howto](https://trac.torproject.org/projects/tor/wiki/FlashProxyHowto).

These bundles contain the same hardcoded obfs2 bridge addresses as the previous bundles which may work for some jurisdictions but you are strongly advised to get new bridge addresses from BridgeDB: [https://bridges.torproject.org/?transport=obfs2](https://bridges.torproject.org/?transport=obfs2 "https://bridges.torproject.org/?transport=obfs2").

Furthermore, we are looking for feedback on how the bundles work. Please leave comments on the [flash proxy usability wiki page](https://trac.torproject.org/projects/tor/wiki/FlashProxyUsability) or [ticket #7824](https://trac.torproject.org/projects/tor/ticket/7824) with your experience, good or bad.

There are other ways you can help beyond testing the bundles. One is to [run a bridge with pyobfsproxy](https://gitweb.torproject.org/user/asn/pyobfsproxy.git/blob/HEAD:/doc/HOWTO.txt). Another is to [put the flash proxy badge](http://crypto.stanford.edu/flashproxy/#badge-howto) on your web site or blog, or [add it to your Wikipedia profile](https://gitweb.torproject.org/flashproxy.git/blob/HEAD:/modules/mediawiki/custom.js). If you want your browser to continue to be a proxy after a switch to an opt-in model, click the “Yes” button on [the options page](http://crypto.stanford.edu/flashproxy/options.html).

