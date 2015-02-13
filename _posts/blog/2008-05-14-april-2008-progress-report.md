---
layout: post
title: "April 2008 Progress Report"
permalink: april-2008-progress-report
date: 2008-05-14 11:53:24
author: phobos
category: blog
status: closed
tags: ["progress report", "release candidate", "torbrowser", "torbutton", "translation"]
---

Tor 0.2.0.24-rc (released Apr 22) adds dizum (run by Alex de Joode)  
 as the new sixth v3 directory authority, makes relays with dynamic IP  
 addresses and no DirPort notice more quickly when their IP address  
 changes, fixes a few rare crashes and memory leaks, and fixes a few  
 other miscellaneous bugs. Tor 0.2.0.25-rc (released Apr 23) makes Tor  
 work again on OS X and certain BSDs.  
 [http://archives.seul.org/or/talk/May-2008/msg00014.html](http://archives.seul.org/or/talk/May-2008/msg00014.html "http://archives.seul.org/or/talk/May-2008/msg00014.html")

Torbutton 1.1.18 (released Apr 17) fixes many usability and interoperability  
 items, in an attempt to make the new Torbutton not so obnoxious in its  
 zeal to protect the user. It also includes new translations for French,  
 Russian, Farsi, Italian, and Spanish.

We did a complete overhaul of the [https://check.torproject.org/](https://check.torproject.org/ "https://check.torproject.org/")  
 page. Now it accepts a language choice,  
 e.g. [https://check.torproject.org/?lang=fa-IR](https://check.torproject.org/?lang=fa-IR "https://check.torproject.org/?lang=fa-IR")  
 Available languages are German, English, Spanish, Italian, Farsi,  
 Japanese, Polish, Portugese, Russian, and Chinese. The Tor Browser  
 Bundle automatically uses the appropriate language as its home page,  
 based on which language of the Browser Bundle was downloaded.

Started on a documentation page to explain to users what bridges are,  
 how they can decide whether they need one, and how to configure their  
 Tor client to use them:  
 [https://www.torproject.org/bridges.html](https://www.torproject.org/bridges.html "https://www.torproject.org/bridges.html")

We've also started working on a design proposal for making it easier  
 to set up a private or testing Tor network. With the advent of the v3  
 directory protocol, it currently takes up to 30 minutes before a test  
 network will produce a useful networkstatus consensus. Also, there are  
 a dozen different config options that need to be set correctly for  
 a Tor network running on a single IP address to not trigger various  
 security defenses. This approach should let more people set up their  
 own Tor networks, either for testing or because they can't reach the  
 main Tor network. [**read more »**](https://blog.torproject.org/blog/april-2008-progress-report)
