---
layout: post
title: "Tor 0.2.0.35-stable released"
permalink: tor-02035stable-released
date: 2009-06-25 19:34:49
author: phobos
category: blog
status: closed
tags: ["bug fixes", "hidden service fixes", "stable release"]
---

Tor 0.2.0.35 fixes a big bug that was causing Tor relays with dynamic  
 IP addresses to disappear from the network. It also fixes a rare crash  
 bug on fast exit relays.

[https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

Changes in version 0.2.0.35 - 2009-06-24  
 **Security fix:**

-   Avoid crashing in the presence of certain malformed descriptors.  
     Found by lark, and by automated fuzzing.
-   Fix an edge case where a malicious exit relay could convince a  
     controller that the client's DNS question resolves to an internal IP  
     address. Bug found and fixed by "optimist"; bugfix on 0.1.2.8-beta.

**Major bugfixes:**

Finally fix the bug where dynamic-IP relays disappear when their  
 IP address changes: directory mirrors were mistakenly telling  
 them their old address if they asked via begin\_dir, so they  
 never got an accurate answer about their new address, so they [**read more »**](https://blog.torproject.org/blog/tor-02035stable-released)
