---
layout: post
title: "January 2008 Progress Report"
permalink: january-2008-progress-report
date: 2008-02-18 19:09:33
author: phobos
category: blog
status: closed
tags: ["bridges", "incognito", "progress report", "tor", "torbrowser", "torbutton"]
---

Tor 0.2.0.18-alpha (released Jan 25) adds a sixth v3 directory authority run by CCC, fixes a big memory leak in 0.2.0.17-alpha, and adds new config options that can warn or reject connections to ports generally associated with vulnerable-plaintext protocols.  
 [http://archives.seul.org/or/talk/Jan-2008/msg00442.html](http://archives.seul.org/or/talk/Jan-2008/msg00442.html "http://archives.seul.org/or/talk/Jan-2008/msg00442.html")

Tor 0.2.0.16-alpha and 0.2.0.17-alpha (released Jan 17) add a fifth v3 directory authority run by Karsten Loesing, and generally clean up a lot of features and minor bugs.  
 [http://archives.seul.org/or/talk/Jan-2008/msg00254.html](http://archives.seul.org/or/talk/Jan-2008/msg00254.html "http://archives.seul.org/or/talk/Jan-2008/msg00254.html")

Tor 0.1.2.19 (released Jan 17) fixes a huge memory leak on exit relays, makes the default exit policy a little bit more conservative so it's safer to run an exit relay on a home system, and fixes a variety of smaller issues.  
 [http://archives.seul.org/or/announce/Jan-2008/msg00000.html](http://archives.seul.org/or/announce/Jan-2008/msg00000.html "http://archives.seul.org/or/announce/Jan-2008/msg00000.html")

We continued work on the "BridgeDB" module: major progress on January was to improve robustness of the email subsystem so it is better at detecting forged mails that claim to be from gmail but are actually from elsewhere.

Work continued toward the upcoming Torbutton 1.1.13 release (which came out Feb 1). This new release has several significant security-related fixes:  
 [https://torbutton.torproject.org/dev/CHANGELOG](https://torbutton.torproject.org/dev/CHANGELOG "https://torbutton.torproject.org/dev/CHANGELOG")

Work continued toward the upcoming Vidalia 0.1.0 release: support for launching Firefox and Polipo as supporting applications; support for learning from Tor when the first circuit is ready so it can inform the user; and many other bugfixes including a few security fixes:  
 [http://trac.vidalia-project.net/browser/vidalia/trunk/CHANGELOG](http://trac.vidalia-project.net/browser/vidalia/trunk/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/trunk/CHANGELOG")

We added a "How do I find a bridge?" link and corresponding help text to Vidalia's 'Network' settings page.

From the Tor 0.2.0.16-alpha ChangeLog:  
 “Do not try to download missing certificates until we have tried to check our fallback consensus.” This change gets us closer to being able to bootstrap without ever needing to contact the central directory authorities. [**read more »**](https://blog.torproject.org/blog/january-2008-progress-report)
