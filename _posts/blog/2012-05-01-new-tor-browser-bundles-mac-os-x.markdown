---
layout: post
title: "New Tor Browser Bundles for Mac OS X"
permalink: new-tor-browser-bundles-mac-os-x
date: 2012-05-01
author: erinn
category: blog
tags: ["osx", "tbb", "tor browser bundle", "torbrowser"]
---

We recently switched our build machine to Lion (OS X 10.7) which had some unintended effects on the Firefox/TorBrowser build. After consulting with Mozilla developers, Sebastian Hahn was able to nail down the problem and provide a [fix](https://gitweb.torproject.org/torbrowser.git/commitdiff/1b56e945bbd5a772f895dd9d3a818f2e606a430d). The Mac OS X Tor Browser Bundles have been updated so they should stop crashing for everyone now. Thanks for your patience!

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Tor Browser Bundle (2.2.35-10)**

- Make TorBrowser stop crashing on random websites by building with clang instead of llvm-gcc. (closes: [#5697](https://trac.torproject.org/projects/tor/ticket/5697))

