---
layout: post
title: "Tor 0.2.2.14-alpha released"
permalink: tor-02214-alpha-released
date: 2010-07-19 04:30:14
author: phobos
category: blog
status: closed
tags: ["alpha release", "directory authority", "geoip", "performance improvements"]
---

Tor 0.2.2.14-alpha greatly improves client-side handling of circuit build  
 timeouts, which are used to estimate speed and improve performance. We  
 also move to a much better GeoIP database, port Tor to Windows CE,  
 introduce new compile flags that improve code security, add an eighth  
 v3 directory authority, and address a lot of more minor issues.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

Packages will be appearing over the next few days or weeks. (We've decided  
 to start announcing alpha versions when they're released, rather than  
 waiting for all the packages first.)

Changes in version 0.2.2.14-alpha - 2010-07-12  
 o Major bugfixes:  
 - Tor directory authorities no longer crash when started with a  
 cached-microdesc-consensus file in their data directory. Bugfix  
 on 0.2.2.6-alpha; fixes bug 1532.  
 - Treat an unset \$HOME like an empty \$HOME rather than triggering an  
 assert. Bugfix on 0.0.8pre1; fixes bug 1522. [**read more »**](https://blog.torproject.org/blog/tor-02214-alpha-released)
