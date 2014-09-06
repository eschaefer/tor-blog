---
layout: post
title: "New bundles (security release)"
permalink: blog/new-bundles-security-release
date: 2012-09-12
author: erinn
category: blog
tags: ["release candidate", "security fixes", "stable release", "tbb", "tor", "tor browser bundle"]
---

New Bundles (security release)

All of the available bundles of Tor have been updated for the latest stable Tor 0.2.2.39 release and the 0.2.3.22-rc release. These releases fix a remote crash bug found in Tor and all users and relays are **STRONGLY** encouraged to update immediately.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

Further notes about Tor Browser Bundle updates:

The random port selection has been temporarily disabled in the Linux and Mac OS X alpha bundles. Most of you probably didn't notice any random port selection happpening at all, but if you encounter a problem running a system Tor and your Tor Browser Bundle at the same time, you can switch to the stable bundles for now. The next update should have a fix that allows us to re-enable automatic port selection.

**Tor Browser Bundle (2.2.39-1)**

- Update Tor to 0.2.2.39
- Update NoScript to 2.5.4

**Tor Browser Bundle (2.3.22-alpha-1)**

- Update Tor to 0.2.3.22-rc
- Temporarily use fixed Control and SOCKS ports as a workaround for #6803

