---
layout: post
title: "Testing Tor Browser Bundle 1.2.7-dev"
permalink: testing-tor-browser-bundle-127dev
date: 2009-08-16
author: phobos
category: blog
tags: ["openssl fixes", "tor browser bundle", "usability enhancements", "vidalia releases"]
---

I've updated the Tor Browser Bundle with torbutton 1.2.2, the [new Vidalia 0.2.2](//blog.torproject.org/blog/vidalia-022-released), and openssl 0.9.8k compiled with Microsoft Visual C to handle ssl compatibility issues with various versions of Windows.

If this works, it will be the new Tor Browser Bundle 1.2.8. Please test away.

The full list of changes:

- update Torbutton to 1.2.2
- update Vidalia to 0.2.2
- compile OpenSSL 0.9.8k with Visual C to make dlls

There is an issue for some people using a clean Windows XP, Vista, 7 which would either require we ship the Visual C redistributable package, or compile OpenSSL ourselves with Visual C. The symptoms were the "find bridges now" button didn't appear in Vidalia 0.2.x, and the relays would never get flags. A few people posted comments to this blog about lacking flags and geoip information with TBB.

This is now fixed (at least it works on a freshly installed and patched WinXP system).

