---
layout: post
title: "Tor Browser Bundle 1.2.1 Released"
permalink: blog/tor-browser-bundle-121-released
date: 2009-06-21
author: phobos
category: blog
tags: ["bug fixes", "firefox updates", "pidgin updates", "tor browser bundle"]
---

[Tor Browser Bundle 1.2.1](https://www.torproject.org/torbrowser/) is released. The major changes are:

- changes to Firefox to stop scanning for plugins such as Java, Windows Media, etc. These were disabled by torbutton, but still showed up in Firefox. More work will continue on this task
- Include OpenSSL dll (ssleay32.dll) so we're not relying upon the system ssl dll. This should fix Vidalia errors relating to ssl differences.

The official changelog is:

- Better updates to Firefox to stop scanning for plugins on start
- Update Pidgin to 2.5.6r2
- Update Firefox to 3.0.11
- Include OpenSSL 0.9.8k DLL and stop using the system ssl dll
- Update Tor to 0.2.1.16-rc

