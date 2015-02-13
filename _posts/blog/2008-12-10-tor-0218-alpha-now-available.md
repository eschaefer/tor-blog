---
layout: post
title: "Tor 0.2.1.8-alpha is now available"
permalink: tor-0218-alpha-now-available
date: 2008-12-10 07:53:21
author: phobos
category: blog
status: closed
tags: ["alpha release", "bugfixes"]
---

Tor 0.2.1.8-alpha fixes some crash bugs in earlier alpha releases,  
 builds better on unusual platforms like Solaris and old OS X, and fixes  
 a variety of other issues.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

Changes in version 0.2.1.8-alpha - 2008-12-08  
 **Major features:**

-   New DirPortFrontPage option that takes an html file and publishes  
     it as "/" on the DirPort. Now relay operators can provide a  
     disclaimer without needing to set up a separate webserver. There's  
     a sample disclaimer in contrib/tor-exit-notice.html.

**Security fixes:**

-   When the client is choosing entry guards, now it selects at most  
     one guard from a given relay family. Otherwise we could end up with  
     all of our entry points into the network run by the same operator.  
     Suggested by Camilo Viecco. Fix on 0.1.1.11-alpha.

**Major bugfixes:**

-   Fix a DOS opportunity during the voting signature collection process  
     at directory authorities. Spotted by rovv. Bugfix on 0.2.0.x.
-   Fix a possible segfault when establishing an exit connection. Bugfix  
     on 0.2.1.5-alpha.

**Minor bugfixes:** [**read more »**](https://blog.torproject.org/blog/tor-0.2.1.8-alpha-now-available)

Get file locking working on win32. Bugfix on 0.2.1.6-alpha. Fixes  
 bug 859.

Made Tor a little less aggressive about deleting expired  
 certificates. Partial fix for bug 854.

Stop doing unaligned memory access that generated bus errors on  
 sparc64. Bugfix on 0.2.0.10-alpha. Fix for bug 862.

Fix a crash bug when changing EntryNodes from the controller. Bugfix  
 on 0.2.1.6-alpha. Fix for bug 867. Patched by Sebastian.

Make USR2 log-level switch take effect immediately. Bugfix on  
 0.1.2.8-beta.

If one win32 nameserver fails to get added, continue adding the  
 rest, and don't automatically fail.
