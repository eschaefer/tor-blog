---
layout: post
title: "Tor 0.2.0.33-stable released"
permalink: tor-02033-stable-released
date: 2009-01-22 14:25:00
author: phobos
category: blog
status: closed
tags: ["bug fixes", "security fixes", "stable release"]
---

Tor 0.2.0.33 fixes a variety of bugs that were making relays less useful  
 to users. It also finally fixes a bug where a relay or client that's  
 been off for many days would take a long time to bootstrap.

This update also fixes an important security-related bug reported by  
 Ilja van Sprundel. You should upgrade. (We'll send out more details  
 about the bug once people have had some time to upgrade.)

[https://www.torproject.org/download.html](https://www.torproject.org/download.html "https://www.torproject.org/download.html")

Changes in version 0.2.0.33 - 2009-01-21  
 **Security fixes:**

-   Fix a heap-corruption bug that may be remotely triggerable on  
     some platforms. Reported by Ilja van Sprundel.

**Major bugfixes:**

When a stream at an exit relay is in state "resolving" or  
 "connecting" and it receives an "end" relay cell, the exit relay  
 would silently ignore the end cell and not close the stream. If  
 the client never closes the circuit, then the exit relay never [**read more »**](https://blog.torproject.org/blog/tor-02033-stable-released)
