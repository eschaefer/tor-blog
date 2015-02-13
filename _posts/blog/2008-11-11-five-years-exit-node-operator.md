---
layout: post
title: "Five Years as an Exit Node Operator"
permalink: five-years-exit-node-operator
date: 2008-11-11 00:50:57
author: phobos
category: blog
status: closed
tags: ["exit node", "exit relay", "hugging dmca notices", "operator experiences", "tor is benign"]
---

The official version of ["What to expect"](https://www.torproject.org/faq-abuse.html.en#TypicalAbuses) when running a Tor exit relay is fairly brief. This post will be verbose.

I've been running a node since 2003. I first started off running a node in Xen on a server at a colocation datacenter with an un-metered line. The dual Xeon kept up with the demands fairly well. I ran it with the default exit policy with open irc ports. Things went smoothly for many months until my ISP called. The Abuse Department said my IP was reported in a mass irc bot attack against [DalNet](http://www.dal.net/). I spent some time on the phone explaining Tor, explaining how it's an anonymizing proxy, and how it's used for good in the world. I highlighted that of the megabits of bandwidth it provided 7x24 for many months, this was the first issue. They asked that I block irc ports, and all would be well. I modified the exit policy to block irc ports.

Many more months passed without issue. Apparently, given the lax bandwidth controls, many other customers ran Tor exit nodes as well. The ISP updated their Terms of Service, and notified all of us that running any proxy was now in violation of the ToS. This meant I was at risk of disconnection. I switched to a non-exit configuration. I ran this way for months. I knew full well I was violating the ToS. If I was disconnected, it was my fault. Then the ISP was bought; and the new owners demanded I shut off my Tor node or be disconnected. It was fun while it lasted.

Welcome to 2005. New ISP, same nickname, different server, same non-exit Tor configuration. Tor loved the dual opteron cpus. The difference in cpu load was dramatic. The load before was 40-50% cpu for "NumCPU 2" on the dual Xeons. On the dual Opterons, the load was 5-10%. Same non-exit config. Same version of Tor. Different hardware, newer version of the OS (Redhat 4 as opposed to CentOS 3). [**read more »**](https://blog.torproject.org/blog/five-years-exit-node-operator)
