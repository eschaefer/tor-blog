---
layout: post
title: "Apple workaround for openssl issues on OS X 10.5 and 10.6"
permalink: apple-workaround-openssl-issues-os-x-105-and-106
date: 2010-01-31 22:10:14
author: phobos
category: blog
status: closed
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

If you have a PowerPC (ppc) Mac AND are running OS X 10.5 or 10.6, use these packages: [**read more »**](https://blog.torproject.org/blog/apple-workaround-openssl-issues-os-x-105-and-106)
