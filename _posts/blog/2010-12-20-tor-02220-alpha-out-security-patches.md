---
layout: post
title: "Tor 0.2.2.20-alpha is out (security patches)"
permalink: tor-02220-alpha-out-security-patches
date: 2010-12-20 11:10:39
author: phobos
category: blog
status: closed
tags: ["bug fixes", "enhancements", "security advisory"]
---

Tor 0.2.2.20-alpha does some code cleanup to reduce the risk of remotely  
 exploitable bugs. Thanks to Willem Pinckaers for notifying us of the  
 issue. The Common Vulnerabilities and Exposures project has assigned  
 CVE-2010-1676 to this issue.

We also fix a variety of other significant bugs, change the IP address  
 for one of our directory authorities, and update the minimum version  
 that Tor relays must run to join the network.

All Tor users should upgrade.

[https://www.torproject.org/download/download](https://www.torproject.org/download/download "https://www.torproject.org/download/download")

Changes in version 0.2.2.20-alpha - 2010-12-17  
 **Major bugfixes:** [**read more »**](https://blog.torproject.org/blog/tor-02220-alpha-out-security-patches)

Fix a remotely exploitable bug that could be used to crash instances  
 of Tor remotely by overflowing on the heap. Remote-code execution  
 hasn't been confirmed, but can't be ruled out. Everyone should  
 upgrade. Bugfix on the 0.1.1 series and later.

Fix a bug that could break accounting on 64-bit systems with large  

