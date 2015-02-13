---
layout: post
title: "Updated Tor Cloud images"
permalink: updated-tor-cloud-images-380
date: 2012-01-16 14:32:31
author: Runa
category: blog
status: closed
tags: ["bridge relays", "cloud", "tor", "tor cloud"]
---

The [Tor Cloud](https://cloud.torproject.org/) images for all the seven regions have been updated to include the *[anonymizing relay monitor (arm)](http://www.atagar.com/arm/)*. This works much like top does for system usage, providing real time statistics for bandwidth, cpu, memory usage, current Tor configuration, connection details etc.

If you're already running a Tor Cloud instance and wish to install arm, connect to your instance with SSH and run *sudo aptitude install tor-arm*.
