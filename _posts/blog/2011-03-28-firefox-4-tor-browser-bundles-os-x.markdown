---
layout: post
title: "Firefox 4 Tor Browser Bundles for OS X"
permalink: blog/firefox-4-tor-browser-bundles-os-x
date: 2011-03-28
author: erinn
category: blog
tags: ["apple osx love", "bug fixes", "tbb", "tor browser bundle", "torbrowser", "updated packages"]
---

 **UPDATE:** there were some issues with the first set of bundles which have been fixed. I've updated the links below. The changelog is [here](https://gitweb.torproject.org/erinn/torbrowser.git/commitdiff/f9a70aadab4d4a950d55df0f373bb4804ef9e012?hp=48cb945f7f180baad7f536405d4a0cf3ddfa3714).

We have new Firefox 4 Tor Browser Bundles available for OS X. (Worry not, users of other operating systems, your turn is coming in the next few days!) They come in 64- and 32-bit versions, and one important fix for 10.6 64-bit users is that Firefox no longer crashes on initial startup. These are alpha, but they are going to be a permanent addition to the Tor Browser Bundle family and will be maintained from now on. You can download them here:

- [64-bit OS X Tor Browser Bundle with Firefox 4](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-2.2.23-2-alpha-osx-x86_64-en-US.zip) ( [sig](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-2.2.23-12alpha-osx-x86_64-en-US.zip.asc))
- [32-bit OS X Tor Browser Bundle with Firefox 4](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-2.2.23-2-alpha-osx-i386-en-US.zip) ( [sig](https://www.torproject.org/dist/torbrowser/osx/TorBrowser-2.2.23-2-alpha-osx-i386-en-US.zip.asc))

These have thus far only been tested on Snow Leopard, but the 32-bit bundle ought to work on Leopard. If it doesn't please let me know! And as usual, please [file any bugs](https://trac.torproject.org/projects/tor) you discover.

**Tor Browser Bundle (2.2.23-1) alpha; suite=osx**

- Create new bundles for Firefox 4, both i386 and x86\_64 (closes: [#2140](https://trac.torproject.org/projects/tor/ticket/2140))
- Update Tor to 0.2.2.23-alpha
- Update Torbutton to 1.3.2-alpha
- Update OpenSSL to 1.0.0d
- Update HTTPS-Everywhere to 0.9.9.development.4
- Update NoScript to 2.0.9.9
- Update BetterPrivacy to 1.49

