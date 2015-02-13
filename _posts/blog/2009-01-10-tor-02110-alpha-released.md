---
layout: post
title: "Tor 0.2.1.10-alpha released"
permalink: tor-02110-alpha-released
date: 2009-01-10 14:07:09
author: phobos
category: blog
status: closed
tags: ["alpha release", "bug fixes", "code refactoring", "documentation"]
---

Tor 0.2.1.10-alpha fixes two major bugs in bridge relays (one that would  
 make the bridge relay not so useful if it had DirPort set to 0, and one  
 that could let an attacker learn a little bit of information about the  
 bridge's users), and a bug that would cause your Tor relay to ignore a  
 circuit create request it can't decrypt (rather than reply with an error).  
 It also fixes a wide variety of other bugs.

[https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

Changes in version 0.2.1.10-alpha - 2009-01-06  
 **Major bugfixes:** [**read more »**](https://blog.torproject.org/blog/tor-0.2.1.10-alpha-released)

-   If the cached networkstatus consensus is more than five days old,  
     discard it rather than trying to use it. In theory it could  
     be useful because it lists alternate directory mirrors, but in  
     practice it just means we spend many minutes trying directory  
     mirrors that are long gone from the network. Helps bug 887 a bit;  
     bugfix on 0.2.0.x.
-   Bridge relays that had DirPort set to 0 would stop fetching  
     descriptors shortly after startup, and then briefly resume  
     after a new bandwidth test and/or after publishing a new bridge  
     descriptor. Bridge users that try to bootstrap from them would  
     get a recent networkstatus but would get descriptors from up to  
     18 hours earlier, meaning most of the descriptors were obsolete  
     already. Reported by Tas; bugfix on 0.2.0.13-alpha.
-   Prevent bridge relays from serving their 'extrainfo' document  
     to anybody who asks, now that extrainfo docs include potentially  
     sensitive aggregated client geoip summaries. Bugfix on  
     0.2.0.13-alpha.

