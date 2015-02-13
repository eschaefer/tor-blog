---
layout: post
title: "Tor Check Outage on 03 and 04 July 2013"
permalink: tor-check-outage-03-and-04-july-2013
date: 2013-07-04 07:53:11
author: phobos
category: blog
status: closed
tags: ["abuse", "check", "dns queries from hell", "exitlist", "TorCheck"]
---

Over the past 24 hours [https://check.torproject.org](https://check.torproject.org "https://check.torproject.org") has been unavailable due to excessive DNS queries to the exitlist service. It seems there are a number of individuals and companies with commercial products relying upon this volunteer service. We finally hit the point where we couldn't keep up with the queries and simply disabled the service.

This is a volunteer service offered as a proof of concept. We strongly encourage people to run their own. The code is available at [https://svn.torproject.org/svn/check/trunk/](https://svn.torproject.org/svn/check/trunk/ "https://svn.torproject.org/svn/check/trunk/").

The new [Tor Browser 3.0 alpha](https://blog.torproject.org/blog/tor-browser-bundle-30alpha2-released) series includes a new way to detect "tor or not" locally, without relying on a single point of failure service. This is the first step towards finally retiring check.torproject.org for good.

As of 09:00 on 04 July 2013, the service is re-enabled. We reserve the right to take it down as needed without notice.
