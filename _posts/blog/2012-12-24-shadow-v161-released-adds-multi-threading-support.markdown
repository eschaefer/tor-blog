---
layout: post
title: "Shadow v1.6.1 released, adds multi-threading support"
permalink: shadow-v161-released-adds-multi-threading-support
date: 2012-12-24
author: arma
category: blog
tags: ["metrics", "performance", "shadow"]
---

Rob just tagged [Shadow](http://shadow.cs.umn.edu/) v1.6.1, and added a link on [the download page](http://shadow.cs.umn.edu/download/). This is really more like a pre-1.7.0 release, but he wanted to get out some exciting new support for running multi-threaded simulations earlier!

This release includes:

- Support for running multi-threaded simulations! (use the “-w” flag to specify the number of worker threads)
- A few bugfixes

In preliminary testing, the biggest improvements have been seen when using between 4 and 8 worker threads. Happy simulating!

