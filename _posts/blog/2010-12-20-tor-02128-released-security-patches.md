---
layout: post
title: "Tor 0.2.1.28 is released (security patches)"
permalink: tor-02128-released-security-patches
date: 2010-12-20 11:05:03
author: phobos
category: blog
status: closed
tags: ["bug fixes", "enhancements", "security advisory"]
---

Tor 0.2.1.28 does some code cleanup to reduce the risk of remotely  
 exploitable bugs. Thanks to Willem Pinckaers for notifying us of the  
 issue. The Common Vulnerabilities and Exposures project has assigned  
 CVE-2010-1676 to this issue.

We also took this opportunity to change the IP address for one of our  
 directory authorities, and to update the geoip database we ship.

All Tor users should upgrade.

[https://www.torproject.org/download/download](https://www.torproject.org/download/download "https://www.torproject.org/download/download")

Changes in version 0.2.1.28 - 2010-12-17  
 **Major bugfixes:**

-   Fix a remotely exploitable bug that could be used to crash instances of Tor remotely by overflowing on the heap. Remote-code execution hasn't been confirmed, but can't be ruled out. Everyone should upgrade. Bugfix on the 0.1.1 series and later.

**Directory authority changes:**

-   Change IP address and ports for gabelmoo (v3 directory authority).

**Minor features:** [**read more »**](https://blog.torproject.org/blog/tor-02128-released-security-patches)
