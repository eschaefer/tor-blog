---
layout: post
title: "Tor 0.2.1.16-rc Release Candidate now available"
permalink: tor-02116rc-release-candidate-now-available
date: 2009-06-24 09:32:45
author: phobos
category: blog
status: closed
tags: ["bug fixes", "hidden service fixes", "release candidate", "security fixes"]
---

Tor 0.2.1.16-rc speeds up performance for fast exit relays, and fixes  
 a bunch of minor bugs.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

Changes in version 0.2.1.16-rc - 2009-06-20  
 **Security fixes:**

-   Fix an edge case where a malicious exit relay could convince a  
     controller that the client's DNS question resolves to an internal IP  
     address. Bug found and fixed by "optimist"; bugfix on 0.1.2.8-beta.

**Major performance improvements (on 0.2.0.x):**

-   Disable and refactor some debugging checks that forced a linear scan  
     over the whole server-side DNS cache. These accounted for over 50%  
     of CPU time on a relatively busy exit node's gprof profile. Found  
     by Jacob.
-   Disable some debugging checks that appeared in exit node profile  
     data.

**Minor features:** [**read more »**](https://blog.torproject.org/blog/tor-02116rc-release-candidate-now-available)

Update to the "June 3 2009" ip-to-country file.
