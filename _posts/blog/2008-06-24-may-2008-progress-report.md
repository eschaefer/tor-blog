---
layout: post
title: "May 2008 Progress Report"
permalink: may-2008-progress-report
date: 2008-06-24 22:39:17
author: phobos
category: blog
status: closed
tags: ["bridges", "browser bundle", "progress report", "tor", "torbutton", "vidalia"]
---

Tor 0.2.0.26-rc (released May 13) fixes a major security vulnerability caused by a bug in Debian's OpenSSL packages. All users running any 0.2.0.x version should upgrade, whether they're running Debian or not.  
 [http://archives.seul.org/or/talk/May-2008/msg00048.html](http://archives.seul.org/or/talk/May-2008/msg00048.html "http://archives.seul.org/or/talk/May-2008/msg00048.html")

Vidalia 0.1.3 (released May 25) adds a hidden service configuration UI designed and implemented by Domenik Bork, as well as a few other bugfixes.  
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.3/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.3/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.3/CHANGELOG")

The Tor Browser Bundle 1.0.2 (released May 3) and 1.0.3 (released May 16) include upgraded versions of Tor, Vidalia, Torbutton, and Firefox.

We added three new part-time developers in May. We hired Matt Edman as a part-time employee at the beginning of May, to work on Vidalia maintenance, bugfixes, and new features. We also are funding Karsten Loesing to work on making hidden service rendezvous and interaction faster, and Peter Palfrader to work on lowering the overhead of directory requests, especially during bootstrap, which should directly improve the experience for Tor users on modems or cell phones.

Google has agreed to give us some funding to work on auto-update for Windows. Our plan is for Vidalia to look at the majority-signed network status consensus to decide when to update and to what version (Tor already lists what versions are considered safe, in each network status document). We should actually do the update via Tor if possible, for additional privacy, and we need to make sure to check package signatures to ensure package validity. Last, we need to give the user an interface for these updates, including letting her opt to migrate from one major Tor version to the next.

We continued enhancements to the Chinese and Russian Tor website translations. Vidalia also added a Turkish translation.

From the Vidalia 0.1.3 ChangeLog: [**read more »**](https://blog.torproject.org/blog/may-2008-progress-report)
