---
layout: post
title: "Tor 0.2.2.18-alpha available"
permalink: tor-02218-alpha-available
date: 2010-11-17
author: phobos
category: blog
tags: ["alpha release", "bug fixes", "feature enhancements"]
---

Tor 0.2.2.18-alpha fixes several crash bugs that have been nagging us lately, makes unpublished bridge relays able to detect their IP address, and fixes a wide variety of other bugs to get us much closer to a stable release.

[https://www.torproject.org/download/download](https://www.torproject.org/download/download "https://www.torproject.org/download/download")

Packages will be appearing over the next few days. The original version of this announcement is at [http://archives.seul.org/or/talk/Nov-2010/msg00082.html](http://archives.seul.org/or/talk/Nov-2010/msg00082.html "http://archives.seul.org/or/talk/Nov-2010/msg00082.html").

Changes in version 0.2.2.18-alpha - 2010-11-16  
 o Major bugfixes:  
 - Do even more to reject (and not just ignore) annotations on  
 router descriptors received anywhere but from the cache. Previously  
 we would ignore such annotations at first, but cache them to disk  
 anyway. Bugfix on 0.2.0.8-alpha. Found by piebeer.  
 - Do not log messages to the controller while shrinking buffer  
 freelists. Doing so would sometimes make the controller connection  
 try to allocate a buffer chunk, which would mess up the internals  
 of the freelist and cause an assertion failure. Fixes bug 1125;  
 fixed by Robert Ransom. Bugfix on 0.2.0.16-alpha.  
 - Learn our external IP address when we're a relay or bridge, even if  
 we set PublishServerDescriptor to 0. Bugfix on 0.2.0.3-alpha,  
 where we introduced bridge relays that don't need to publish to  
 be useful. Fixes bug 2050.  
 - Maintain separate TLS contexts and certificates for incoming and  
 outgoing connections in bridge relays. Previously we would use the  
 same TLS contexts and certs for incoming and outgoing connections.  
 Bugfix on 0.2.0.3-alpha; addresses bug 988.  
 - Maintain separate identity keys for incoming and outgoing TLS  
 contexts in bridge relays. Previously we would use the same  
 identity keys for incoming and outgoing TLS contexts. Bugfix on  
 0.2.0.3-alpha; addresses the other half of bug 988.  
 - Avoid an assertion failure when we as an authority receive a  
 duplicate upload of a router descriptor that we already have,  
 but which we previously considered an obsolete descriptor.  
 Fixes another case of bug 1776. Bugfix on 0.2.2.16-alpha.  
 - Avoid a crash bug triggered by looking at a dangling pointer while  
 setting the network status consensus. Found by Robert Ransom.  
 Bugfix on 0.2.2.17-alpha. Fixes bug 2097.  
 - Fix a logic error where servers that \_didn't\_ act as exits would  
 try to keep their server lists more aggressively up to date than  
 exits, when it was supposed to be the other way around. Bugfix  
 on 0.2.2.17-alpha.

o Minor bugfixes (on Tor 0.2.1.x and earlier):  
 - When we're trying to guess whether we know our IP address as  
 a relay, we would log various ways that we failed to guess  
 our address, but never log that we ended up guessing it  
 successfully. Now add a log line to help confused and anxious  
 relay operators. Bugfix on 0.1.2.1-alpha; fixes bug 1534.  
 - Bring the logic that gathers routerinfos and assesses the  
 acceptability of circuits into line. This prevents a Tor OP from  
 getting locked in a cycle of choosing its local OR as an exit for a  
 path (due to a .exit request) and then rejecting the circuit because  
 its OR is not listed yet. It also prevents Tor clients from using an  
 OR running in the same instance as an exit (due to a .exit request)  
 if the OR does not meet the same requirements expected of an OR  
 running elsewhere. Fixes bug 1859; bugfix on 0.1.0.1-rc.  
 - Correctly describe errors that occur when generating a TLS object.  
 Previously we would attribute them to a failure while generating a  
 TLS context. Patch by Robert Ransom. Bugfix on 0.1.0.4-rc; fixes  
 bug 1994.  
 - Enforce multiplicity rules when parsing annotations. Bugfix on  
 0.2.0.8-alpha. Found by piebeer.  
 - Fix warnings that newer versions of autoconf produced during  
 ./autogen.sh. These warnings appear to be harmless in our case,  
 but they were extremely verbose. Fixes bug 2020.

o Minor bugfixes (on Tor 0.2.2.x):  
 - Enable protection of small arrays whenever we build with gcc  
 hardening features, not only when also building with warnings  
 enabled. Fixes bug 2031; bugfix on 0.2.2.14-alpha. Reported by keb.

o Minor features:  
 - Make hidden services work better in private Tor networks by not  
 requiring any uptime to join the hidden service descriptor  
 DHT. Implements ticket 2088.  
 - Rate-limit the "your application is giving Tor only an IP address"  
 warning. Addresses bug 2000; bugfix on 0.0.8pre2.  
 - When AllowSingleHopExits is set, print a warning to explain to the  
 relay operator why most clients are avoiding her relay.  
 - Update to the November 1 2010 Maxmind GeoLite Country database.

o Code simplifications and refactoring:  
 - When we fixed bug 1038 we had to put in a restriction not to send  
 RELAY\_EARLY cells on rend circuits. This was necessary as long  
 as relays using Tor 0.2.1.3-alpha through 0.2.1.18-alpha were  
 active. Now remove this obsolete check. Resolves bug 2081.  
 - Some options used different conventions for uppercasing of acronyms  
 when comparing manpage and source. Fix those in favor of the  
 manpage, as it makes sense to capitalize acronyms.  
 - Remove the torrc.complete file. It hasn't been kept up to date  
 and users will have better luck checking out the manpage.  
 - Remove the obsolete "NoPublish" option; it has been flagged  
 as obsolete and has produced a warning since 0.1.1.18-rc.  
 - Remove everything related to building the expert bundle for OS X.  
 It has confused many users, doesn't work right on OS X 10.6,  
 and is hard to get rid of once installed. Resolves bug 1274.

