---
layout: post
title: "Tor 0.2.2.11-alpha and 0.2.2.12-alpha are out"
permalink: tor-02211-alpha-and-02212-alpha-are-out
date: 2010-04-24
author: phobos
category: blog
tags: ["alpha releases", "bug fixes", "performance improvements"]
---

Tor 0.2.2.12-alpha fixes a critical bug in how directory authorities  
handle and vote on descriptors. It was causing relays to drop out of  
the consensus.

Tor 0.2.2.11-alpha fixes yet another instance of broken OpenSSL libraries  
that was causing some relays to drop out of the consensus.

(Windows bundles will be available whenever Andrew gets around to making  
them; we're trying to stick to a policy of announcing alphas on time  
rather than waiting for every package.)

[https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

Original announcement is at [http://archives.seul.org/or/talk/Apr-2010/msg00174.html](http://archives.seul.org/or/talk/Apr-2010/msg00174.html "http://archives.seul.org/or/talk/Apr-2010/msg00174.html")

Changes in version 0.2.2.12-alpha - 2010-04-20  
 o Major bugfixes:  
 - Many relays have been falling out of the consensus lately because  
 not enough authorities know about their descriptor for them to get  
 a majority of votes. When we deprecated the v2 directory protocol,  
 we got rid of the only way that v3 authorities can hear from each  
 other about other descriptors. Now authorities examine every v3  
 vote for new descriptors, and fetch them from that authority. Bugfix  
 on 0.2.1.23.  
 - Fix two typos in tor\_vasprintf() that broke the compile on Windows,  
 and a warning in or.h related to bandwidth\_weight\_rule\_t that  
 prevented clean compile on OS X. Fixes bug 1363; bugfix on  
 0.2.2.11-alpha.  
 - Fix a segfault on relays when DirReqStatistics is enabled  
 and 24 hours pass. Bug found by keb. Fixes bug 1365; bugfix on  
 0.2.2.11-alpha.

o Minor bugfixes:  
 - Demote a confusing TLS warning that relay operators might get when  
 someone tries to talk to their OrPort. It is neither the operator's  
 fault nor can they do anything about it. Fixes bug 1364; bugfix  
 on 0.2.0.14-alpha.

Changes in version 0.2.2.11-alpha - 2010-04-15  
 o Major bugfixes:  
 - Directory mirrors were fetching relay descriptors only from v2  
 directory authorities, rather than v3 authorities like they should.  
 Only 2 v2 authorities remain (compared to 7 v3 authorities), leading  
 to a serious bottleneck. Bugfix on 0.2.0.9-alpha. Fixes bug 1324.  
 - Fix a parsing error that made every possible value of  
 CircPriorityHalflifeMsec get treated as "1 msec". Bugfix  
 on 0.2.2.7-alpha. Rename CircPriorityHalflifeMsec to  
 CircuitPriorityHalflifeMsec, so authorities can tell newer relays  
 about the option without breaking older ones.  
 - Fix SSL renegotiation behavior on OpenSSL versions like on Centos  
 that claim to be earlier than 0.9.8m, but which have in reality  
 backported huge swaths of 0.9.8m or 0.9.8n renegotiation  
 behavior. Possible fix for some cases of bug 1346.

o Minor features:  
 - Experiment with a more aggressive approach to preventing clients  
 from making one-hop exit streams. Exit relays who want to try it  
 out can set "RefuseUnknownExits 1" in their torrc, and then look  
 for "Attempt by %s to open a stream" log messages. Let us know  
 how it goes!  
 - Add support for statically linking zlib by specifying  
 --enable-static-zlib, to go with our support for statically linking  
 openssl and libevent. Resolves bug 1358.

o Minor bugfixes:  
 - Fix a segfault that happens whenever a Tor client that is using  
 libevent2's bufferevents gets a hup signal. Bugfix on 0.2.2.5-alpha;  
 fixes bug 1341.  
 - When we cleaned up the contrib/tor-exit-notice.html file, we left  
 out the first line. Fixes bug 1295.  
 - When building the manpage from a tarball, we required asciidoc, but  
 the asciidoc -> roff/html conversion was already done for the  
 tarball. Make 'make' complain only when we need asciidoc (either  
 because we're compiling directly from git, or because we altered  
 the asciidoc manpage in the tarball). Bugfix on 0.2.2.9-alpha.  
 - When none of the directory authorities vote on any params, Tor  
 segfaulted when trying to make the consensus from the votes. We  
 didn't trigger the bug in practice, because authorities do include  
 params in their votes. Bugfix on 0.2.2.10-alpha; fixes bug 1322.

o Testsuite fixes:  
 - In the util/threads test, no longer free the test\_mutex before all  
 worker threads have finished. Bugfix on 0.2.1.6-alpha.  
 - The master thread could starve the worker threads quite badly on  
 certain systems, causing them to run only partially in the allowed  
 window. This resulted in test failures. Now the master thread sleeps  
 occasionally for a few microseconds while the two worker-threads  
 compete for the mutex. Bugfix on 0.2.0.1-alpha.

