---
layout: post
title: "New Stable released, Tor 0.2.1.21"
permalink: new-stable-released-tor-02121
date: 2009-12-30 09:21:46
author: phobos
category: blog
status: closed
tags: ["bug fixes", "exit relays", "openssl fixes", "stable release"]
---

Tor 0.2.1.21 fixes an incompatibility with the most recent OpenSSL  
 library. If you use Tor on Linux / Unix and you're getting SSL  
 renegotiation errors, upgrading should help. We also recommend an  
 upgrade if you're an exit relay.

[https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

Changes in version 0.2.1.21 - 2009-12-21  
 **Major bugfixes:**

-   Work around a security feature in OpenSSL 0.9.8l that prevents our  
     handshake from working unless we explicitly tell OpenSSL that we  
     are using SSL renegotiation safely. We are, of course, but OpenSSL  
     0.9.8l won't work unless we say we are.
-   Avoid crashing if the client is trying to upload many bytes and the  
     circuit gets torn down at the same time, or if the flip side  
     happens on the exit relay. Bugfix on 0.2.0.1-alpha; fixes bug 1150.

**Minor bugfixes:** [**read more »**](https://blog.torproject.org/blog/new-stable-released-tor-02121)

Do not refuse to learn about authority certs and v2 networkstatus  

