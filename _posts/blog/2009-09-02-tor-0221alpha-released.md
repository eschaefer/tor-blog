---
layout: post
title: "Tor 0.2.2.1-alpha released"
permalink: tor-0221alpha-released
date: 2009-09-02 14:32:58
author: phobos
category: blog
status: closed
tags: ["alpha release", "anonymity fixes", "bug fixes", "improvements", "os x", "packages", "safe statistic collection", "security fixes", "vidalia bundle"]
---

Tor 0.2.2.1-alpha disables ".exit" address notation by default, allows  
 Tor clients to bootstrap on networks where only port 80 is reachable,  
 makes it more straightforward to support hardware crypto accelerators,  
 and starts the groundwork for gathering stats safely at relays.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

We've been improving our packages and bundles:  
 **Packaging changes:** [**read more »**](https://blog.torproject.org/blog/tor-0221alpha-released)

Upgrade Vidalia from 0.1.15 to 0.2.3 in the Windows and OS X  
 installer bundles. See  
 [https://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.2.3/CHAN...](https://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.2.3/CHANGELOG "https://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.2.3/CHANGELOG")  
 for details of what's new in Vidalia 0.2.3.

Windows Vidalia Bundle: update Privoxy from 3.0.6 to 3.0.14-beta.

OS X Vidalia Bundle: move to Polipo 1.0.4 with Tor specific  
 configuration file, rather than the old Privoxy.

OS X Vidalia Bundle: Vidalia, Tor, and Polipo are compiled as  
 x86-only for better compatibility with OS X 10.6, aka Snow Leopard.
