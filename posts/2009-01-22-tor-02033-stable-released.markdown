---
layout: post
title: "Tor 0.2.0.33-stable released"
permalink: tor-02033-stable-released
date: 01/22/2009
author: phobos
category: blog
tags: ["bug fixes", "security fixes", "stable release"]
---

Tor 0.2.0.33 fixes a variety of bugs that were making relays less useful  
to users. It also finally fixes a bug where a relay or client that's  
been off for many days would take a long time to bootstrap.

This update also fixes an important security-related bug reported by  
Ilja van Sprundel. You should upgrade. (We'll send out more details  
about the bug once people have had some time to upgrade.)

[https://www.torproject.org/download.html](https://www.torproject.org/download.html "https://www.torproject.org/download.html")

Changes in version 0.2.0.33 - 2009-01-21  
**Security fixes:**

- Fix a heap-corruption bug that may be remotely triggerable on  
 some platforms. Reported by Ilja van Sprundel.

**Major bugfixes:**

- When a stream at an exit relay is in state "resolving" or  
 "connecting" and it receives an "end" relay cell, the exit relay  
 would silently ignore the end cell and not close the stream. If  
 the client never closes the circuit, then the exit relay never  
 closes the TCP connection. Bug introduced in Tor 0.1.2.1-alpha;  
 reported by "wood".
- When sending CREATED cells back for a given circuit, use a 64-bit  
 connection ID to find the right connection, rather than an addr:port  
 combination. Now that we can have multiple OR connections between  
 the same ORs, it is no longer possible to use addr:port to uniquely  
 identify a connection.
- Bridge relays that had DirPort set to 0 would stop fetching  
 descriptors shortly after startup, and then briefly resume  
 after a new bandwidth test and/or after publishing a new bridge  
 descriptor. Bridge users that try to bootstrap from them would  
 get a recent networkstatus but would get descriptors from up to  
 18 hours earlier, meaning most of the descriptors were obsolete  
 already. Reported by Tas; bugfix on 0.2.0.13-alpha.
- Prevent bridge relays from serving their 'extrainfo' document  
 to anybody who asks, now that extrainfo docs include potentially  
 sensitive aggregated client geoip summaries. Bugfix on  
 0.2.0.13-alpha.
- If the cached networkstatus consensus is more than five days old,  
 discard it rather than trying to use it. In theory it could be  
 useful because it lists alternate directory mirrors, but in practice  
 it just means we spend many minutes trying directory mirrors that  
 are long gone from the network. Also discard router descriptors as  
 we load them if they are more than five days old, since the onion  
 key is probably wrong by now. Bugfix on 0.2.0.x. Fixes bug 887.

**Minor bugfixes:**

- Do not mark smartlist\_bsearch\_idx() function as ATTR\_PURE. This bug  
 could make gcc generate non-functional binary search code. Bugfix  
 on 0.2.0.10-alpha.
- Build correctly on platforms without socklen\_t.
- Compile without warnings on solaris.
- Avoid potential crash on internal error during signature collection.  
 Fixes bug 864. Patch from rovv.
- Correct handling of possible malformed authority signing key  
 certificates with internal signature types. Fixes bug 880.  
 Bugfix on 0.2.0.3-alpha.
- Fix a hard-to-trigger resource leak when logging credential status.  
 CID 349.
- When we can't initialize DNS because the network is down, do not  
 automatically stop Tor from starting. Instead, we retry failed  
 dns\_inits() every 10 minutes, and change the exit policy to reject  
 \*:\* until one succeeds. Fixes bug 691.
- Use 64 bits instead of 32 bits for connection identifiers used with  
 the controller protocol, to greatly reduce risk of identifier reuse.
- When we're choosing an exit node for a circuit, and we have  
 no pending streams, choose a good general exit rather than one that  
 supports "all the pending streams". Bugfix on 0.1.1.x. Fix by rovv.
- Fix another case of assuming, when a specific exit is requested,  
 that we know more than the user about what hosts it allows.  
 Fixes one case of bug 752. Patch from rovv.
- Clip the MaxCircuitDirtiness config option to a minimum of 10  
 seconds. Warn the user if lower values are given in the  
 configuration. Bugfix on 0.1.0.1-rc. Patch by Sebastian.
- Clip the CircuitBuildTimeout to a minimum of 30 seconds. Warn the  
 user if lower values are given in the configuration. Bugfix on  
 0.1.1.17-rc. Patch by Sebastian.
- Fix a memory leak when we decline to add a v2 rendezvous descriptor to  
 the cache because we already had a v0 descriptor with the same ID.  
 Bugfix on 0.2.0.18-alpha.
- Fix a race condition when freeing keys shared between main thread  
 and CPU workers that could result in a memory leak. Bugfix on  
 0.1.0.1-rc. Fixes bug 889.
- Send a valid END cell back when a client tries to connect to a  
 nonexistent hidden service port. Bugfix on 0.1.2.15. Fixes bug  
 840. Patch from rovv.
- Check which hops rendezvous stream cells are associated with to  
 prevent possible guess-the-streamid injection attacks from  
 intermediate hops. Fixes another case of bug 446. Based on patch  
 from rovv.
- If a broken client asks a non-exit router to connect somewhere,  
 do not even do the DNS lookup before rejecting the connection.  
 Fixes another case of bug 619. Patch from rovv.
- When a relay gets a create cell it can't decrypt (e.g. because it's  
 using the wrong onion key), we were dropping it and letting the  
 client time out. Now actually answer with a destroy cell. Fixes  
 bug 904. Bugfix on 0.0.2pre8.

**Minor bugfixes (hidden services):**

- Do not throw away existing introduction points on SIGHUP. Bugfix on  
 0.0.6pre1. Patch by Karsten. Fixes bug 874.

**Minor features:**

- Report the case where all signatures in a detached set are rejected  
 differently than the case where there is an error handling the  
 detached set.
- When we realize that another process has modified our cached  
 descriptors, print out a more useful error message rather than  
 triggering an assertion. Fixes bug 885. Patch from Karsten.
- Implement the 0x20 hack to better resist DNS poisoning: set the  
 case on outgoing DNS requests randomly, and reject responses that do  
 not match the case correctly. This logic can be disabled with the  
 ServerDNSRamdomizeCase setting, if you are using one of the 0.3%  
 of servers that do not reliably preserve case in replies. See  
 "Increased DNS Forgery Resistance through 0x20-Bit Encoding"  
 for more info.
- Check DNS replies for more matching fields to better resist DNS  
 poisoning.
- Never use OpenSSL compression: it wastes RAM and CPU trying to  
 compress cells, which are basically all encrypted, compressed, or  
 both.

The original announcement can be found at [http://archives.seul.org/or/announce/Jan-2009/msg00000.html](http://archives.seul.org/or/announce/Jan-2009/msg00000.html "http://archives.seul.org/or/announce/Jan-2009/msg00000.html")

