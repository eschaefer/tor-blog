---
layout: post
title: "March 2009 Progress Report"
permalink: march-2009-progress-report
date: 2009-04-13 07:56:43
author: phobos
category: blog
status: closed
tags: ["alpha release", "bug fixes", "progress report"]
---

**New releases, new hires, new funding**

On March 9, we released Tor 0.2.1.13-alpha. It includes the following fixes and enhancements:

o Major bugfixes:  
 - Correctly update the list of which countries we exclude as exits, when the GeoIP file is loaded or reloaded. Diagnosed by lark. Bugfix on 0.2.1.6-alpha.

o Minor bugfixes (on 0.2.0.x and earlier):  
 - Automatically detect MacOSX versions earlier than 10.4.0, and  
 disable kqueue from inside Tor when running with these versions.  
 We previously did this from the startup script, but that was no  
 help to people who didn't use the startup script. Resolves bug 863.  
 - When we had picked an exit node for a connection, but marked it as  
 "optional", and it turned out we had no onion key for the exit,  
 stop wanting that exit and try again. This situation may not  
 be possible now, but will probably become feasible with proposal [**read more »**](https://blog.torproject.org/blog/march-2009-progress-report)
