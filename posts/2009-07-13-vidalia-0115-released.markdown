---
layout: post
title: "Vidalia 0.1.15 Released"
permalink: vidalia-0115-released
date: 07/13/2009
author: phobos
category: blog
tags: ["bugfixes", "vidalia releases"]
---

Vidalia 0.1.15 is released. It contains fixes for:

- Bump the minimum required Qt version to 4.3.0.
- Remove USE\_QSSLSOCKET as a build option. If your Qt doesn't support !OpenSSL, then you don't get GeoIP lookups.
- Fix the TorPostFlight portion of the OS X bundle installer so it doesn't fail when installing Torbutton.
- Include libeay32.dll in the Windows installers. 

It can be obtained at [https://www.torproject.org/vidalia/](https://www.torproject.org/vidalia/ "https://www.torproject.org/vidalia/")

