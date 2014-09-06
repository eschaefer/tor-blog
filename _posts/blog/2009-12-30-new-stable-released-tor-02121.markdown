---
layout: post
title: "New Stable released, Tor 0.2.1.21"
permalink: blog/new-stable-released-tor-02121
date: 2009-12-30
author: phobos
category: blog
tags: ["bug fixes", "exit relays", "openssl fixes", "stable release"]
---

Tor 0.2.1.21 fixes an incompatibility with the most recent OpenSSL
library. If you use Tor on Linux / Unix and you're getting SSL
renegotiation errors, upgrading should help. We also recommend an
upgrade if you're an exit relay.

[https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

Changes in version 0.2.1.21 - 2009-12-21
**Major bugfixes:**

- Work around a security feature in OpenSSL 0.9.8l that prevents our
 handshake from working unless we explicitly tell OpenSSL that we
 are using SSL renegotiation safely. We are, of course, but OpenSSL
 0.9.8l won't work unless we say we are.
- Avoid crashing if the client is trying to upload many bytes and the
 circuit gets torn down at the same time, or if the flip side
 happens on the exit relay. Bugfix on 0.2.0.1-alpha; fixes bug 1150.

**Minor bugfixes:**

- Do not refuse to learn about authority certs and v2 networkstatus
 documents that are older than the latest consensus. This bug might
 have degraded client bootstrapping. Bugfix on 0.2.0.10-alpha.
 Spotted and fixed by xmux.
- Fix a couple of very-hard-to-trigger memory leaks, and one hard-to-
 trigger platform-specific option misparsing case found by Coverity
 Scan.
- Fix a compilation warning on Fedora 12 by removing an impossible-to-
 trigger assert. Fixes bug 1173.

The original announcement can be found at [http://archives.seul.org/or/announce/Dec-2009/msg00000.html](http://archives.seul.org/or/announce/Dec-2009/msg00000.html "http://archives.seul.org/or/announce/Dec-2009/msg00000.html")

