---
layout: post
title: "Combined flash proxy + pyobfsproxy browser bundles"
permalink: combined-flash-proxy-pyobfsproxy-browser-bundles
date: 2013-01-14
author: dcf
category: blog
tags: []
---

Please help us test new experimental bundles that have flash proxy and pyobfsproxy enabled by default.

- [Windows](https://people.torproject.org/~dcf/flashproxy/tor-flashproxy-pyobfsproxy-browser-2.4.7-alpha-1_en-US.exe) ( [sig](https://people.torproject.org/~dcf/flashproxy/tor-flashproxy-pyobfsproxy-browser-2.4.7-alpha-1_en-US.exe.asc))
- [Mac OS X](https://people.torproject.org/~dcf/flashproxy/TorBrowser-FlashProxy-PyObfsproxy-2.4.7-alpha-1-osx-i386-en-US.zip) ( [sig](https://people.torproject.org/~dcf/flashproxy/TorBrowser-FlashProxy-PyObfsproxy-2.4.7-alpha-1-osx-i386-en-US.zip.asc))
- [GNU/Linux 32-bit](https://people.torproject.org/~dcf/flashproxy/tor-flashproxy-pyobfsproxy-browser-gnu-linux-i686-2.4.7-alpha-1-dev-en-US.tar.gz) ( [sig](https://people.torproject.org/~dcf/flashproxy/tor-flashproxy-pyobfsproxy-browser-gnu-linux-i686-2.4.7-alpha-1-dev-en-US.tar.gz.asc))
- [GNU/Linux 64-bit](https://people.torproject.org/~dcf/flashproxy/tor-flashproxy-pyobfsproxy-browser-gnu-linux-x86_64-2.4.7-alpha-1-dev-en-US.tar.gz) ( [sig](https://people.torproject.org/~dcf/flashproxy/tor-flashproxy-pyobfsproxy-browser-gnu-linux-x86_64-2.4.7-alpha-1-dev-en-US.tar.gz.asc))

[Flash proxy](http://crypto.stanford.edu/flashproxy/) is a transport that uses proxies running in web browsers as access points into Tor. [pyobfsproxy](https://gitweb.torproject.org/user/asn/pyobfsproxy.git) is a Python implementation of the [obfsproxy](https://www.torproject.org/projects/obfsproxy) modular transport that makes network traffic look unlike normal Tor traffic. Both of these technologies make it harder to block access to Tor. If you previously used the obfsproxy bundle, please upgrade to this bundle, which in addition to flash proxy has new obfsproxy bridges.

[Flash proxy works differently](https://trac.torproject.org/projects/tor/wiki/FlashProxyHowto) than other pluggable transports, and you need to take extra steps to make it work. In particular, **you will probably need to configure port forwarding** in order to receive connections from browser proxies. There are instructions and hints on how to do that at this page: [flash proxy howto](https://trac.torproject.org/projects/tor/wiki/FlashProxyHowto).

These bundles contain fresh obfs2 bridge addresses, which may work for you if the bridges in the obfsproxy bundle are blocked. The bundles also includes an experimental obfs3 bridge—obfs3 is a new protocol designed to be harder to identify than the previous obfs2. If even these new bridges become blocked, you can [find your own obfs2 bridges](https://bridges.torproject.org/?transport=obfs2).

We are looking for feedback on how the bundles work. Please leave comments on the [flash proxy usability wiki page](https://trac.torproject.org/projects/tor/wiki/FlashProxyUsability) or [ticket #7824](https://trac.torproject.org/projects/tor/ticket/7824) with your experience, good or bad.

There are other ways you can help beyond testing the bundles. One is to [run a bridge with pyobfsproxy](https://gitweb.torproject.org/user/asn/pyobfsproxy.git/blob/HEAD:/doc/HOWTO.txt). Another is to [put the flash proxy badge](http://crypto.stanford.edu/flashproxy/#badge-howto) on your web site or blog, or [add it to your Wikipedia profile](https://gitweb.torproject.org/flashproxy.git/blob/HEAD:/modules/mediawiki/custom.js). If you want your browser to continue to be a proxy after a switch to an opt-in model, click the “Yes” button on [the options page](http://crypto.stanford.edu/flashproxy/options.html).

