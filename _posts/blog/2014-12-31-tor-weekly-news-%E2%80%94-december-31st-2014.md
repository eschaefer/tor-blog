---
layout: post
title: "Tor Weekly News — December 31st, 2014"
permalink: tor-weekly-news-—-december-31st-2014
date: 2014-12-31 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the final issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Attacks and rumors of attacks
=============================

Two weeks ago, the Tor Project relayed a [warning](https://blog.torproject.org/blog/possible-upcoming-attempts-disable-tor-network) from an unspecified source to the effect that someone may have been preparing to seize, attack, or otherwise disable one or more of Tor’s [directory authorities](https://metrics.torproject.org/about.html#directory-authority) in a bid to disrupt the entire Tor network. The lack of any specific information about the threat caused understandable concern in the Tor community, and several events that followed over the next fortnight did little to dispel this.

First, the operator of a large Tor exit relay cluster [reported](https://lists.torproject.org/pipermail/tor-talk/2014-December/036067.html) that his servers may have been physically interfered with by unknown parties a short while before his message. Later [updates](https://lists.torproject.org/pipermail/tor-talk/2014-December/036084.html) suggested that foul play was less likely than initially thought.

Several days later, a large number of small exit relays were created all at once, in what appeared to be a “[Sybil attack](https://en.wikipedia.org/wiki/Sybil_attack)”; this was [detected](https://lists.torproject.org/pipermail/tor-consensus-health/2014-December/005381.html) and halted almost immediately, as was a [second, more recent incident](https://lists.torproject.org/pipermail/tor-consensus-health/2014-December/005414.html). As the Tor Project put it in a [response](http://www.twitlonger.com/show/n_1sjg365), “we don’t expect any anonymity or performance effects based on what we've seen so far”, although a side-effect of the countermeasure is that relays hosted on some IP ranges are currently being [rejected](https://lists.torproject.org/pipermail/tor-relays/2014-December/006020.html) by dirauths.

As far as anyone can tell, these events are not related in any way to the initial warning. The Tor network has functioned normally throughout this period, and the appearance of a series of incidents is likely to be the result of coincidence (helped by the online rumor mill) rather than a coordinated campaign. It is never possible to say with certainty that attacks on the network will not occur, but the threat referred to in the original blog post has not yet materialized — and “no news is good news”.

Miscellaneous news
==================

Lasse Øverlier discovered that [ScrambleSuit](http://www.cs.kau.se/philwint/scramblesuit/)’s protection against “replay attacks”, in which an adversary repeats a client authentication event to learn that the server is in fact a ScrambleSuit bridge, doesn’t work. Philipp Winter [explained](https://lists.torproject.org/pipermail/tor-dev/2014-December/008019.html) the issue, and suggested some simple fixes.

Tom van der Woerdt asked for [review](https://lists.torproject.org/pipermail/tor-dev/2014-December/008023.html) of a [patch](https://github.com/TvdW/tor/commit/75b5d94eb976ee4998189dc69582c62511dde9eb) to remove the obsolete version 1 of Tor’s link protocol from the current software: “It’s a rather large patch, though not as large as the patch that will remove v2 of the protocol. However, before I write that one, can someone please check whether my patch is sane and I’m not violating any standards or policies?”

David Fifield [trimmed](https://bugs.torproject.org/12778#comment:5) the length of [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek)’s HTTP headers from 413 to 162 bytes, reducing the bandwidth it uses by “approximately” 3%.

Thanks to [Kura](https://lists.torproject.org/pipermail/tor-mirrors/2014-December/000815.html) for running a mirror of the Tor Project website and software archive!

* * * * *

This issue of Tor Weekly News has been assembled by Harmony, David Fifield, Chuck Peters, and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
