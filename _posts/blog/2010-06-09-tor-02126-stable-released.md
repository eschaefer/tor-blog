---
layout: post
title: "Tor 0.2.1.26-stable released"
permalink: tor-02126-stable-released
date: 2010-06-09 22:18:21
author: phobos
category: blog
status: closed
tags: ["connection overload", "stable release", "test suite fixes", "v3 directories"]
---

Tor 0.2.1.26 addresses the recent connection and memory overload problems we've been seeing on relays, especially relays with their DirPort open. If your relay has been crashing, or you turned it off because it used too many resources, give this release a try.

This release also fixes yet another instance of broken OpenSSL libraries that was causing some relays to drop out of the consensus.

Available for download at [https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

Changes in version 0.2.1.26  
 **Major bugfixes:**

Teach relays to defend themselves from connection overload. Relays  
 now close idle circuits early if it looks like they were intended  
 for directory fetches. Relays are also more aggressive about closing  
 TLS connections that have no circuits on them. Such circuits are  
 unlikely to be re-used, and tens of thousands of them were piling  
 up at the fast relays, causing the relays to run out of sockets [**read more »**](https://blog.torproject.org/blog/tor-02126-stable-released)
