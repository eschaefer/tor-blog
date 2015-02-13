---
layout: post
title: "February 2008 Progress Report"
permalink: february-2008-progress-report
date: 2008-03-11 19:47:23
author: phobos
category: blog
status: closed
tags: ["progress report", "release candidate", "tor", "torbrowser", "torbutton"]
---

Tor 0.2.0.20-rc (released Feb 24) is the first release candidate for the 0.2.0 series. It makes more progress towards normalizing Tor's TLS handshake, makes hidden services work better again, helps relays bootstrap if they don't know their IP address, adds optional support for linking in openbsd's allocator or tcmalloc, allows really fast relays to scale past 15000 sockets, and fixes a bunch of minor bugs reported by Veracode.  
 [http://archives.seul.org/or/talk/Feb-2008/msg00279.html](http://archives.seul.org/or/talk/Feb-2008/msg00279.html "http://archives.seul.org/or/talk/Feb-2008/msg00279.html")

Tor 0.2.0.19-alpha (released Feb 9) makes more progress towards normalizing Tor's TLS handshake, makes path selection for relays more secure and IP address guessing more robust, and generally fixes a lot of bugs in preparation for calling the 0.2.0 branch stable.  
 [http://archives.seul.org/or/talk/Feb-2008/msg00134.html](http://archives.seul.org/or/talk/Feb-2008/msg00134.html "http://archives.seul.org/or/talk/Feb-2008/msg00134.html")

Torbutton 1.1.13 (released Feb 1), 1.1.14 (released Feb 24), and 1.1.15 (released Feb 26) fix many more potential privacy and identity leaks, mostly based on exploits found by Greg Fleischer. They also add support for automatic updates via the usual Firefox extension upgrade approach.  
 [https://torbutton.torproject.org/dev/CHANGELOG](https://torbutton.torproject.org/dev/CHANGELOG "https://torbutton.torproject.org/dev/CHANGELOG")

Work continued toward the upcoming Vidalia 0.1.0 release (which came out March 1): support for launching Firefox and Polipo as supporting applications; support for learning from Tor when the first circuit is ready so it can inform the user; and many other bugfixes including a few security fixes.  
 [http://trac.vidalia-project.net/browser/vidalia/releases/vidalia-0.1.0/C...](http://trac.vidalia-project.net/browser/vidalia/releases/vidalia-0.1.0/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/releases/vidalia-0.1.0/CHANGELOG")

The Tor 0.2.0.19-alpha release contained many security-related cleanups based on an anonymously submitted code review from a static analysis tool. The Tor 0.2.0.20-rc release contained even more security-related cleanups, based on an external security analysis and audit by Veracode. Hopefully cleanups at this stage will reduce the number of times we need to push out an urgent new stable "0.2.0" release for security reasons. [**read more »**](https://blog.torproject.org/blog/february-2008-progress-report)
