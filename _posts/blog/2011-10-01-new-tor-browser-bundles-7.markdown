---
layout: post
title: "New Tor Browser Bundles"
permalink: new-tor-browser-bundles-7
date: 2011-10-01
author: erinn
category: blog
tags: ["firefox updates", "tbb", "tor", "tor browser bundle"]
---

The Tor Browser Bundles have been updated to Firefox 7.0.1 and Tor 0.2.2.33. The bundles were originally uploaded with Firefox 7.0, but a fix was quickly released, so the two changelogs have been merged in this post.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Tor Browser Bundle (2.2.33-2)**

**Windows fixes**

- Begin building Vidalia with DEP/ASLR

**OS X fixes**

- Stop TBB from logging so much information to the system by only allowing dyld log library loads to syslog when it is in debug mode (closes: #4093)

**General fixes and updates**

- Update Firefox to 7.0.1
- Update OpenSSL to 1.0.0e (closes: #3996) (except for OS X)
- Update Tor to 0.2.2.33
- Update NoScript to 2.1.2.8
- Downgrade HTTPS Everywhere to 1.0.3, because we don't want stable TBBs to use development versions of extensions (closes: #4050)

