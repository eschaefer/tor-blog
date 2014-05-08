---
layout: post
title: "Tor 0.2.1.26-stable released"
permalink: tor-02126-stable-released
date: 06/10/2010
author: phobos
category: blog
tags: ["connection overload", "stable release", "test suite fixes", "v3 directories"]
---

Tor 0.2.1.26 addresses the recent connection and memory overload problems we've been seeing on relays, especially relays with their DirPort open. If your relay has been crashing, or you turned it off because it used too many resources, give this release a try.

This release also fixes yet another instance of broken OpenSSL libraries that was causing some relays to drop out of the consensus.

Available for download at [https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

Changes in version 0.2.1.26  
**Major bugfixes:**

- Teach relays to defend themselves from connection overload. Relays  
 now close idle circuits early if it looks like they were intended  
 for directory fetches. Relays are also more aggressive about closing  
 TLS connections that have no circuits on them. Such circuits are  
 unlikely to be re-used, and tens of thousands of them were piling  
 up at the fast relays, causing the relays to run out of sockets  
 and memory. Bugfix on 0.2.0.22-rc (where clients started tunneling  
 their directory fetches over TLS).
- Fix SSL renegotiation behavior on OpenSSL versions like on Centos  
 that claim to be earlier than 0.9.8m, but which have in reality  
 backported huge swaths of 0.9.8m or 0.9.8n renegotiation  
 behavior. Possible fix for some cases of bug 1346.
- Directory mirrors were fetching relay descriptors only from v2  
 directory authorities, rather than v3 authorities like they should.  
 Only 2 v2 authorities remain (compared to 7 v3 authorities), leading  
 to a serious bottleneck. Bugfix on 0.2.0.9-alpha. Fixes bug 1324.

**Minor bugfixes:**

- Finally get rid of the deprecated and now harmful notion of "clique  
 mode", where directory authorities maintain TLS connections to  
 every other relay.

**Testsuite fixes:**

- In the util/threads test, no longer free the test\_mutex before all  
 worker threads have finished. Bugfix on 0.2.1.6-alpha.
- The master thread could starve the worker threads quite badly on  
 certain systems, causing them to run only partially in the allowed  
 window. This resulted in test failures. Now the master thread sleeps  
 occasionally for a few microseconds while the two worker-threads  
 compete for the mutex. Bugfix on 0.2.0.1-alpha.

