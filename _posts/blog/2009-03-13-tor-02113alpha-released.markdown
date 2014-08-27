---
layout: post
title: "Tor 0.2.1.13-alpha released"
permalink: tor-02113alpha-released
date: 2009-03-13
author: phobos
category: blog
tags: ["alpha release", "bug fixes", "security fixes"]
---

Tor 0.2.1.13-alpha includes another big pile of minor bugfixes and  
cleanups. We're finally getting close to a release candidate.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

Changes in version 0.2.1.13-alpha - 2009-03-09  
**Major bugfixes:**

- Correctly update the list of which countries we exclude as  
 exits, when the GeoIP file is loaded or reloaded. Diagnosed by  
 lark. Bugfix on 0.2.1.6-alpha.

**Minor bugfixes (on 0.2.0.x and earlier):**

- Automatically detect MacOSX versions earlier than 10.4.0, and  
 disable kqueue from inside Tor when running with these versions.  
 We previously did this from the startup script, but that was no  
 help to people who didn't use the startup script. Resolves bug 863.
- When we had picked an exit node for a connection, but marked it as  
 "optional", and it turned out we had no onion key for the exit,  
 stop wanting that exit and try again. This situation may not  
 be possible now, but will probably become feasible with proposal  
 158. Spotted by rovv. Fixes another case of bug 752.
- Clients no longer cache certificates for authorities they do not  
 recognize. Bugfix on 0.2.0.9-alpha.
- When we can't transmit a DNS request due to a network error, retry  
 it after a while, and eventually transmit a failing response to  
 the RESOLVED cell. Bugfix on 0.1.2.5-alpha.
- If the controller claimed responsibility for a stream, but that  
 stream never finished making its connection, it would live  
 forever in circuit\_wait state. Now we close it after SocksTimeout  
 seconds. Bugfix on 0.1.2.7-alpha; reported by Mike Perry.
- Drop begin cells to a hidden service if they come from the middle  
 of a circuit. Patch from lark.
- When we erroneously receive two EXTEND cells for the same circuit  
 ID on the same connection, drop the second. Patch from lark.
- Fix a crash that occurs on exit nodes when a nameserver request  
 timed out. Bugfix on 0.1.2.1-alpha; our CLEAR debugging code had  
 been suppressing the bug since 0.1.2.10-alpha. Partial fix for  
 bug 929.
- Do not assume that a stack-allocated character array will be  
 64-bit aligned on platforms that demand that uint64\_t access is  
 aligned. Possible fix for bug 604.
- Parse dates and IPv4 addresses in a locale- and libc-independent  
 manner, to avoid platform-dependent behavior on malformed input.
- Build correctly when configured to build outside the main source  
 path. Patch from Michael Gold.
- We were already rejecting relay begin cells with destination port  
 of 0. Now also reject extend cells with destination port or address  
 of 0. Suggested by lark.

**Minor bugfixes (on 0.2.1.x):**

- Don't re-extend introduction circuits if we ran out of RELAY\_EARLY  
 cells. Bugfix on 0.2.1.3-alpha. Fixes more of bug 878.
- If we're an exit node, scrub the IP address to which we are exiting  
 in the logs. Bugfix on 0.2.1.8-alpha.

**Minor features:**

- On Linux, use the prctl call to re-enable core dumps when the user  
 is option is set.
- New controller event NEWCONSENSUS that lists the networkstatus  
 lines for every recommended relay. Now controllers like Torflow  
can keep up-to-date on which relays they should be using.
- Update to the "February 26 2009" ip-to-country file.

The original notice can be found at [http://archives.seul.org/or/talk/Mar-2009/msg00047.html](http://archives.seul.org/or/talk/Mar-2009/msg00047.html "http://archives.seul.org/or/talk/Mar-2009/msg00047.html")

