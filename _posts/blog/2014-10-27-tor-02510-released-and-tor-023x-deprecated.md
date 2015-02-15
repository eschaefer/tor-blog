---
layout: post
title: "Tor 0.2.5.10 is released! (and Tor 0.2.3.x is deprecated)"
permalink: tor-02510-released-and-tor-023x-deprecated
date: 2014-10-27 08:25:36
author: nickm
category: blog
comments: open
tags: ["deprecation", "release", "tor", "tor-025"]
---

Tor 0.2.5.10 is the first stable release in the 0.2.5 series.

It adds several new security features, including improved denial-of-service resistance for relays, new compiler hardening options, and a system-call sandbox for hardened installations on Linux (requires seccomp2). The controller protocol has several new features, resolving IPv6 addresses should work better than before, and relays should be a little more CPU-efficient. We've added support for more OpenBSD and FreeBSD transparent proxy types. We've improved the build system and testing infrastructure to allow unit testing of more parts of the Tor codebase. Finally, we've addressed several nagging pluggable transport usability issues, and included numerous other small bugfixes and features mentioned below.

This release marks end-of-life for Tor 0.2.3.x; those Tor versions have accumulated many known flaws; everyone should upgrade.

Below we list all changes in 0.2.5.10 since the 0.2.4.x series; for a list of changes in individual alpha releases, [see the ChangeLog](https://gitweb.torproject.org/tor.git/blob_plain/refs/heads/release-0.2.5:/ChangeLog). [**read more »**](https://blog.torproject.org/blog/tor-02510-released-and-tor-023x-deprecated)

Changes in version 0.2.5.10 - 2014-10-24
----------------------------------------
