---
layout: post
title: "Apple workaround for openssl issues on OS X 10.5 and 10.6"
permalink: apple-workaround-openssl-issues-os-x-105-and-106
date: 2010-02-01
author: phobos
category: blog
tags: ["10.3", "10.4", "10.5", "10.6", "confused users", "openssl", "osx", "packaging mess", "tls renegotiation"]
---

Apple responded to my bug report about a broken openssl. I've since built test packages for OS X 10.5 and 10.6 users. Their response is:

> Thank you for your report of this issue with Tor.
> 
> The issue you're seeing is because the current versions of the development tools were created before the OpenSSL security fix, and so do not include the "SSL3\_FLAGS\_ALLOW\_UNSAFE\_LEGACY\_RENEGOTIATION" definition in the OpenSSL headers.
> 
> You can work around this issue by supplying the definition to Tor directly, for example by compiling Tor using
> 
> CPPFLAGS='-DSSL3\_FLAGS\_ALLOW\_UNSAFE\_LEGACY\_RENEGOTIATION=0x0010' ./configure && make
> 
> This will work on both Leopard and Snow Leopard.

If you have an Intel (i386) Mac, use the normal i386 packages for Tor 0.2.2.8-alpha release at [https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download").

If you have a PowerPC (ppc) Mac AND are running OS X 10.5 or 10.6, use these packages:

Tor Expert: [https://www.torproject.org/dist/osx-old/Tor-0.2.2.8-alpha-i386-10.5-10.6...](https://www.torproject.org/dist/osx-old/Tor-0.2.2.8-alpha-i386-10.5-10.6-only-Bundle.dmg "https://www.torproject.org/dist/osx-old/Tor-0.2.2.8-alpha-i386-10.5-10.6-only-Bundle.dmg") and .asc.

Vidalia Bundle: [https://www.torproject.org/dist/vidalia-bundles/vidalia-bundle-0.2.2.8-a...](https://www.torproject.org/dist/vidalia-bundles/vidalia-bundle-0.2.2.8-alpha-0.2.7-10.5-10.6-only-ppc.dmg "https://www.torproject.org/dist/vidalia-bundles/vidalia-bundle-0.2.2.8-alpha-0.2.7-10.5-10.6-only-ppc.dmg") and .asc.

If you have a PowerPC (ppc) Mac AND ARE running OS X 10.3 or 10.4, use the normal ppc packages at [https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download").

This can be confusing. I now maintain two different PowerPC packages. One set for pre-10.5 and one set for 10.5 and later OS X versions. This is because Apple didn't update 10.3 nor 10.4 for the openssl bug.

