---
layout: post
title: "Tor Project infrastructure updates"
permalink: tor-project-infrastructure-updates
date: 2010-01-22 10:51:45
author: phobos
category: blog
status: closed
tags: ["alpha release", "security updates", "stable release", "tor"]
---

You should upgrade to Tor 0.2.1.22 or 0.2.2.7-alpha:  
 [https://www.torproject.org/easy-download.html.en](https://www.torproject.org/easy-download.html.en "https://www.torproject.org/easy-download.html.en")

In early January we discovered that two of the seven servers that run directory  
 authorities were compromised (moria1 and gabelmoo), along with  
 metrics.torproject.org, a new server we'd recently set up to serve  
 metrics data and graphs. The three servers have since been reinstalled  
 with service migrated to other servers.

We made fresh identity keys for the two directory authorities, which is  
 why you need to upgrade.

Moria also hosted our git repository and svn repository. We took the  
 services offline as soon as we learned of the breach. It appears the  
 attackers didn't realize what they broke into -- just that they had  
 found some servers with lots of bandwidth. The attackers set up some ssh  
 keys and proceeded to use the three servers for launching other attacks.  
 We've done some preliminary comparisons, and it looks like git and svn  
 were not touched in any way. [**read more »**](https://blog.torproject.org/blog/tor-project-infrastructure-updates)
