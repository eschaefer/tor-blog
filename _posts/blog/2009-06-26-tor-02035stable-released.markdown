---
layout: post
title: "Tor 0.2.0.35-stable released"
permalink: blog/tor-02035stable-released
date: 2009-06-26
author: phobos
category: blog
tags: ["bug fixes", "hidden service fixes", "stable release"]
---

Tor 0.2.0.35 fixes a big bug that was causing Tor relays with dynamic
IP addresses to disappear from the network. It also fixes a rare crash
bug on fast exit relays.

[https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

Changes in version 0.2.0.35 - 2009-06-24
**Security fix:**

- Avoid crashing in the presence of certain malformed descriptors.
 Found by lark, and by automated fuzzing.
- Fix an edge case where a malicious exit relay could convince a
 controller that the client's DNS question resolves to an internal IP
 address. Bug found and fixed by "optimist"; bugfix on 0.1.2.8-beta.

**Major bugfixes:**

- Finally fix the bug where dynamic-IP relays disappear when their
 IP address changes: directory mirrors were mistakenly telling
 them their old address if they asked via begin\_dir, so they
 never got an accurate answer about their new address, so they
 just vanished after a day. For belt-and-suspenders, relays that
 don't set Address in their config now avoid using begin\_dir for
 all direct connections. Should fix bugs 827, 883, and 900.
- Fix a timing-dependent, allocator-dependent, DNS-related crash bug
 that would occur on some exit nodes when DNS failures and timeouts
 occurred in certain patterns. Fix for bug 957.

**Minor bugfixes:**

- When starting with a cache over a few days old, do not leak
 memory for the obsolete router descriptors in it. Bugfix on
 0.2.0.33; fixes bug 672.
- Hidden service clients didn't use a cached service descriptor that
 was older than 15 minutes, but wouldn't fetch a new one either,
 because there was already one in the cache. Now, fetch a v2
 descriptor unless the same descriptor was added to the cache within
 the last 15 minutes. Fixes bug 997; reported by Marcus Griep.

The original announcement can be found at [http://archives.seul.org/or/announce/Jun-2009/msg00000.html](http://archives.seul.org/or/announce/Jun-2009/msg00000.html "http://archives.seul.org/or/announce/Jun-2009/msg00000.html")

