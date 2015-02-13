---
layout: post
title: "An update on the censorship in Ethiopia"
permalink: update-censorship-ethiopia
date: 2012-06-03 10:12:58
author: Runa
category: blog
status: closed
tags: ["censorship circumvention", "deep packet inspection", "dpi", "ethiopia", "internet censorship", "tor blocked"]
---

A few days ago, we published a blog post exposing the use of [Deep Packet Inspection (DPI) to filter all Internet traffic in Ethiopia](https://blog.torproject.org/blog/ethiopia-introduces-deep-packet-inspection), including connections to the Tor network. We concluded that they are doing some sort of TLS fingerprinting, but had not been able to figure out exactly what they are fingerprinting on. Since then, we have managed to determine exactly how Ethiopia blocks Tor and we have developed a workaround. We will publish a full technical analysis very soon.

The long-term solution for Tor users in Ethiopia is to use the [Obfsproxy Tor Browser Bundle](https://www.torproject.org/projects/obfsproxy). The bundles are, unfortunately, not up to date at the moment, but this is something we are working on (see [\#5937](https://trac.torproject.org/projects/tor/ticket/5937) for details). In the meantime, try using one of the following three bridges:

213.138.103.17:443  
 107.21.149.216:443  
 46.137.226.203:55440

If the bridges are not working, or you have questions, send an email to [help@rt.torproject.org](mailto:help@rt.torproject.org).
