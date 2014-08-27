---
layout: post
title: "Tor Browser Bundle for Mac OS X"
permalink: tor-browser-bundle-mac-os-x
date: 2010-09-15
author: erinn
category: blog
tags: ["alpha releases", "portable bundles", "tbb", "torbrowser"]
---

Tor Browser Bundle for Mac OS X is now available for the i386 architecture in 11 languages. **Snow Leopard users** : please read about the known bugs at the bottom of the post.

The Tor Browser Bundle lets you use Tor without needing to install any software. It can run off a USB flash drive, comes with a pre-configured web browser and is self-contained.

You can download it from the [Tor Browser](https://www.torproject.org/torbrowser/) page which also has instructions about how to extract and use it.

The bundle comes with the following software:

- [Tor 0.2.2.15-alpha](https://www.torproject.org/)
- [Vidalia 0.2.10](https://www.torproject.org/vidalia/) -- cross-platform controller GUI for the Tor software
- [Polipo 1.0.4.1](https://www.pps.jussieu.fr/~jch/software/polipo/) -- caching web proxy
- [Firefox/Namoroka 3.6.9](http://www.mozilla.com/firefox/) -- web browser
- [Torbutton 1.2.5](https://www.torproject.org/torbutton/) -- Firefox extension to enable or disable the browser's use of Tor
- [NoScript 2.0.2.3](http://noscript.net/) -- Firefox extension to only allow scripts from trusted sites
- [HTTPS-Everywhere 0.2.2](https://www.eff.org/https-everywhere) -- Firefox extension to provide encryption to a major number of websites

This is a beta version which has primarily been tested on an i386 Leopard machine.

Early testers on Snow Leopard report that Firefox does not launch the first time they launch the Tor Browser Bundle app. The workaround for this is currently to stop Tor with Vidalia and then restart it. They also say that the Torbutton status bar on the bottom of the Firefox window does not show up, but Torbutton functions properly. Please give us feedback and [file bugs](https://trac.torproject.org/).

