---
layout: post
title: "Tor 0.2.1.16-rc Release Candidate now available"
permalink: blog/tor-02116rc-release-candidate-now-available
date: 2009-06-24
author: phobos
category: blog
tags: ["bug fixes", "hidden service fixes", "release candidate", "security fixes"]
---

Tor 0.2.1.16-rc speeds up performance for fast exit relays, and fixes
a bunch of minor bugs.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

Changes in version 0.2.1.16-rc - 2009-06-20
**Security fixes:**

- Fix an edge case where a malicious exit relay could convince a
 controller that the client's DNS question resolves to an internal IP
 address. Bug found and fixed by "optimist"; bugfix on 0.1.2.8-beta.

**Major performance improvements (on 0.2.0.x):**

- Disable and refactor some debugging checks that forced a linear scan
 over the whole server-side DNS cache. These accounted for over 50%
 of CPU time on a relatively busy exit node's gprof profile. Found
 by Jacob.
- Disable some debugging checks that appeared in exit node profile
 data.

**Minor features:**

- Update to the "June 3 2009" ip-to-country file.
- Do not have tor-resolve automatically refuse all .onion addresses;
 if AutomapHostsOnResolve is set in your torrc, this will work fine.

**Minor bugfixes (on 0.2.0.x):**

- Log correct error messages for DNS-related network errors on
 Windows.
- Fix a race condition that could cause crashes or memory corruption
 when running as a server with a controller listening for log
 messages.
- Avoid crashing when we have a policy specified in a DirPolicy or
 SocksPolicy or ReachableAddresses option with ports set on it,
 and we re-load the policy. May fix bug 996.
- Hidden service clients didn't use a cached service descriptor that
 was older than 15 minutes, but wouldn't fetch a new one either,
 because there was already one in the cache. Now, fetch a v2
 descriptor unless the same descriptor was added to the cache within
 the last 15 minutes. Fixes bug 997; reported by Marcus Griep.

**Minor bugfixes (on 0.2.1.x):**

- Don't warn users about low port and hibernation mix when they
 provide a \*ListenAddress directive to fix that. Bugfix on
 0.2.1.15-rc.
- When switching back and forth between bridge mode, do not start
 gathering GeoIP data until two hours have passed.
- Do not complain that the user has requested an excluded node as
 an exit when the node is not really an exit. This could happen
 because the circuit was for testing, or an introduction point.
 Fix for bug 984.

The original announcement can be found at [http://archives.seul.org/or/talk/Jun-2009/msg00288.html](http://archives.seul.org/or/talk/Jun-2009/msg00288.html "http://archives.seul.org/or/talk/Jun-2009/msg00288.html")

