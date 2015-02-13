---
layout: post
title: "September 2008 Progress Report"
permalink: september-2008-progress-report
date: 2008-10-14 19:07:12
author: phobos
category: blog
status: closed
tags: ["alpha", "bug fixes", "facebook", "lectures", "media articles", "progress report", "rpm", "stable", "tor browser bundle", "vidalia"]
---

**Releases**  
 Vidalia 0.1.9 (released September 2) fixes a big pile of bugs and inconveniences in the earlier releases. This new release marks the first "stable" release of Vidalia, in that we have now branched into a stable (0.1.x) branch and a development (0.2.x) branch.  
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.9/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.9/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.9/CHANGELOG")

Tor 0.2.0.31 (released September 3) addresses two potential anonymity issues, starts to fix a big bug we're seeing where in rare cases traffic from one Tor stream gets mixed into another stream, and fixes a variety of smaller issues.  
 [http://archives.seul.org/or/announce/Sep-2008/msg00000.html](http://archives.seul.org/or/announce/Sep-2008/msg00000.html "http://archives.seul.org/or/announce/Sep-2008/msg00000.html")

Tor 0.2.1.6-alpha (released September 30) further improves performance and robustness of hidden services, starts work on supporting per-country relay selection, and fixes a variety of smaller issues.  
 [http://archives.seul.org/or/talk/Oct-2008/msg00093.html](http://archives.seul.org/or/talk/Oct-2008/msg00093.html "http://archives.seul.org/or/talk/Oct-2008/msg00093.html")

**Circumvention Enhancements**  
 From the Vidalia 0.1.9 ChangeLog:  
 "Correct the location of the simplified Chinese help files so they will actually load again."

From the Tor 0.2.1.6-alpha ChangeLog:  
 "Start work to allow node restrictions to include country codes. The syntax to exclude nodes in a country with country code XX is "ExcludeNodes {XX}". Patch from Robert Hogan. It still needs some refinement to decide what config options should take priority if you ask to both use a particular node and exclude it."  
 This feature should allow users in China to specify that they don't want to enter (and/or exit) in China, which in theory could provide stronger security for them.

From the Tor 0.2.1.6-alpha ChangeLog:  
 "Allow ports 465 and 587 in the default exit policy again. We had rejected them in 0.1.0.15, because back in 2005 they were commonly misconfigured and ended up as spam targets. We hear they are better locked down these days." [**read more »**](https://blog.torproject.org/blog/september-2008-progress-report)
