---
layout: post
title: "Research problem: measuring the safety of the Tor network"
permalink: research-problem-measuring-safety-tor-network
date: 2011-02-06 00:18:00
author: arma
category: blog
status: closed
tags: ["research", "research progress", "thesis idea"]
---

We need a better understanding of how much anonymity the Tor network provides against a partial network adversary who observes and/or operates some of the network. Specifically, we want to understand the chances that this class of adversary can observe a user's traffic coming into the network and also the corresponding traffic exiting the network.

Most of our graphs historically have looked at the total number of relays over time. But this simple scalar doesn't take into account relay capacity, exit policies, geographic or network location, etc.

One concrete problem from this bad metric is that when many new relays show up (e.g. due to a [political event](https://blog.torproject.org/files/relays-diff-2011-01-28.png)), we really don't have any insight about how the diversity of the new relays compares to the rest of the network. The simplistic metric also gets misused in academic research papers to produce misleading results like "I can sign up 2% of the Tor relays and capture 50% of the paths," when what they mean is "I can provide half the capacity in the Tor network and capture half the paths."

There are four parts to this research problem. First, we need a broad array of metrics that reflect various instances of our partial network adversary. Second, we need to understand for each metric how stable it is (sensitivity analysis) and what changes in the Tor network would efficiently improve (or harm) it. Third, we should make the calculations as realistic as possible based on actual Tor client behavior. Last, we need a better infrastructure for comparing the safety impact from alternate design scenarios, for example different path selection or route balancing algorithms.

We'd love to [work with you](https://www.torproject.org/research) to help answer these questions. [**read more »**](https://blog.torproject.org/blog/research-problem-measuring-safety-tor-network)
