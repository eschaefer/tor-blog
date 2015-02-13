---
layout: post
title: "Tor 0.2.1.13-alpha released"
permalink: tor-02113alpha-released
date: 2009-03-13 00:32:59
author: phobos
category: blog
status: closed
tags: ["alpha release", "bug fixes", "security fixes"]
---

Tor 0.2.1.13-alpha includes another big pile of minor bugfixes and  
 cleanups. We're finally getting close to a release candidate.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

Changes in version 0.2.1.13-alpha - 2009-03-09  
 **Major bugfixes:**

-   Correctly update the list of which countries we exclude as  
     exits, when the GeoIP file is loaded or reloaded. Diagnosed by  
     lark. Bugfix on 0.2.1.6-alpha.

**Minor bugfixes (on 0.2.0.x and earlier):**

Automatically detect MacOSX versions earlier than 10.4.0, and  
 disable kqueue from inside Tor when running with these versions.  
 We previously did this from the startup script, but that was no  
 help to people who didn't use the startup script. Resolves bug 863.

When we had picked an exit node for a connection, but marked it as  
 "optional", and it turned out we had no onion key for the exit, [**read more »**](https://blog.torproject.org/blog/tor-02113alpha-released)
