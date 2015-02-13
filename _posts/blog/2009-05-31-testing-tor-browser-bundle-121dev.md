---
layout: post
title: "Testing Tor Browser Bundle 1.2.1-dev"
permalink: testing-tor-browser-bundle-121dev
date: 2009-05-31 11:51:53
author: phobos
category: blog
status: closed
tags: ["bug fixes", "plugin scanning", "testing", "tor browser bundle"]
---

This is a testing release of Tor IM Browser Bundle 1.2.1-dev. The only fix in this release so far is an updated prefs.js to fix plugin scanning. The InvalidPrefs.js file no longer appears either. I'm working on the other suggestions from [this comment](http://blog.torproject.org/blog/testing-tor-browser-bundle-120dev#comment-1386).

You can [view the diffs](https://svn.torproject.org/cgi-bin/viewvc.cgi/torbrowser/trunk/build-scripts/config/prefs.js?view=log) to see the changes.

The [bundle](https://www.torproject.org/torbrowser/dist/tor-im-browser-1.2.1-dev_en-US.exe) and associated [signature](https://www.torproject.org/torbrowser/dist/tor-im-browser-1.2.1-dev_en-US.exe.asc) and [sha1](https://www.torproject.org/torbrowser/dist/tor-im-browser-1.2.1-dev_en-US.exe.sha1) files are available too.
