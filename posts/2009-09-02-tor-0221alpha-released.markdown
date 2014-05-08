---
layout: post
title: "Tor 0.2.2.1-alpha released"
permalink: tor-0221alpha-released
date: 09/02/2009
author: phobos
category: blog
tags: ["alpha release", "anonymity fixes", "bug fixes", "improvements", "os x", "packages", "safe statistic collection", "security fixes", "vidalia bundle"]
---

Tor 0.2.2.1-alpha disables ".exit" address notation by default, allows  
Tor clients to bootstrap on networks where only port 80 is reachable,  
makes it more straightforward to support hardware crypto accelerators,  
and starts the groundwork for gathering stats safely at relays.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

We've been improving our packages and bundles:  
**Packaging changes:**

- Upgrade Vidalia from 0.1.15 to 0.2.3 in the Windows and OS X  
 installer bundles. See  
 [https://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.2.3/CHAN...](https://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.2.3/CHANGELOG "https://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.2.3/CHANGELOG")  
 for details of what's new in Vidalia 0.2.3.
- Windows Vidalia Bundle: update Privoxy from 3.0.6 to 3.0.14-beta.
- OS X Vidalia Bundle: move to Polipo 1.0.4 with Tor specific  
 configuration file, rather than the old Privoxy.
- OS X Vidalia Bundle: Vidalia, Tor, and Polipo are compiled as  
 x86-only for better compatibility with OS X 10.6, aka Snow Leopard.
- OS X Tor Expert Bundle: Tor is compiled as x86-only for  
 better compatibility with OS X 10.6, aka Snow Leopard.
- OS X Vidalia Bundle: The multi-package installer is now replaced  
 by a simple drag and drop to the /Applications folder. This change  
 occurred with the upgrade to Vidalia 0.2.3.

Changes in version 0.2.2.1-alpha - 2009-08-26  
**Security fixes:**

- Start the process of disabling ".exit" address notation, since it  
 can be used for a variety of esoteric application-level attacks  
 on users. To reenable it, set "AllowDotExit 1" in your torrc. Fix  
 on 0.0.9rc5.

**New directory authorities:**

- Set up urras (run by Jacob Appelbaum) as the seventh v3 directory  
 authority.

**Major features:**

- New AccelName and AccelDir options add support for dynamic OpenSSL  
 hardware crypto acceleration engines.
- Tor now supports tunneling all of its outgoing connections over  
 a SOCKS proxy, using the SOCKS4Proxy and/or SOCKS5Proxy  
 configuration options. Code by Christopher Davis.

**Major bugfixes:**

- Send circuit or stream sendme cells when our window has decreased  
 by 100 cells, not when it has decreased by 101 cells. Bug uncovered  
 by Karsten when testing the "reduce circuit window" performance  
 patch. Bugfix on the 54th commit on Tor -- from July 2002,  
 before the release of Tor 0.0.0. This is the new winner of the  
 oldest-bug prize.

**New options for gathering stats safely:**

- Directories that set "DirReqStatistics 1" write statistics on  
 directory request to disk every 24 hours. As compared to the  
 --enable-geoip-stats flag in 0.2.1.x, there are a few improvements:  
 1) stats are written to disk exactly every 24 hours; 2) estimated  
 shares of v2 and v3 requests are determined as mean values, not at  
 the end of a measurement period; 3) unresolved requests are listed  
 with country code '??'; 4) directories also measure download times.
- Exit nodes that set "ExitPortStatistics 1" write statistics on the  
 number of exit streams and transferred bytes per port to disk every  
 24 hours.
- Relays that set "CellStatistics 1" write statistics on how long  
 cells spend in their circuit queues to disk every 24 hours.
- Entry nodes that set "EntryStatistics 1" write statistics on the  
 rough number and origins of connecting clients to disk every 24  
 hours.
- Relays that write any of the above statistics to disk and set  
 "ExtraInfoStatistics 1" include the past 24 hours of statistics in  
 their extra-info documents.

**Minor features:**

- New --digests command-line switch to output the digests of the  
 source files Tor was built with.
- The "torify" script now uses torsocks where available.
- The memarea code now uses a sentinel value at the end of each area  
 to make sure nothing writes beyond the end of an area. This might  
 help debug some conceivable causes of bug 930.
- Time and memory units in the configuration file can now be set to  
 fractional units. For example, "2.5 GB" is now a valid value for  
 AccountingMax.
- Certain Tor clients (such as those behind check.torproject.org) may  
 want to fetch the consensus in an extra early manner. To enable this  
 a user may now set FetchDirInfoExtraEarly to 1. This also depends on  
 setting FetchDirInfoEarly to 1. Previous behavior will stay the same  
 as only certain clients who must have this information sooner should  
 set this option.
- Instead of adding the svn revision to the Tor version string, report  
 the git commit (when we're building from a git checkout).

**Minor bugfixes:**

- If any the v3 certs we download are unparseable, we should actually  
 notice the failure so we don't retry indefinitely. Bugfix on  
 0.2.0.x; reported by "rotator".
- If the cached cert file is unparseable, warn but don't exit.
- Fix possible segmentation fault on directory authorities. Bugfix on  
 0.2.1.14-rc.
- When Tor fails to parse a descriptor of any kind, dump it to disk.  
 Might help diagnosing bug 1051.

**Deprecated and removed features:**

- The controller no longer accepts the old obsolete "addr-mappings/"  
 or "unregistered-servers-" GETINFO values.
- Hidden services no longer publish version 0 descriptors, and clients  
 do not request or use version 0 descriptors. However, the old hidden  
 service authorities still accept and serve version 0 descriptors  
 when contacted by older hidden services/clients.
- The EXTENDED\_EVENTS and VERBOSE\_NAMES controller features are now  
 always on; using them is necessary for correct forward-compatible  
 controllers.
- Remove support for .noconnect style addresses. Nobody was using  
 them, and they provided another avenue for detecting Tor users  
 via application-level web tricks.

