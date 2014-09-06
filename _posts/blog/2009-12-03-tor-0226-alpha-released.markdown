---
layout: post
title: "Tor 0.2.2.6-alpha released"
permalink: blog/tor-0226-alpha-released
date: 2009-12-03
author: phobos
category: blog
tags: ["alpha release", "android", "enhancements", "new features", "openssl"]
---

On November 19, we released the latest in the Tor alpha series, version 0.2.2.6-alpha. This release lays the groundwork for many upcoming features:
support for the new lower-footprint "microdescriptor" directory design,
future-proofing our consensus format against new hash functions or
other changes, and an Android port. It also makes Tor compatible with
the upcoming OpenSSL 0.9.8l release, and fixes a variety of bugs.

It can be downloaded at [https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

**Major features:**

- Directory authorities can now create, vote on, and serve multiple
 parallel formats of directory data as part of their voting process.
 Partially implements Proposal 162: "Publish the consensus in
 multiple flavors".
- Directory authorities can now agree on and publish small summaries
 of router information that clients can use in place of regular
 server descriptors. This transition will eventually allow clients
 to use far less bandwidth for downloading information about the
 network. Begins the implementation of Proposal 158: "Clients
 download consensus + microdescriptors".
- The directory voting system is now extensible to use multiple hash
 algorithms for signatures and resource selection. Newer formats
 are signed with SHA256, with a possibility for moving to a better
 hash algorithm in the future.
- New DisableAllSwap option. If set to 1, Tor will attempt to lock all
 current and future memory pages via mlockall(). On supported
 platforms (modern Linux and probably BSD but not Windows or OS X),
 this should effectively disable any and all attempts to page out
 memory. This option requires that you start your Tor as root --
 if you use DisableAllSwap, please consider using the User option
 to properly reduce the privileges of your Tor.
- Numerous changes, bugfixes, and workarounds from Nathan Freitas
 to help Tor build correctly for Android phones.

**Major bugfixes:**

- Work around a security feature in OpenSSL 0.9.8l that prevents our
 handshake from working unless we explicitly tell OpenSSL that we
 are using SSL renegotiation safely. We are, but OpenSSL 0.9.8l
 won't work unless we say we are.

**Minor bugfixes:**

- Fix a crash bug when trying to initialize the evdns module in
 Libevent 2. Bugfix on 0.2.1.16-rc.
- Stop logging at severity 'warn' when some other Tor client tries
 to establish a circuit with us using weak DH keys. It's a protocol
 violation, but that doesn't mean ordinary users need to hear about
 it. Fixes the bug part of bug 1114. Bugfix on 0.1.0.13.
- Do not refuse to learn about authority certs and v2 networkstatus
 documents that are older than the latest consensus. This bug might
 have degraded client bootstrapping. Bugfix on 0.2.0.10-alpha.
 Spotted and fixed by xmux.
- Fix numerous small code-flaws found by Coverity Scan Rung 3.
- If all authorities restart at once right before a consensus vote,
 nobody will vote about "Running", and clients will get a consensus
 with no usable relays. Instead, authorities refuse to build a
 consensus if this happens. Bugfix on 0.2.0.10-alpha; fixes bug 1066.
- If your relay can't keep up with the number of incoming create
 cells, it would log one warning per failure into your logs. Limit
 warnings to 1 per minute. Bugfix on 0.0.2pre10; fixes bug 1042.
- Bridges now use "reject \*:\*" as their default exit policy. Bugfix
 on 0.2.0.3-alpha; fixes bug 1113.
- Fix a memory leak on directory authorities during voting that was
 introduced in 0.2.2.1-alpha. Found via valgrind.

The original announcement can be found at [http://archives.seul.org/or/talk/Nov-2009/msg00106.html](http://archives.seul.org/or/talk/Nov-2009/msg00106.html "http://archives.seul.org/or/talk/Nov-2009/msg00106.html")

