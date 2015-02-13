---
layout: post
title: "Overhead from directory info: past, present, future"
permalink: overhead-directory-info-past-present-future
date: 2009-02-16 02:05:16
author: arma
category: blog
status: closed
tags: ["directory", "performance", "research"]
---

A growing number of people want to use Tor in low-bandwidth contexts (e.g. modems or shared Internet cafes in the Middle East) and mobile contexts (start up a Tor client, use it for a short time, and then stop it again). Currently Tor is nearly unusable in these situations, because it spends too many bytes fetching directory info. This post summarizes the steps we've taken so far to reduce directory overhead, and explains the steps that are coming next.

First, what do I mean by "directory info"? Part of the Tor design is the \_discovery\_ component: how clients learn about the available Tor relays, along with their keys, locations, exit policies, and so on. Tor's solution so far uses a few trusted directory authorities that sign and distribute official lists of the relays that make up the Tor network. [**read more »**](https://blog.torproject.org/blog/overhead-directory-info%3A-past%2C-present%2C-future)
