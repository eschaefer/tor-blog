---
layout: post
title: "Stable Torbutton Release Approaches"
permalink: stable-torbutton-release-approaches
date: 2008-07-06 20:45:08
author: mikeperry
category: blog
status: closed
tags: ["torbutton", "uglyrumors"]
---

For those of you just tuning in: Over the past year, I have been the maintainer of the [Torbutton Firefox extension](https://torbutton.torproject.org/dev/), adding a number of features and security enhancements to transform Torbutton from a simple proxy switcher into a secure way to [fully isolate all browser state](https://torbutton.torproject.org/dev/design/#requirements) from one proxy state to another and defend against all known [privacy and IP address leakage attacks](https://torbutton.torproject.org/dev/design/#adversary).

The release candidate phase of the extension started about a month ago, but with the release of Firefox 3 and Torbutton 1.2.0rc series occurring at the same time, we've hit a number of unexpected rough spots and snags. However, with the 1.2.0rc5 release of Torbutton, I'm pleased to report that the majority of those now seem to be [behind us](https://torbutton.torproject.org/dev/CHANGELOG) (a few annoying [Firefox bugs](https://torbutton.torproject.org/dev/design/#FirefoxBugs) notwithstanding).

Thanks to contributions from [arno](http://www.fdn.fr/~arenevier/), the Cookie Jar features now work with Firefox 3. They have even been improved to allow cookies to persist in memory-based jars across Tor toggle (as opposed to requiring Tor cookies to be written to disk to preserve them), which I personally already find very useful. [**read more »**](https://blog.torproject.org/blog/stable-torbutton-release-approaches)
