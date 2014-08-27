---
layout: post
title: "Tor Project infrastructure updates"
permalink: tor-project-infrastructure-updates
date: 2010-01-22
author: phobos
category: blog
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
were not touched in any way.

We've been very lucky the past few years regarding security. It still  
seems this breach is unrelated to Tor itself. To be clear, it doesn't  
seem that anyone specifically attacked our servers to get at Tor. It  
seems we were attacked for the cpu capacity and bandwidth of the servers,  
and the servers just happened to also carry out functions for Tor.

We've tried to address the most common questions below.

**I read that Tor's encryption keys were compromised, is this true?**

No. The operating systems were compromised, not tor. The tor source, and running Tor Directory Authorities were left untouched. It appears the  
attackers didn't realize what they broke into -- just that they had  
found some servers with lots of bandwidth. We've generated new Directory Authority keys out of an abundance of caution.

**Does this mean someone could have matched users up to their  
destinations?**

No. By design, Tor requires a majority of directory authorities (four  
in this case) to generate a consensus; and like other relays in the  
Tor network, directory authorities don't know enough to match a user  
and traffic or destination.

**Does this mean somebody could have changed the Tor source?**

No, we've checked the source. It does mean you should upgrade so your  
client knows about all the currently valid directory authorities.

** Does this mean someone could have learned more about Tor than an  
ordinary user?**

Since our software and specifications are open, everyone already has  
access to almost everything on these machines... except some old bridge  
descriptors, which we give out only in small batches as entry points for  
blocked clients.

**Can I trust Tor's security?**

We've taken steps to fix the weaknesses identified and to harden our  
systems further. Tor has a track record of openness and transparency,  
with its source code and specifications and also with its operations.  
Moreover, we're disclosing breaches such as this so you can monitor our  
status. You shouldn't assume those who don't disclose security breaches  
never have any!

