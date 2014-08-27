---
layout: post
title: "Tor 0.2.2.20-alpha is out (security patches)"
permalink: tor-02220-alpha-out-security-patches
date: 2010-12-20
author: phobos
category: blog
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
**Major bugfixes:**

- Fix a remotely exploitable bug that could be used to crash instances  
 of Tor remotely by overflowing on the heap. Remote-code execution  
 hasn't been confirmed, but can't be ruled out. Everyone should  
 upgrade. Bugfix on the 0.1.1 series and later.
- Fix a bug that could break accounting on 64-bit systems with large  
 time\_t values, making them hibernate for impossibly long intervals.  
 Fixes bug 2146. Bugfix on 0.0.9pre6; fix by boboper.
- Fix a logic error in directory\_fetches\_from\_authorities() that  
 would cause all \_non\_-exits refusing single-hop-like circuits  
 to fetch from authorities, when we wanted to have \_exits\_ fetch  
 from authorities. Fixes more of 2097. Bugfix on 0.2.2.16-alpha;  
 fix by boboper.
- Fix a stream fairness bug that would cause newer streams on a given  
 circuit to get preference when reading bytes from the origin or  
 destination. Fixes bug 2210. Fix by Mashael AlSabah. This bug was  
 introduced before the first Tor release, in svn revision r152.

**Directory authority changes:**

- Change IP address and ports for gabelmoo (v3 directory authority).

**Minor bugfixes:**

- Avoid crashes when AccountingMax is set on clients. Fixes bug 2235.  
 Bugfix on 0.2.2.18-alpha. Diagnosed by boboper.
- Fix an off-by-one error in calculating some controller command  
 argument lengths. Fortunately, this mistake is harmless since  
 the controller code does redundant NUL termination too. Found by  
 boboper. Bugfix on 0.1.1.1-alpha.
- Do not dereference NULL if a bridge fails to build its  
 extra-info descriptor. Found by an anonymous commenter on  
 Trac. Bugfix on 0.2.2.19-alpha.

**Minor features:**

- Update to the December 1 2010 Maxmind GeoLite Country database.
- Directory authorities now reject relays running any versions of  
 Tor between 0.2.1.3-alpha and 0.2.1.18 inclusive; they have  
 known bugs that keep RELAY\_EARLY cells from working on rendezvous  
 circuits. Followup to fix for bug 2081.
- Directory authorities now reject relays running any version of Tor  
 older than 0.2.0.26-rc. That version is the earliest that fetches  
 current directory information correctly. Fixes bug 2156.
- Report only the top 10 ports in exit-port stats in order not to  
 exceed the maximum extra-info descriptor length of 50 KB. Implements  
 task 2196.

