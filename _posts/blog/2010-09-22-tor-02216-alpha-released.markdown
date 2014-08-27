---
layout: post
title: "Tor 0.2.2.16-alpha released"
permalink: tor-02216-alpha-released
date: 2010-09-22
author: phobos
category: blog
tags: ["alpha release", "enhancements"]
---

Tor 0.2.2.16-alpha fixes a variety of old stream fairness bugs (most  
evident at exit relays), and also continues to resolve all the little  
bugs that have been filling up the bug tracker lately.

[https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

Packages will be appearing over the next few days or weeks (except  
on Windows, which apparently doesn't build -- stay tuned for an  
0.2.2.17-alpha in that case).

Changes in version 0.2.2.16-alpha - 2010-09-17  
 o Major bugfixes (stream-level fairness):  
 - When receiving a circuit-level SENDME for a blocked circuit, try  
 to package cells fairly from all the streams that had previously  
 been blocked on that circuit. Previously, we had started with the  
 oldest stream, and allowed each stream to potentially exhaust  
 the circuit's package window. This gave older streams on any  
 given circuit priority over newer ones. Fixes bug 1937. Detected  
 originally by Camilo Viecco. This bug was introduced before the  
 first Tor release, in svn commit r152: it is the new winner of  
 the longest-lived bug prize.  
 - When the exit relay got a circuit-level sendme cell, it started  
 reading on the exit streams, even if had 500 cells queued in the  
 circuit queue already, so the circuit queue just grew and grew in  
 some cases. We fix this by not re-enabling reading on receipt of a  
 sendme cell when the cell queue is blocked. Fixes bug 1653. Bugfix  
 on 0.2.0.1-alpha. Detected by Mashael AlSabah. Original patch by  
 "yetonetime".  
 - Newly created streams were allowed to read cells onto circuits,  
 even if the circuit's cell queue was blocked and waiting to drain.  
 This created potential unfairness, as older streams would be  
 blocked, but newer streams would gladly fill the queue completely.  
 We add code to detect this situation and prevent any stream from  
 getting more than one free cell. Bugfix on 0.2.0.1-alpha. Partially  
 fixes bug 1298.

o Minor features:  
 - Update to the September 1 2010 Maxmind GeoLite Country database.  
 - Warn when CookieAuthFileGroupReadable is set but CookieAuthFile is  
 not. This would lead to a cookie that is still not group readable.  
 Closes bug 1843. Suggested by katmagic.  
 - When logging a rate-limited warning, we now mention how many messages  
 got suppressed since the last warning.  
 - Add new "perconnbwrate" and "perconnbwburst" consensus params to  
 do individual connection-level rate limiting of clients. The torrc  
 config options with the same names trump the consensus params, if  
 both are present. Replaces the old "bwconnrate" and "bwconnburst"  
 consensus params which were broken from 0.2.2.7-alpha through  
 0.2.2.14-alpha. Closes bug 1947.  
 - When a router changes IP address or port, authorities now launch  
 a new reachability test for it. Implements ticket 1899.  
 - Make the formerly ugly "2 unknown, 7 missing key, 0 good, 0 bad,  
 2 no signature, 4 required" messages about consensus signatures  
 easier to read, and make sure they get logged at the same severity  
 as the messages explaining which keys are which. Fixes bug 1290.  
 - Don't warn when we have a consensus that we can't verify because  
 of missing certificates, unless those certificates are ones  
 that we have been trying and failing to download. Fixes bug 1145.  
 - If you configure your bridge with a known identity fingerprint,  
 and the bridge authority is unreachable (as it is in at least  
 one country now), fall back to directly requesting the descriptor  
 from the bridge. Finishes the feature started in 0.2.0.10-alpha;  
 closes bug 1138.  
 - When building with --enable-gcc-warnings on OpenBSD, disable  
 warnings in system headers. This makes --enable-gcc-warnings  
 pass on OpenBSD 4.8.

o Minor bugfixes (on 0.2.1.x and earlier):  
 - Authorities will now attempt to download consensuses if their  
 own efforts to make a live consensus have failed. This change  
 means authorities that restart will fetch a valid consensus, and  
 it means authorities that didn't agree with the current consensus  
 will still fetch and serve it if it has enough signatures. Bugfix  
 on 0.2.0.9-alpha; fixes bug 1300.  
 - Ensure DNS requests launched by "RESOLVE" commands from the  
 controller respect the \_\_LeaveStreamsUnattached setconf options. The  
 same goes for requests launched via DNSPort or transparent  
 proxying. Bugfix on 0.2.0.1-alpha; fixes bug 1525.  
 - Allow handshaking OR connections to take a full KeepalivePeriod  
 seconds to handshake. Previously, we would close them after  
 IDLE\_OR\_CONN\_TIMEOUT (180) seconds, the same timeout as if they  
 were open. Bugfix on 0.2.1.26; fixes bug 1840. Thanks to mingw-san  
 for analysis help.  
 - Rate-limit "Failed to hand off onionskin" warnings.  
 - Never relay a cell for a circuit we have already destroyed.  
 Between marking a circuit as closeable and finally closing it,  
 it may have been possible for a few queued cells to get relayed,  
 even though they would have been immediately dropped by the next  
 OR in the circuit. Fixes bug 1184; bugfix on 0.2.0.1-alpha.  
 - Never queue a cell for a circuit that's already been marked  
 for close.  
 - Never vote for a server as "Running" if we have a descriptor for  
 it claiming to be hibernating, and that descriptor was published  
 more recently than our last contact with the server. Bugfix on  
 0.2.0.3-alpha; fixes bug 911.  
 - Squash a compile warning on OpenBSD. Reported by Tas; fixes  
 bug 1848.

o Minor bugfixes (on 0.2.2.x):  
 - Fix a regression introduced in 0.2.2.7-alpha that marked relays  
 down if a directory fetch fails and you've configured either  
 bridges or EntryNodes. The intent was to mark the relay as down  
 \_unless\_ you're using bridges or EntryNodes, since if you are  
 then you could quickly run out of entry points.  
 - Fix the Windows directory-listing code. A bug introduced in  
 0.2.2.14-alpha could make Windows directory servers forget to load  
 some of their cached v2 networkstatus files.  
 - Really allow clients to use relays as bridges. Fixes bug 1776;  
 bugfix on 0.2.2.15-alpha.  
 - Demote a warn to info that happens when the CellStatistics option  
 was just enabled. Bugfix on 0.2.2.15-alpha; fixes bug 1921.  
 Reported by Moritz Bartl.  
 - On Windows, build correctly either with or without Unicode support.  
 This is necessary so that Tor can support fringe platforms like  
 Windows 98 (which has no Unicode), or Windows CE (which has no  
 non-Unicode). Bugfix on 0.2.2.14-alpha; fixes bug 1797.

o Testing  
 - Add a unit test for cross-platform directory-listing code.

The original announcement is [http://archives.seul.org/or/talk/Sep-2010/msg00108.html](http://archives.seul.org/or/talk/Sep-2010/msg00108.html "http://archives.seul.org/or/talk/Sep-2010/msg00108.html")

