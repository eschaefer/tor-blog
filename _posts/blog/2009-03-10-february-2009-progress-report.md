---
layout: post
title: "February 2009 Progress Report"
permalink: february-2009-progress-report
date: 2009-03-10 10:24:22
author: phobos
category: blog
status: closed
tags: ["anonymity advocacy", "progress report", "translation"]
---

**New releases, new hires, new funding**  
 On February 8, we released versions 0.2.0.34-stable and 0.2.1.12-alpha.

Tor 0.2.0.34 features several more security-related fixes. You should upgrade, especially if you run an exit relay (remote crash) or a directory authority (remote infinite loop), or you're on an older (pre-XP) or not-recently-patched Windows (remote exploit).

This release marks end-of-life for Tor 0.1.2.x. Those Tor versions have many known flaws, and nobody should be using them. You should upgrade. If you're using a Linux or BSD and its packages are obsolete, stop using those packages and upgrade anyway.

**Enhancements**  
 In Tor 0.2.1.12-alpha, if we're using bridges and our network goes away, be more willing to forgive our bridges and try again when we get an application request. Bugfix on 0.2.0.x. [**read more »**](https://blog.torproject.org/blog/february-2009-progress-report)
