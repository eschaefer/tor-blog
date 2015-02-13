---
layout: post
title: "Research problem: adaptive throttling of Tor clients by entry guards"
permalink: research-problem-adaptive-throttling-tor-clients-entry-guards
date: 2010-09-19 17:02:14
author: arma
category: blog
status: closed
tags: ["bandwidth throttling", "research", "research progress", "thesis idea", "torperf"]
---

Looking for a paper topic (or a thesis topic)? Here's a Tor research area that needs more attention. The short version is: if we prevent the really loud users from using too much of the Tor network, how much can it help?

We've instrumented Tor's entry relays so they can rate-limit connections from users, and we've instrumented the directory authorities so they can change the rate-limiting parameters globally across the network. Which parameter values improve performance for the Tor network as a whole? How should relays adapt their rate-limiting parameters based on their capacity and based on the network load they see, and what rate-limiting algorithms will work best?

We'd love to [work with you](https://www.torproject.org/research) to help answer these questions. [**read more »**](https://blog.torproject.org/blog/research-problem-adaptive-throttling-tor-clients-entry-guards)
