---
layout: post
title: "Tor 0.2.2.34 is released (security patches)"
permalink: tor-02234-released-security-patches
date: 2011-10-27 19:24:40
author: erinn
category: blog
status: closed
tags: ["security advisory", "security fixes", "tor", "tor stable"]
---

**Tor 0.2.2.34 fixes a critical anonymity vulnerability where an attacker  
 can deanonymize Tor users. Everybody should upgrade.**

The attack relies on four components:

-   1) Clients reuse their TLS cert when talking to different relays, so relays can recognize a user by the identity key in her cert.
-   2) An attacker who knows the client's identity key can probe each guard relay to see if that identity key is connected to that guard relay right now.
-   3) A variety of active attacks in the literature (starting from "Low-Cost Traffic Analysis of Tor" by Murdoch and Danezis in 2005) allow a malicious website to discover the guard relays that a Tor user visiting the website is using.
-   4) Clients typically pick three guards at random, so the set of guards for a given user could well be a unique fingerprint for her. This release fixes components \#1 and \#2, which is enough to block the attack; the other two remain as open research problems.

Special thanks to "frosty\_un" for reporting the issue to us! (As far as we know, this has nothing to do with any claimed attack currently getting attention in the media.)

**Clients should upgrade so they are no longer recognizable by the TLS certs they present. Relays should upgrade so they no longer allow a remote attacker to probe them to test whether unpatched clients are currently connected to them.**

This release also fixes several vulnerabilities that allow an attacker to enumerate bridge relays. Some bridge enumeration attacks still remain; see for example proposal 188.

[https://torproject.org/download/download-easy](https://torproject.org/download/download-easy "https://torproject.org/download/download-easy")

Changes in version 0.2.2.34 - 2011-10-26

**Privacy/anonymity fixes (clients):**

-   Clients and bridges no longer send TLS certificate chains on outgoing OR  
     connections. Previously, each client or bridge would use the same cert chain  
     for all outgoing OR connections until its IP address changes, which allowed any  
     relay that the client or bridge contacted to determine which entry guards it is  
     using. Fixes CVE-2011-2768. Bugfix on 0.0.9pre5; found by "frosty\_un".
-   If a relay receives a CREATE\_FAST cell on a TLS connection, it no longer  
     considers that connection as suitable for satisfying a circuit EXTEND request.  
     Now relays can protect clients from the CVE-2011-2768 issue even if the clients  
     haven't upgraded yet.
-   Directory authorities no longer assign the Guard flag to relays that  
     haven't upgraded to the above "refuse EXTEND requests to client connections"  
     fix. Now directory authorities can protect clients from the CVE-2011-2768 issue  
     even if neither the clients nor the relays have upgraded yet. There's a new  
     "GiveGuardFlagTo\_CVE\_2011\_2768\_VulnerableRelays" config option to let us  
     transition smoothly, else tomorrow there would be no guard relays.

**Privacy/anonymity fixes (bridge enumeration):**

-   Bridge relays now do their directory fetches inside Tor TLS connections,  
     like all the other clients do, rather than connecting directly to the DirPort  
     like public relays do. Removes another avenue for enumerating bridges. Fixes  
     bug 4115; bugfix on 0.2.0.35.
-   Bridges relays now build circuits for themselves in a more similar way to  
     how clients build them. Removes another avenue for enumerating bridges. Fixes  
     bug 4124; bugfix on 0.2.0.3-alpha, when bridges were introduced.
-   Bridges now refuse CREATE or CREATE\_FAST cells on OR connections that they  
     initiated. Relays could distinguish incoming bridge connections from client  
     connections, creating another avenue for enumerating bridges. Fixes  
     CVE-2011-2769. Bugfix on 0.2.0.3-alpha. Found by "frosty\_un".

**Major bugfixes:**

-   Fix a crash bug when changing node restrictions while a DNS lookup is  
     in-progress. Fixes bug 4259; bugfix on 0.2.2.25-alpha. Bugfix by "Tey'".
-   Don't launch a useless circuit after failing to use one of a hidden  
     service's introduction points. Previously, we would launch a new introduction  
     circuit, but not set the hidden service which that circuit was intended to  
     connect to, so it would never actually be used. A different piece of code would  
     then create a new introduction circuit correctly. Bug reported by katmagic and  
     found by Sebastian Hahn. Bugfix on 0.2.1.13-alpha; fixes bug 4212.

**Minor bugfixes:**

-   Change an integer overflow check in the OpenBSD\_Malloc code so that GCC is  
     less likely to eliminate it as impossible. Patch from Mansour Moufid. Fixes bug  
     4059.
-   When a hidden service turns an extra service-side introduction circuit into  
     a general-purpose circuit, free the rend\_data and intro\_key fields first, so we  
     won't leak memory if the circuit is cannibalized for use as another  
     service-side introduction circuit. Bugfix on 0.2.1.7-alpha; fixes bug  
     4251.
-   Bridges now skip DNS self-tests, to act a little more stealthily. Fixes  
     bug 4201; bugfix on 0.2.0.3-alpha, which first introduced bridges. Patch by  
     "warms0x".
-   Fix internal bug-checking logic that was supposed to catch failures in  
     digest generation so that it will fail more robustly if we ask for a  
     nonexistent algorithm. Found by Coverity Scan. Bugfix on 0.2.2.1-alpha; fixes  
     Coverity CID 479.
-   Report any failure in init\_keys() calls launched because our IP address has  
     changed. Spotted by Coverity Scan. Bugfix on 0.1.1.4-alpha; fixes CID 484.

**Minor bugfixes (log messages and documentation):**

-   Remove a confusing dollar sign from the example fingerprint in the man  
     page, and also make the example fingerprint a valid one. Fixes bug 4309; bugfix  
     on 0.2.1.3-alpha.
-   The next version of Windows will be called Windows 8, and it has a major  
     version of 6, minor version of 2. Correctly identify that version instead of  
     calling it "Very recent version". Resolves ticket 4153; reported by  
     funkstar.
-   Downgrade log messages about circuit timeout calibration from "notice" to  
     "info": they don't require or suggest any human intervention. Patch from Tom  
     Lowenthal. Fixes bug 4063; bugfix on 0.2.2.14-alpha.

**Minor features:**

-   Turn on directory request statistics by default and include them in  
     extra-info descriptors. Don't break if we have no GeoIP database. Backported  
     from 0.2.3.1-alpha; implements ticket 3951.
-   Update to the October 4 2011 Maxmind GeoLite Country database.

