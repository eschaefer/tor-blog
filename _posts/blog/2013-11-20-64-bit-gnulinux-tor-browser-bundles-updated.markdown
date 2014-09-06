---
layout: post
title: "64-bit GNU/Linux Tor Browser Bundles updated"
permalink: blog/64-bit-gnulinux-tor-browser-bundles-updated
date: 2013-11-20
author: erinn
category: blog
tags: ["hotfix", "tbb", "tor browser", "tor browser bundle"]
---

It turns out that the 64-bit bundles were a bit crashy because of a change in the way they were built. This change has been reverted and I've updated the stable and RC versions of the 2.x series of GNU/Linux Tor Browser Bundles.

Direct links:
 [Stable 64-bit GNU/Linux Tor Browser Bundle](https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-x86_64-2.3.25-16-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-x86_64-2.3.25-16-dev-en-US.tar.gz.asc))
 [RC 64-bit GNU/Linux Tor Browser Bundle](https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-x86_64-2.4.18-rc-2-dev-en-US.tar.gz) ( [sig](https://www.torproject.org/dist/torbrowser/linux/tor-browser-gnu-linux-x86_64-2.4.18-rc-2-dev-en-US.tar.gz.asc))

**Tor Browser Bundle (2.3.25-16); suite=linux**

- Update 64-bit Linux's mozconfig to --disable-optimize so Tor Browser will
 stop crashing (closes: #10195)

**Tor Browser Bundle (2.4.18-rc-2); suite=linux**

- Update 64-bit Linux's mozconfig to --disable-optimize so Tor Browser will
 stop crashing (closes: #10195)

