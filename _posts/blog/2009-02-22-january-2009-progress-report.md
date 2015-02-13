---
layout: post
title: "January 2009 Progress Report"
permalink: january-2009-progress-report
date: 2009-02-22 20:23:37
author: phobos
category: blog
status: closed
tags: ["bug fixes", "progress report", "releases", "security fixes", "translations"]
---

**New releases, new hires, new funding**

Tor 0.2.1.10-alpha (released January 6) fixes two major bugs in bridge  
 relays (one that would make the bridge relay not so useful if it had  
 DirPort set to 0, and one that could let an attacker learn a little bit  
 of information about the bridge's users), and a bug that would cause your  
 Tor relay to ignore a circuit create request it can't decrypt (rather  
 than reply with an error). It also fixes a wide variety of other bugs.  
 [http://archives.seul.org/or/talk/Jan-2009/msg00078.html](http://archives.seul.org/or/talk/Jan-2009/msg00078.html "http://archives.seul.org/or/talk/Jan-2009/msg00078.html")

Tor 0.2.1.11-alpha (released Jan 20) finishes fixing the "if your Tor is  
 off for a week it will take a long time to bootstrap again" bug. It also  
 fixes an important security-related bug reported by Ilja van Sprundel. You  
 should upgrade. (We'll send out more details about the bug once people  
 have had some time to upgrade.)  
 [http://archives.seul.org/or/talk/Jan-2009/msg00171.html](http://archives.seul.org/or/talk/Jan-2009/msg00171.html "http://archives.seul.org/or/talk/Jan-2009/msg00171.html") [**read more »**](https://blog.torproject.org/blog/january-2009-progress-report)
