---
layout: post
title: "Torbutton-alpha 1.3.1 released for testing"
permalink: torbutton-alpha-131-released-testing
date: 01/05/2011
author: phobos
category: blog
tags: ["alpha release", "firefox", "torbutton"]
---

Torbutton 1.3.1-alpha has been released at:  
 [https://www.torproject.org/dist/torbutton/torbutton-1.3.1-alpha.xpi](https://www.torproject.org/dist/torbutton/torbutton-1.3.1-alpha.xpi "https://www.torproject.org/dist/torbutton/torbutton-1.3.1-alpha.xpi") and .asc

This release features a fix for the nasty pref dialog issue in 1.3.0 (bug #2011), as well as Firefox 4.0 support. Thanks to new APIs in Firefox 3.5 and better privacy options in Firefox 4, Torbutton has now been simplified as well. While we still provide a number of XPCOM components, the number of native Firefox components we replace has shrunk from 5 to just one.

However, the amount of changes involved in supporting Firefox 4 were substantial, and it is likely that these changes as well as the removal of old code has introduced new bugs. We've done our best to test out operation on Firefox 3.6 and 4.0, but we have not tested Firefox 3.0, and may have missed other issues as well. Please report any issues you notice on our bugtracker: [https://trac.torproject.org/projects/tor/report/14](https://trac.torproject.org/projects/tor/report/14 "https://trac.torproject.org/projects/tor/report/14")

Here is the complete changelog:  
 \* bugfix: bug 1894: Amnesia is now called TAILS (patch from intrigeri)  
 \* bugfix: bug 2315: Remove reference to TorVM (patch from intrigeri)  
 \* bugfix: bug 2011: Fix preference dialog issues (patch from chrisdoble)  
 \* bugfix: Fix some incorrect log lines in RefSpoofer  
 \* new: Support Firefox 4.0 (many changes)  
 \* new: Place button in the nav-bar (FF4 killed the status-bar)  
 \* misc: No longer reimplement the session store, use new APIs instead  
 \* misc: Simplify crash detection and startup mode settings

