---
layout: post
title: "Vidalia 0.2.4 Released"
permalink: vidalia-024-released
date: 2009-09-07 15:13:01
author: phobos
category: blog
status: closed
tags: ["drag and drop OS X install", "msi installer", "polipo", "updated packages", "vidalia releases"]
---

Vidalia 0.2.4 is released. The OS X -alpha bundles are updated to fix a bug in the default "bootstrap" vidalia.conf file that pointed to a non-existent Polipo configuration file, causing Polipo to fail on startup.

The Changelog for this release is: [**read more »**](https://blog.torproject.org/blog/vidalia-024-released)

Split the message log into "Basic" and "Advanced" views. The  
 "Advanced" view contains standard log messages from Tor, while the new  
 experimental "Basic" view displays status events received from Tor.  
 (Ticket \#265)

Apply an application-global stylesheet on OS X that forces all tree  
 widgets in Vidalia to use the 12pt font recommended by Apple's human  
 interface guidelines.

Add an OSX\_FORCE\_32BIT CMake option that can be used to force a 32-bit  
 build on Mac OS X versions that default to 64-bit builds (e.g., Snow  
 Leopard), if only 32-bit versions of the Qt libraries are available.

Fix a bug introduced in 0.2.3 that prevented Vidalia from correctly  

