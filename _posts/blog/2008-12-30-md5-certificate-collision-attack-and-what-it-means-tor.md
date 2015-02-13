---
layout: post
title: "The MD5 certificate collision attack, and what it means for Tor"
permalink: md5-certificate-collision-attack-and-what-it-means-tor
date: 2008-12-30 11:53:04
author: nickm
category: blog
status: closed
tags: ["attack", "md5", "security", "ssl", "tls", "x509"]
---

Today, a team of security researchers and cryptographers gave a talk at the [25th Chaos Communication Congress (25C3)](http://events.ccc.de/congress/2008/), about a [nifty attack against X.509 certificates generated using the MD5 digest algorithm](http://www.win.tue.nl/hashclash/rogue-ca/). We figured that people will ask us about how this attack affects Tor, so I'm writing an answer in advance.

**The short version:** This attack doesn't affect Tor.

**The medium version:** This attack doesn't affect Tor, since Tor doesn't ever use MD5 certificates, and since Tor doesn't care what certificate authorities say. On the other hand, this attack probably *does* affect your browser. Check your browser vendor for updates over the next few days and weeks, and make sure you install them. [**read more »**](https://blog.torproject.org/blog/md5-certificate-collision-attack%2C-and-what-it-means-tor)
