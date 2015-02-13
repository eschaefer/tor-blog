---
layout: post
title: "March 2010 Progress Report"
permalink: march-2010-progress-report
date: 2010-04-17 19:28:01
author: phobos
category: blog
status: closed
tags: ["advocacy", "progress report", "proposals", "releases", "scalability", "translations"]
---

**New Releases**  
 On March 7th, we released the latest in the -alpha series, Tor 0.2.2.10-alpha. Tor 0.2.2.10-alpha fixes a regression introduced in 0.2.2.9-alpha that could prevent relays from guessing their IP address correctly. It also starts the groundwork for another client-side performance boost, since currently we're not making efficient use of relays that have both the Guard flag and the Exit flag.

o Major bugfixes:  
 - Fix a regression from our patch for bug 1244 that caused relays  
 to guess their IP address incorrectly if they didn't set Address  
 in their torrc and/or their address fails to resolve. Bugfix on  
 0.2.2.9-alpha; fixes bug 1269.

o Major features (performance):  
 - Directory authorities now compute consensus weightings that instruct  
 clients how to weight relays flagged as Guard, Exit, Guard+Exit,  
 and no flag. Clients that use these weightings will distribute [**read more »**](https://blog.torproject.org/blog/march-2010-progress-report)
