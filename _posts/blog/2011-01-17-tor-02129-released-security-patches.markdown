---
layout: post
title: "Tor 0.2.1.29 is released (security patches)"
permalink: blog/tor-02129-released-security-patches
date: 2011-01-17
author: erinn
category: blog
tags: ["security fixes", "stable releases", "tor"]
---

Tor 0.2.1.29 continues our recent code security audit work. The main
fix resolves a remote heap overflow vulnerability that can allow remote
code execution. Other fixes address a variety of assert and crash bugs,
most of which we think are hard to exploit remotely.

**All Tor users should upgrade.**

[https://www.torproject.org/download/download](https://www.torproject.org/download/download "https://www.torproject.org/download/download")

Changes in version 0.2.1.29 - 2011-01-15
**Major bugfixes (security):**

- Fix a heap overflow bug where an adversary could cause heap
 corruption. This bug probably allows remote code execution
 attacks. Reported by "debuger". Fixes CVE-2011-0427. Bugfix on
 0.1.2.10-rc.
- Prevent a denial-of-service attack by disallowing any
 zlib-compressed data whose compression factor is implausibly
 high. Fixes part of bug 2324; reported by "doorss".
- Zero out a few more keys in memory before freeing them. Fixes
 bug 2384 and part of bug 2385. These key instances found by
 "cypherpunks", based on Andrew Case's report about being able
 to find sensitive data in Tor's memory space if you have enough
 permissions. Bugfix on 0.0.2pre9.

**Major bugfixes (crashes):**

- Prevent calls to Libevent from inside Libevent log handlers.
 This had potential to cause a nasty set of crashes, especially
 if running Libevent with debug logging enabled, and running
 Tor with a controller watching for low-severity log messages.
 Bugfix on 0.1.0.2-rc. Fixes bug 2190.
- Add a check for SIZE\_T\_MAX to tor\_realloc() to try to avoid
 underflow errors there too. Fixes the other part of bug 2324.
- Fix a bug where we would assert if we ever had a
 cached-descriptors.new file (or another file read directly into
 memory) of exactly SIZE\_T\_CEILING bytes. Fixes bug 2326; bugfix
 on 0.2.1.25. Found by doorss.
- Fix some potential asserts and parsing issues with grossly
 malformed router caches. Fixes bug 2352; bugfix on Tor 0.2.1.27.
 Found by doorss.

**Minor bugfixes (other):**

- Fix a bug with handling misformed replies to reverse DNS lookup
 requests in DNSPort. Bugfix on Tor 0.2.0.1-alpha. Related to a
 bug reported by doorss.
- Fix compilation on mingw when a pthreads compatibility library
 has been installed. (We don't want to use it, so we shouldn't
 be including pthread.h.) Fixes bug 2313; bugfix on 0.1.0.1-rc.
- Fix a bug where we would declare that we had run out of virtual
 addresses when the address space was only half-exhausted. Bugfix
 on 0.1.2.1-alpha.
- Correctly handle the case where AutomapHostsOnResolve is set but
 no virtual addresses are available. Fixes bug 2328; bugfix on
 0.1.2.1-alpha. Bug found by doorss.
- Correctly handle wrapping around when we run out of virtual
 address space. Found by cypherpunks, bugfix on 0.2.0.5-alpha.

**Minor features:**

- Update to the January 1 2011 Maxmind GeoLite Country database.
- Introduce output size checks on all of our decryption functions.

**Build changes:**

- Tor does not build packages correctly with Automake 1.6 and earlier;
 added a check to Makefile.am to make sure that we're building with
 Automake 1.7 or later.
- The 0.2.1.28 tarball was missing src/common/OpenBSD\_malloc\_Linux.c
 because we built it with a too-old version of automake. Thus that
 release broke ./configure --enable-openbsd-malloc, which is popular
 among really fast exit relays on Linux.

