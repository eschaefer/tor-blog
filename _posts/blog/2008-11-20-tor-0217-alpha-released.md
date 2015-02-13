---
layout: post
title: "Tor 0.2.1.7-alpha released"
permalink: tor-0217-alpha-released
date: 2008-11-20 19:09:13
author: phobos
category: blog
status: closed
tags: ["alpha release", "bugfix", "bugs"]
---

Tor 0.2.1.7-alpha fixes a major security problem in Debian and Ubuntu  
 packages (and maybe other packages) noticed by Theo de Raadt, fixes  
 a smaller security flaw that might allow an attacker to access local  
 services, adds better defense against DNS poisoning attacks on exit  
 relays, further improves hidden service performance, and fixes a variety  
 of other issues.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

Changes in version 0.2.1.7-alpha - 2008-11-08

**Security fixes:** [**read more »**](https://blog.torproject.org/blog/tor-0.2.1.7-alpha-released)

-   The "ClientDNSRejectInternalAddresses" config option wasn't being  
     consistently obeyed: if an exit relay refuses a stream because its  
     exit policy doesn't allow it, we would remember what IP address  
     the relay said the destination address resolves to, even if it's  
     an internal IP address. Bugfix on 0.2.0.7-alpha; patch by rovv.
-   The "User" and "Group" config options did not clear the  
     supplementary group entries for the Tor process. The "User" option  
     is now more robust, and we now set the groups to the specified  
     user's primary group. The "Group" option is now ignored. For more  
     detailed logging on credential switching, set CREDENTIAL\_LOG\_LEVEL  
     in common/compat.c to LOG\_NOTICE or higher. Patch by Jacob Appelbaum  
     and Steven Murdoch. Bugfix on 0.0.2pre14. Fixes bug 848.
-   Do not use or believe expired v3 authority certificates. Patch  
     from Karsten. Bugfix in 0.2.0.x. Fixes bug 851.

