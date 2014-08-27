---
layout: post
title: "Tor 0.2.2.15-alpha released"
permalink: tor-02215-alpha-released
date: 2010-08-23
author: erinn
category: blog
tags: ["alpha releases", "hidden services", "memory leaks", "performance improvements", "tor"]
---

Tor 0.2.2.15-alpha fixes a big bug in hidden service availability, fixes a variety of other bugs that were preventing performance experiments from moving forward, fixes several bothersome memory leaks, and generally closes a lot of smaller bugs that have been filling up trac lately.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

[Changes in version 0.2.2.15-alpha - 2010-08-18](https://gitweb.torproject.org/tor.git/blob_plain/eba3f37f17a2af4ff628dd5cbc653441e6dce6eb:/ChangeLog)  
 o Major bugfixes:  
 - Stop assigning the HSDir flag to relays that disable their  
 DirPort (and thus will refuse to answer directory requests). This  
 fix should dramatically improve the reachability of hidden services:  
 hidden services and hidden service clients pick six HSDir relays  
 to store and retrieve the hidden service descriptor, and currently  
 about half of the HSDir relays will refuse to work. Bugfix on  
 0.2.0.10-alpha; fixes part of bug 1693.  
 - The PerConnBWRate and Burst config options, along with the  
 bwconnrate and bwconnburst consensus params, initialized each conn's  
 token bucket values only when the connection is established. Now we  
 update them if the config options change, and update them every time  
 we get a new consensus. Otherwise we can encounter an ugly edge  
 case where we initialize an OR conn to client-level bandwidth,  
 but then later the relay joins the consensus and we leave it  
 throttled. Bugfix on 0.2.2.7-alpha; fixes bug 1830.  
 - Fix a regression that caused Tor to rebind its ports if it receives  
 SIGHUP while hibernating. Bugfix in 0.1.1.6-alpha; closes bug 919.

o Major features:  
 - Lower the maximum weighted-fractional-uptime cutoff to 98%. This  
 should give us approximately 40-50% more Guard-flagged nodes,  
 improving the anonymity the Tor network can provide and also  
 decreasing the dropoff in throughput that relays experience when  
 they first get the Guard flag.  
 - Allow enabling or disabling the \*Statistics config options while  
 Tor is running.

o Minor features:  
 - Update to the August 1 2010 Maxmind GeoLite Country database.  
 - Have the controller interface give a more useful message than  
 "Internal Error" in response to failed GETINFO requests.  
 - Warn when the same option is provided more than once in a torrc  
 file, on the command line, or in a single SETCONF statement, and  
 the option is one that only accepts a single line. Closes bug 1384.  
 - Build correctly on mingw with more recent versions of OpenSSL 0.9.8.  
 Patch from mingw-san.  
 - Add support for the country code "{??}" in torrc options like  
 ExcludeNodes, to indicate all routers of unknown country. Closes  
 bug 1094.  
 - Relays report the number of bytes spent on answering directory  
 requests in extra-info descriptors similar to {read,write}-history.  
 Implements enhancement 1790.

o Minor bugfixes (on 0.2.1.x and earlier):  
 - Complain if PublishServerDescriptor is given multiple arguments that  
 include 0 or 1. This configuration will be rejected in the future.  
 Bugfix on 0.2.0.1-alpha; closes bug 1107.  
 - Disallow BridgeRelay 1 and ORPort 0 at once in the configuration.  
 Bugfix on 0.2.0.13-alpha; closes bug 928.  
 - Change "Application request when we're believed to be offline."  
 notice to "Application request when we haven't used client  
 functionality lately.", to clarify that it's not an error. Bugfix  
 on 0.0.9.3; fixes bug 1222.  
 - Fix a bug in the controller interface where "GETINFO ns/asdaskljkl"  
 would return "551 Internal error" rather than "552 Unrecognized key  
 ns/asdaskljkl". Bugfix on 0.1.2.3-alpha.  
 - Users can't configure a regular relay to be their bridge. It didn't  
 work because when Tor fetched the bridge descriptor, it found  
 that it already had it, and didn't realize that the purpose of the  
 descriptor had changed. Now we replace routers with a purpose other  
 than bridge with bridge descriptors when fetching them. Bugfix on  
 0.1.1.9-alpha. Bug 1776 not yet fixed because now we immediately  
 refetch the descriptor with router purpose 'general', disabling  
 it as a bridge.  
 - Fix a rare bug in rend\_fn unit tests: we would fail a test when  
 a randomly generated port is 0. Diagnosed by Matt Edman. Bugfix  
 on 0.2.0.10-alpha; fixes bug 1808.  
 - Exit nodes didn't recognize EHOSTUNREACH as a plausible error code,  
 and so sent back END\_STREAM\_REASON\_MISC. Clients now recognize a new  
 stream ending reason for this case: END\_STREAM\_REASON\_NOROUTE.  
 Servers can start sending this code when enough clients recognize  
 it. Also update the spec to reflect this new reason. Bugfix on  
 0.1.0.1-rc; fixes part of bug 1793.  
 - Delay geoip stats collection by bridges for 6 hours, not 2 hours,  
 when we switch from being a public relay to a bridge. Otherwise  
 there will still be clients that see the relay in their consensus,  
 and the stats will end up wrong. Bugfix on 0.2.1.15-rc; fixes bug  
 932 even more.  
 - Instead of giving an assertion failure on an internal mismatch  
 on estimated freelist size, just log a BUG warning and try later.  
 Mitigates but does not fix bug 1125.  
 - Fix an assertion failure that could occur in caches or bridge users  
 when using a very short voting interval on a testing network.  
 Diagnosed by Robert Hogan. Fixes bug 1141; bugfix on 0.2.0.8-alpha.

o Minor bugfixes (on 0.2.2.x):  
 - Alter directory authorities to always consider Exit-flagged nodes  
 as potential Guard nodes in their votes. The actual decision to  
 use Exits as Guards is done in the consensus bandwidth weights.  
 Fixes bug 1294; bugfix on 0.2.2.10-alpha.  
 - When the controller is reporting the purpose of circuits that  
 didn't finish building before the circuit build timeout, it was  
 printing UNKNOWN\_13. Now print EXPIRED. Bugfix on 0.2.2.14-alpha.  
 - Our libevent version parsing code couldn't handle versions like  
 1.4.14b-stable and incorrectly warned the user about using an  
 old and broken version of libevent. Treat 1.4.14b-stable like  
 1.4.14-stable when parsing the version. Fixes bug 1731; bugfix  
 on 0.2.2.1-alpha.  
 - Don't use substitution references like $(VAR:MOD) when  
 $(asciidoc\_files) is empty -- make(1) on NetBSD transforms  
 '$(:x)' to 'x' rather than the empty string. This bites us in  
 doc/ when configured with --disable-asciidoc. Bugfix on  
 0.2.2.9-alpha; fixes bug 1773.  
 - Remove a spurious hidden service server-side log notice about  
 "Ancient non-dirty circuits". Bugfix on 0.2.2.14-alpha; fixes  
 bug 1741.  
 - Fix compilation with --with-dmalloc set. Bugfix on 0.2.2.6-alpha;  
 fixes bug 1832.  
 - Correctly report written bytes on linked connections. Found while  
 implementing 1790. Bugfix on 0.2.2.4-alpha.  
 - Fix three memory leaks: one in circuit\_build\_times\_parse\_state(),  
 one in dirvote\_add\_signatures\_to\_pending\_consensus(), and one every  
 time we parse a v3 network consensus. Bugfixes on 0.2.2.14-alpha,  
 0.2.2.6-alpha, and 0.2.2.10-alpha respectively; fixes bug 1831.

o Code simplifications and refactoring:  
 - Take a first step towards making or.h smaller by splitting out  
 function definitions for all source files in src/or/. Leave  
 structures and defines in or.h for now.  
 - Remove a bunch of unused function declarations as well as a block of  
 #if 0'd code from the unit tests. Closes bug 1824.  
 - New unit tests for exit-port history statistics; refactored exit  
 statistics code to be more easily tested.  
 - Remove the old debian/ directory from the main Tor distribution.  
 The official Tor-for-debian git repository lives at the URL  
 [https://git.torproject.org/debian/tor.git](https://git.torproject.org/debian/tor.git "https://git.torproject.org/debian/tor.git")

