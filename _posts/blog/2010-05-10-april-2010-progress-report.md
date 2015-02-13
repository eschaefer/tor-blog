---
layout: post
title: "April 2010 Progress Report"
permalink: april-2010-progress-report
date: 2010-05-10 15:22:32
author: phobos
category: blog
status: closed
tags: ["alpha releases", "bug fixes", "enhancements", "metrics", "progress report", "tor browser bundle"]
---

**New releases**

On April 24, we released Tor 0.2.2.13-alpha. This version addresses the recent connection and memory overload problems we’ve been seeing on relays, especially relays with their DirPort open. If your relay has been crashing, or you turned it off because it used too many resources, give this release a try.

o Major bugfixes:  
 - Teach relays to defend themselves from connection overload. Relays  
 now close idle circuits early if it looks like they were intended  
 for directory fetches. Relays are also more aggressive about closing  
 TLS connections that have no circuits on them. Such circuits are  
 unlikely to be re-used, and tens of thousands of them were piling  
 up at the fast relays, causing the relays to run out of sockets  
 and memory. Bugfix on 0.2.0.22-rc (where clients started tunneling  
 their directory fetches over TLS).

o Minor features: [**read more »**](https://blog.torproject.org/blog/april-2010-progress-report)
