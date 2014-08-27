---
layout: post
title: "Tor 0.2.2.7-alpha released"
permalink: tor-0227-alpha-released
date: 2010-01-23
author: phobos
category: blog
tags: ["bug fixes", "deprecated features", "feature enhancements", "performance enhancements", "security critical", "security fixes"]
---

alpha fixes a huge client-side performance bug, as well  
as laying the groundwork for further relay-side performance fixes. It  
also starts cleaning up client behavior with respect to the EntryNodes,  
ExitNodes, and StrictNodes config options.

This release also rotates two directory authority keys, due to a security  
breach of some of the Torproject servers:  
 [http://archives.seul.org/or/talk/Jan-2010/msg00161.html](http://archives.seul.org/or/talk/Jan-2010/msg00161.html "http://archives.seul.org/or/talk/Jan-2010/msg00161.html")

Everybody should upgrade:  
 [https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

Changes in version 0.2.2.7-alpha - 2010-01-19  
 o Directory authority changes:  
 - Rotate keys (both v3 identity and relay identity) for moria1  
 and gabelmoo.

o Major features (performance):  
 - We were selecting our guards uniformly at random, and then weighting  
 which of our guards we'd use uniformly at random. This imbalance  
 meant that Tor clients were severely limited on throughput (and  
 probably latency too) by the first hop in their circuit. Now we  
 select guards weighted by currently advertised bandwidth. We also  
 automatically discard guards picked using the old algorithm. Fixes  
 bug 1217; bugfix on 0.2.1.3-alpha. Found by Mike Perry.  
 - When choosing which cells to relay first, relays can now favor  
 circuits that have been quiet recently, to provide lower latency  
 for low-volume circuits. By default, relays enable or disable this  
 feature based on a setting in the consensus. You can override  
 this default by using the new "CircuitPriorityHalflife" config  
 option. Design and code by Ian Goldberg, Can Tang, and Chris  
 Alexander.  
 - Add separate per-conn write limiting to go with the per-conn read  
 limiting. We added a global write limit in Tor 0.1.2.5-alpha,  
 but never per-conn write limits.  
 - New consensus params "bwconnrate" and "bwconnburst" to let us  
 rate-limit client connections as they enter the network. It's  
 controlled in the consensus so we can turn it on and off for  
 experiments. It's starting out off. Based on proposal 163.

o Major features (relay selection options):  
 - Switch to a StrictNodes config option, rather than the previous  
 "StrictEntryNodes" / "StrictExitNodes" separation that was missing a  
 "StrictExcludeNodes" option.  
 - If EntryNodes, ExitNodes, ExcludeNodes, or ExcludeExitNodes  
 change during a config reload, mark and discard all our origin  
 circuits. This fix should address edge cases where we change the  
 config options and but then choose a circuit that we created before  
 the change.  
 - If EntryNodes or ExitNodes are set, be more willing to use an  
 unsuitable (e.g. slow or unstable) circuit. The user asked for it,  
 they get it.  
 - Make EntryNodes config option much more aggressive even when  
 StrictNodes is not set. Before it would prepend your requested  
 entrynodes to your list of guard nodes, but feel free to use others  
 after that. Now it chooses only from your EntryNodes if any of  
 those are available, and only falls back to others if a) they're  
 all down and b) StrictNodes is not set.  
 - Now we refresh your entry guards from EntryNodes at each consensus  
 fetch -- rather than just at startup and then they slowly rot as  
 the network changes.

o Major bugfixes:  
 - Stop bridge directory authorities from answering dbg-stability.txt  
 directory queries, which would let people fetch a list of all  
 bridge identities they track. Bugfix on 0.2.1.6-alpha.

o Minor features:  
 - Log a notice when we get a new control connection. Now it's easier  
 for security-conscious users to recognize when a local application  
 is knocking on their controller door. Suggested by bug 1196.  
 - New config option "CircuitStreamTimeout" to override our internal  
 timeout schedule for how many seconds until we detach a stream from  
 a circuit and try a new circuit. If your network is particularly  
 slow, you might want to set this to a number like 60.  
 - New controller command "getinfo config-text". It returns the  
 contents that Tor would write if you send it a SAVECONF command,  
 so the controller can write the file to disk itself.  
 - New options for SafeLogging to allow scrubbing only log messages  
 generated while acting as a relay.  
 - Ship the bridges spec file in the tarball too.  
 - Avoid a mad rush at the beginning of each month when each client  
 rotates half of its guards. Instead we spread the rotation out  
 throughout the month, but we still avoid leaving a precise timestamp  
 in the state file about when we first picked the guard. Improves  
 over the behavior introduced in 0.1.2.17.

o Minor bugfixes (compiling):  
 - Fix compilation on OS X 10.3, which has a stub mlockall() but  
 hides it. Bugfix on 0.2.2.6-alpha.  
 - Fix compilation on Solaris by removing support for the  
 DisableAllSwap config option. Solaris doesn't have an rlimit for  
 mlockall, so we cannot use it safely. Fixes bug 1198; bugfix on  
 0.2.2.6-alpha.

o Minor bugfixes (crashes):  
 - Do not segfault when writing buffer stats when we haven't observed  
 a single circuit to report about. Found by Fabian Lanze. Bugfix on  
 0.2.2.1-alpha.  
 - If we're in the pathological case where there's no exit bandwidth  
 but there is non-exit bandwidth, or no guard bandwidth but there  
 is non-guard bandwidth, don't crash during path selection. Bugfix  
 on 0.2.0.3-alpha.  
 - Fix an impossible-to-actually-trigger buffer overflow in relay  
 descriptor generation. Bugfix on 0.1.0.15.

o Minor bugfixes (privacy):  
 - Fix an instance where a Tor directory mirror might accidentally  
 log the IP address of a misbehaving Tor client. Bugfix on  
 0.1.0.1-rc.  
 - Don't list Windows capabilities in relay descriptors. We never made  
 use of them, and maybe it's a bad idea to publish them. Bugfix  
 on 0.1.1.8-alpha.

o Minor bugfixes (other):  
 - Resolve an edge case in path weighting that could make us misweight  
 our relay selection. Fixes bug 1203; bugfix on 0.0.8rc1.  
 - Fix statistics on client numbers by country as seen by bridges that  
 were broken in 0.2.2.1-alpha. Also switch to reporting full 24-hour  
 intervals instead of variable 12-to-48-hour intervals.  
 - After we free an internal connection structure, overwrite it  
 with a different memory value than we use for overwriting a freed  
 internal circuit structure. Should help with debugging. Suggested  
 by bug 1055.  
 - Update our OpenSSL 0.9.8l fix so that it works with OpenSSL 0.9.8m  
 too.

o Removed features:  
 - Remove the HSAuthorityRecordStats option that version 0 hidden  
 service authorities could have used to track statistics of overall  
 hidden service usage.

