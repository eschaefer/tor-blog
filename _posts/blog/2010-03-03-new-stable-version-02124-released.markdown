---
layout: post
title: "New Stable Version 0.2.1.24 released"
permalink: new-stable-version-02124-released
date: 2010-03-03
author: phobos
category: blog
tags: ["apple osx love", "bug fixes", "enhancements", "performance enhancements", "stable release", "tor update"]
---

Tor 0.2.1.23 fixes a huge client-side performance bug, makes Tor work again on the latest OS X, and updates the location of a directory authority.

Tor 0.2.1.24 makes Tor work again on the latest OS X -- this time for sure!

The Windows and OS X bundles also come with a newer version of Polipo that fixes some stability and security problems.

People using Tor as a client should upgrade:  
 [https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

Changes in version 0.2.1.23 - 2010-02-13  
**Major bugfixes (performance):**

- We were selecting our guards uniformly at random, and then weighting which of our guards we'd use uniformly at random. This imbalance meant that Tor clients were severely limited on throughput (and probably latency too) by the first hop in their circuit. Now we select guards weighted by currently advertised bandwidth. We also automatically discard guards picked using the old algorithm. Fixes bug 1217; bugfix on 0.2.1.3-alpha. Found by Mike Perry.

**Major bugfixes:**

- Make Tor work again on the latest OS X: when deciding whether to use strange flags to turn TLS renegotiation on, detect the OpenSSL version at run-time, not compile time. We need to do this because Apple doesn't update its dev-tools headers when it updates its libraries in a security patch.
- Fix a potential buffer overflow in lookup\_last\_hid\_serv\_request() that could happen on 32-bit platforms with 64-bit time\_t. Also fix a memory leak when requesting a hidden service descriptor we've requested before. Fixes bug 1242, bugfix on 0.2.0.18-alpha. Found by aakova.

**Minor bugfixes:**

- Refactor resolve\_my\_address() to not use gethostbyname() anymore. Fixes bug 1244; bugfix on 0.0.2pre25. Reported by Mike Mestnik.

**Minor features:**

- Avoid a mad rush at the beginning of each month when each client rotates half of its guards. Instead we spread the rotation out throughout the month, but we still avoid leaving a precise timestamp in the state file about when we first picked the guard. Improves over the behavior introduced in 0.1.2.17.

Changes in version 0.2.1.24 - 2010-02-21  
**Minor bugfixes:**

- Work correctly out-of-the-box with even more vendor-patched versions of OpenSSL. In particular, make it so Debian and OS X don't need customized patches to run/build.

