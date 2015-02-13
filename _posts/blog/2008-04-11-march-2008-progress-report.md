---
layout: post
title: "March 2008 Progress Report"
permalink: march-2008-progress-report
date: 2008-04-11 21:02:18
author: phobos
category: blog
status: closed
tags: ["progress report", "release candidate", "torbrowser", "torbutton"]
---

Tor 0.2.0.23-rc (released Mar 24) is the fourth release candidate for the 0.2.0 series. It makes bootstrapping faster if the first directory mirror you contact is down. The bundles also include the new Vidalia 0.1.2 release.  
 [http://archives.seul.org/or/talk/Mar-2008/msg00204.html](http://archives.seul.org/or/talk/Mar-2008/msg00204.html "http://archives.seul.org/or/talk/Mar-2008/msg00204.html")

Tor 0.2.0.22-rc (released Mar 18) is the third release candidate for the 0.2.0 series. It enables encrypted directory connections by default for non-relays, fixes some broken TLS behavior we added in 0.2.0.20-rc, and resolves many other bugs. The bundles also include Vidalia 0.1.1 and Torbutton 1.1.17.  
 [http://archives.seul.org/or/talk/Mar-2008/msg00136.html](http://archives.seul.org/or/talk/Mar-2008/msg00136.html "http://archives.seul.org/or/talk/Mar-2008/msg00136.html")

Tor 0.2.0.21-rc (released Mar 2) is the second release candidate for the 0.2.0 series. It makes Tor work well with Vidalia again, fixes a rare assert bug, and fixes a pair of more minor bugs. The bundles also include Vidalia 0.1.0 and Torbutton 1.1.16.  
 [http://archives.seul.org/or/talk/Mar-2008/msg00025.html](http://archives.seul.org/or/talk/Mar-2008/msg00025.html "http://archives.seul.org/or/talk/Mar-2008/msg00025.html")

Torbutton 1.1.16 (released Mar 3) and 1.1.17 (released Mar 15) fix many more potential privacy and identity leaks, mostly based on exploits found by Greg Fleischer, and try to start adding support for Firefox 3.  
 [https://torbutton.torproject.org/dev/CHANGELOG](https://torbutton.torproject.org/dev/CHANGELOG "https://torbutton.torproject.org/dev/CHANGELOG")

Vidalia 0.1.0 (released Mar 1), 0.1.1 (released Mar 17), and 0.1.2 (released Mar 24) changes the build process from make to cmake, starts doing encrypted geoip fetches rather than plaintext geoip fetches, checks if the user is running a dangerous or obsolete version of Tor and pops up a window warning them, waits to turn the Vidalia taskbar onion green until Tor reports that it has established a circuit, folds in the patches from Tor Browser Bundle to have Vidalia launch a browser and/or an http proxy, and fixes many miscellaneous bugs.  
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.2/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.2/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.2/CHANGELOG")

From the Tor 0.2.0.23-rc ChangeLog: [**read more »**](https://blog.torproject.org/blog/march-2008-progress-report)
