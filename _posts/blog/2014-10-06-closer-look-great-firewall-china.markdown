---
layout: post
title: "A closer look at the Great Firewall of China"
permalink: closer-look-great-firewall-china
date: 2014-10-06
author: phw
category: blog
tags: ["censorship", "censorship circumvention", "dpi", "GFW"]
---

Over the last years, we learned a lot about how the Great Firewall of China [is](https://blog.torproject.org/blog/knock-knock-knockin-bridges-doors) [blocking](http://www.cs.kau.se/philwint/gfw/) [Tor](http://arxiv.org/pdf/1312.5739v1.pdf). Some questions remained unanswered, however. Roya, Mueen, Jed, and I just published a [project](http://www.cs.unm.edu/~royaen/gfw/) which seeks to answer some of these open questions. Being curious as we are, we tried to find answers to the following questions:

- Is the filtering decentralised (i.e., happening in provinces) or centralised (i.e., happening in Internet exchange points (IXP))?
- Are there any temporal patterns in the filtering? Or in other words, are there certain times when people are more likely to be able to connect to Tor?
- Similarly, are there any spatial patterns? Are folks in some special regions of China able to connect to Tor while others cannot?
- When a computer in China tries to connect to a Tor relay, what part of the TCP handshake is blocked?

It turns out that some of these questions are quite tricky to answer. For example, to find spatial patterns, we need to be able to measure the connectivity between _many_ Tor relays and _many_ clients in China. However, we are not able to control _even a single_ one of these machines. So how do we proceed from here? As so often, side channels come to the rescue! In particular, we made use of two neat network measurement side channels which are the [hybrid idle scan](http://arxiv.org/pdf/1312.5739v1.pdf) and the SYN backlog scan. The backlog scan is a new side channel we discovered and discuss in our paper. Equipped with these two powerful techniques, we were able to infer if there is packet loss between relay A and client B even though we cannot control A and B.

You might notice that our measurement techniques are quite different from most other Internet censorship studies which rely on machines inside the censoring country. While our techniques give us a lot more geographical coverage, they come at a price which is flexibility; we are limited to measuring Internet filtering on the IP layer. More sophisticated filtering techniques such as deep packet inspection remain outside our scope.

Now what we did was to measure the connectivity between several dozen Tor relays and computers in China over four weeks which means that we collected plenty of data points, each of which telling us "was A able to talk to B at time T?". These data points reveal a number of interesting things:

- It appears that many IP addresses inside the China Education and Research Network (CERNET) are able to connect to at least our Tor relay.
- Apart from the CERNET netblock, the filtering seems to be quite effective despite occasional country-wide downtimes.
- It seems like the filtering is centralised at the IXP level instead of being decentralised at the provincial level. That makes sense from the censor's point of view because it is cheap, effective, and easy to control.

Now what does all of this mean for Tor users? Our results show that China still has a tight grip on its communication infrastructure, especially on the IP and TCP layer. That is why our circumvention efforts mostly focus on the application layer (with [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek) being an exception) and pluggable transport protocols such as [ScrambleSuit](http://www.cs.kau.se/philwint/scramblesuit/) (which is now part of the experimental version of [TorBrowser](https://www.torproject.org/projects/torbrowser.html.en#downloads-alpha)) and [obfs4](https://gitweb.torproject.org/pluggable-transports/obfs4.git) are specifically designed to thwart the firewall's [active probing attacks](http://www.cs.kau.se/philwint/gfw/).

