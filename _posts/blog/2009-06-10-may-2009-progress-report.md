---
layout: post
title: "May 2009 Progress Report"
permalink: may-2009-progress-report
date: 2009-06-10 13:41:55
author: phobos
category: blog
status: closed
tags: ["anonymity advocacy", "metrics", "progress report", "proposals", "translations"]
---

**New releases**  
 On May 25, we released Tor 0.2.1.15-rc.  
 On May 17, we released Tor VM 0.0.2.  
 On May 25, we released Vidalia 0.1.13 containing [**read more »**](https://blog.torproject.org/blog/may-2009-progress-report)

Remove an old warning on the relay settings page that running a bridge  
 relay requires Tor 0.2.0.8-alpha or newer.

Add a workaround for a bug that prevented Vidalia's tray icon from  
 getting added to the system notification area on Gnome when Vidalia was  
 run on system startup. Patch by Steve Tyree. (Ticket \#247)

Fix a bug that prevented the control panel from displaying when  
 running on the Enlightenment window manager. Patch by Steve Tyree.

Rename the CMake variables used to store the location of Qt's lupdate  
 and lrelease executables. Recent versions of CMake decided to use the  
 same variable name, which was stomping on mine, resulting in the wrong  
 lupdate and lrelease executables being used.
