---
layout: post
title: "Tor 0.2.2.35 is released (security patches)"
permalink: tor-02235-released-security-patches
date: 2011-12-16 13:51:02
author: erinn
category: blog
status: closed
tags: ["bugfixes", "end of life", "security critical", "security fixes", "stable releases", "tor"]
---

**Tor 0.2.2.35 fixes a critical heap-overflow security issue in Tor's  
 buffers code. Absolutely everybody should upgrade.**

The bug relied on an incorrect calculation when making data continuous  
 in one of our IO buffers, if the first chunk of the buffer was  
 misaligned by just the wrong amount. The miscalculation would allow an  
 attacker to overflow a piece of heap-allocated memory. To mount this  
 attack, the attacker would need to either open a SOCKS connection to  
 Tor's SocksPort (usually restricted to localhost), or target a Tor  
 instance configured to make its connections through a SOCKS proxy  
 (which Tor does not do by default).

Good security practice requires that all heap-overflow bugs should be  
 presumed to be exploitable until proven otherwise, so we are treating  
 this as a potential code execution attack. Please upgrade immediately!  
 This bug does not affect bufferevents-based builds of Tor. Special  
 thanks to "Vektor" for reporting this issue to us!

Tor 0.2.2.35 also fixes several bugs in previous versions, including  
 crash bugs for unusual configurations, and a long-term bug that  
 would prevent Tor from starting on Windows machines with draconian  
 AV software.

With this release, we remind everyone that 0.2.0.x has reached its  
 formal end-of-life. Those Tor versions have many known flaws, and  
 nobody should be using them. You should upgrade -- ideally to the  
 0.2.2.x series. If you're using a Linux or BSD and its packages are  
 obsolete, stop using those packages and upgrade anyway.

The Tor 0.2.1.x series is also approaching its end-of-life: it will no  
 longer receive support after some time in early 2012.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Changes in version 0.2.2.35 - 2011-12-16**

**Major bugfixes:**

-   Fix a heap overflow bug that could occur when trying to pull  
     data into the first chunk of a buffer, when that chunk had  
     already had some data drained from it. Fixes CVE-2011-2778;  
     bugfix on 0.2.0.16-alpha. Reported by "Vektor".
-   Initialize Libevent with the EVENT\_BASE\_FLAG\_NOLOCK flag enabled, so  
     that it doesn't attempt to allocate a socketpair. This could cause  
     some problems on Windows systems with overzealous firewalls. Fix for  
     bug 4457; workaround for Libevent versions 2.0.1-alpha through  
     2.0.15-stable.
-   If we mark an OR connection for close based on a cell we process,  
     don't process any further cells on it. We already avoid further  
     reads on marked-for-close connections, but now we also discard the  
     cells we'd already read. Fixes bug 4299; bugfix on 0.2.0.10-alpha,  
     which was the first version where we might mark a connection for  
     close based on processing a cell on it.
-   Correctly sanity-check that we don't underflow on a memory  
     allocation (and then assert) for hidden service introduction  
     point decryption. Bug discovered by Dan Rosenberg. Fixes bug 4410;  
     bugfix on 0.2.1.5-alpha.
-   Fix a memory leak when we check whether a hidden service  
     descriptor has any usable introduction points left. Fixes bug  
     4424. Bugfix on 0.2.2.25-alpha.
-   Don't crash when we're running as a relay and don't have a GeoIP  
     file. Bugfix on 0.2.2.34; fixes bug 4340. This backports a fix  
     we've had in the 0.2.3.x branch already.
-   When running as a client, do not print a misleading (and plain  
     wrong) log message that we're collecting "directory request"  
     statistics: clients don't collect statistics. Also don't create a  
     useless (because empty) stats file in the stats/ directory. Fixes  
     bug 4353; bugfix on 0.2.2.34.

**Minor bugfixes:**

-   Detect failure to initialize Libevent. This fix provides better  
     detection for future instances of bug 4457.
-   Avoid frequent calls to the fairly expensive cull\_wedged\_cpuworkers  
     function. This was eating up hideously large amounts of time on some  
     busy servers. Fixes bug 4518; bugfix on 0.0.9.8.
-   Resolve an integer overflow bug in smartlist\_ensure\_capacity().  
     Fixes bug 4230; bugfix on Tor 0.1.0.1-rc. Based on a patch by  
     Mansour Moufid.
-   Don't warn about unused log\_mutex in log.c when building with  
     --disable-threads using a recent GCC. Fixes bug 4437; bugfix on  
     0.1.0.6-rc which introduced --disable-threads.
-   When configuring, starting, or stopping an NT service, stop  
     immediately after the service configuration attempt has succeeded  
     or failed. Fixes bug 3963; bugfix on 0.2.0.7-alpha.
-   When sending a NETINFO cell, include the original address  
     received for the other side, not its canonical address. Found  
     by "troll\_un"; fixes bug 4349; bugfix on 0.2.0.10-alpha.
-   Fix a typo in a hibernation-related log message. Fixes bug 4331;  
     bugfix on 0.2.2.23-alpha; found by "tmpname0901".
-   Fix a memory leak in launch\_direct\_bridge\_descriptor\_fetch() that  
     occurred when a client tried to fetch a descriptor for a bridge  
     in ExcludeNodes. Fixes bug 4383; bugfix on 0.2.2.25-alpha.
-   Backport fixes for a pair of compilation warnings on Windows.  
     Fixes bug 4521; bugfix on 0.2.2.28-beta and on 0.2.2.29-beta.
-   If we had ever tried to call tor\_addr\_to\_str on an address of  
     unknown type, we would have done a strdup on an uninitialized  
     buffer. Now we won't. Fixes bug 4529; bugfix on 0.2.1.3-alpha.  
     Reported by "troll\_un".
-   Correctly detect and handle transient lookup failures from  
     tor\_addr\_lookup. Fixes bug 4530; bugfix on 0.2.1.5-alpha.  
     Reported by "troll\_un".
-   Fix null-pointer access that could occur if TLS allocation failed.  
     Fixes bug 4531; bugfix on 0.2.0.20-rc. Found by "troll\_un".
-   Use tor\_socket\_t type for listener argument to accept(). Fixes bug  
     4535; bugfix on 0.2.2.28-beta. Found by "troll\_un".

**Minor features:**

-   Add two new config options for directory authorities:  
     AuthDirFastGuarantee sets a bandwidth threshold for guaranteeing the  
     Fast flag, and AuthDirGuardBWGuarantee sets a bandwidth threshold  
     that is always sufficient to satisfy the bandwidth requirement for  
     the Guard flag. Now it will be easier for researchers to simulate  
     Tor networks with different values. Resolves ticket 4484.
-   When Tor ignores a hidden service specified in its configuration,  
     include the hidden service's directory in the warning message.  
     Previously, we would only tell the user that some hidden service  
     was ignored. Bugfix on 0.0.6; fixes bug 4426.
-   Update to the December 6 2011 Maxmind GeoLite Country database.

**Packaging changes:**

-   Make it easier to automate expert package builds on Windows,  
     by removing an absolute path from makensis.exe command.

