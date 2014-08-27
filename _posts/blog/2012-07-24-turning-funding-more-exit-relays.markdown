---
layout: post
title: "Turning funding into more exit relays"
permalink: turning-funding-more-exit-relays
date: 2012-07-24
author: arma
category: blog
tags: ["exit relays", "performance", "scaling", "volunteer support"]
---

For a few years now, funders have been asking if they can pay Tor to run more relays. I kept telling them their money was better spent on code and design improvements:  
 [https://blog.torproject.org/blog/why-tor-is-slow](https://blog.torproject.org/blog/why-tor-is-slow "https://blog.torproject.org/blog/why-tor-is-slow")  
 [https://trac.torproject.org/projects/tor/wiki/org/roadmaps/Tor/Performan...](https://trac.torproject.org/projects/tor/wiki/org/roadmaps/Tor/Performance "https://trac.torproject.org/projects/tor/wiki/org/roadmaps/Tor/Performance")  
since a) network load would just grow to fill whatever new capacity we have, especially if we don't deal with the tiny fraction of users who do bulk downloads, and b) reducing diversity of relay operator control can harm anonymity.

But lately the Tor network has become noticeably faster, and I think it has a lot to do with the growing amount of excess relay capacity relative to network load:  
 [https://metrics.torproject.org/network.html?graph=bandwidth&start=2010-0...](https://metrics.torproject.org/network.html?graph=bandwidth&start=2010-06-01&end=2012-07-21#bandwidth "https://metrics.torproject.org/network.html?graph=bandwidth&start=2010-06-01&end=2012-07-21#bandwidth")

At the same time, much of our performance improvement comes from better load balancing -- that is, concentrating traffic on the relays that can handle it better. The result though is a direct tradeoff with relay diversity: on today's network, clients choose one of the fastest 5 exit relays around 25-30% of the time, and 80% of their choices come from a pool of 40-50 relays.  
 [https://trac.torproject.org/projects/tor/ticket/6443](https://trac.torproject.org/projects/tor/ticket/6443 "https://trac.torproject.org/projects/tor/ticket/6443")

Since extra capacity is clearly good for performance, and since we're not doing particularly well at diversity with the current approach, we're going to try an experiment: we'll connect funding to exit relay operators so they can run bigger and/or better exit relays.

If we do it right (make more faster exit relays that aren't the current biggest ones, so there are more to choose from), we will improve the network's diversity as well as being able to handle more users.

We've lined up our first funder (BBG, aka [http://www.voanews.com/](http://www.voanews.com/ "http://www.voanews.com/")), and they're excited to have us start as soon as we can. They want to sponsor 125+ fast exits.

I've started a discussion on the tor-relays list about open questions that we as a community will need to decide about:  
1) What exactly would we pay for?  
2) Should we fund existing relays or new ones?  
4) What exactly do we mean by diversity?  
5) How much "should" an exit relay cost?  
6) How exactly should we choose which exit relay operators to reimburse?  
7) How do we audit / track the sponsored relays?  
8) Legal questions?

The first step is collecting facts about the current fast Tor exit relays. Please join the discussion on the tor-relays list if you want to contribute:  
 [https://lists.torproject.org/pipermail/tor-relays/2012-July/001433.html](https://lists.torproject.org/pipermail/tor-relays/2012-July/001433.html "https://lists.torproject.org/pipermail/tor-relays/2012-July/001433.html")

