---
layout: post
title: "Tor Weekly News — August 13th, 2014"
permalink: tor-weekly-news--august-13th-2014
date: 2014-08-13 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the thirty-second issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Torsocks 2.0 is now considered stable
=====================================

[Torsocks](https://gitweb.torproject.org/torsocks.git/blob/HEAD:/README.md) is a wrapper program that will force an application’s network connections to go through the Tor network. David Goulet [released](https://lists.torproject.org/pipermail/tor-dev/2014-August/007330.html) version 2.0.0, blessing the new codebase as stable after [more than a year of efforts](https://lists.torproject.org/pipermail/tor-dev/2013-June/004959.html).

David’s original email highlighted several reasons for a complete rewrite of torsocks. Among the issues were maintainability, error handling, thread safety, and a lack of proper compatibility layer for multiple architectures. The new implementation addresses all these issues while staying about the same size as the previous version (4,000 lines of C according to sloccount), and test coverage has been vastly extended.

Torsocks comes in handy when a piece of software does not natively support the use of a SOCKS proxy. In most cases, the new version may be safer, as torsocks will prevent DNS requests and non-torified connections from happening.

Integrators and power users should watch their steps while migrating to the new version. The configuration file format has changed, and some applications might behave differently as more system calls are now restricted.

Next generation Hidden Services and Introduction Points
=======================================================

When Tor clients need to connect to a Hidden Service, the first step is to create a circuit to its “Introduction Point”. There, the Tor client serving the Hidden Service will be waiting through another circuit to agree on a “Rendezvous Point” and pursue the communication through circuits connecting to this freshly selected Tor node.

This general design is not subject to any changes in the [revision of hidden services](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/224-rend-spec-ng.txt) currently being worked on. But there are still some questions left unanswered regarding the best way to select Introduction Points. George Kadianakis [summarized](https://lists.torproject.org/pipermail/tor-dev/2014-August/007335.html) them as: “How many IPs should an HS have? Which relays can be IPs? What’s the lifetime of an IP?”

For each of these questions, George collected possible answers and assessed whether or not they could respond to several attacks identified in the past. Anyone interested should help with the research needed and join the discussion.

In the meantime, Michael Rogers is also trying to [find ways](https://fulpool.org/pipermail/hidden-services/2014-August/000019.html) to improve hidden service performance in mobile contexts. One way to do so would be to “keep the set of introduction points as stable as possible”. However, a naive approach to doing so would ease the job of attackers trying to locate a hidden service. The idea would be to always use the same guard and middle node for a given introduction point, but this might also open the doors to new attacks. Michael suggests experimenting with the recently published [Java research framework](https://github.com/drgowen/tor-research-framework) to gain a better understanding of the implications.

More status reports for July 2014
=================================

The wave of regular monthly reports from Tor project members for the month of July continued, with submissions from [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2014-August/000615.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2014-August/000616.html), and [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-August/000617.html).

Roger Dingledine sent out the report for [SponsorF](https://lists.torproject.org/pipermail/tor-reports/2014-August/000619.html). Arturo Filastò described what the [OONI team](https://lists.torproject.org/pipermail/tor-reports/2014-August/000621.html) was up to. The [Tails team](https://tails.boum.org/news/report_2014_06-07/) covered their activity for June and July.

Miscellaneous news
==================

Two Tor Browser releases are at QA stage: [4.0-alpha-1](https://lists.torproject.org/pipermail/tor-qa/2014-August/000436.html) including meek and a new directory layout, and [3.6.4](https://lists.torproject.org/pipermail/tor-qa/2014-August/000439.html) for security fixes.

The recent serious [attack against Tor hidden services](https://blog.torproject.org/blog/tor-security-advisory-relay-early-traffic-confirmation-attack) was also a Sybil attack: a large number of malicious nodes joined the network at once. This led to a renewal of interest in detecting Sybil attacks against the Tor network more quickly. Karsten Loesing published [some code](https://github.com/kloesing/SAD) computing similarity metrics, and David Fifield has explored [visualizations](https://bugs.torproject.org/12813) of the consensus that made the recent attack visible.

Gareth Owen sent out an [update](https://lists.torproject.org/pipermail/tor-dev/2014-August/007328.html) about the Java Tor Research Framework. This prompted a discussion with George Kadianakis and Tim about the best way to perform [fuzz testing](https://en.wikipedia.org/wiki/Fuzz_testing) on Tor. Have a look if you want to comment on [Tim’s approaches](https://lists.torproject.org/pipermail/tor-dev/2014-August/007334.html).

Thanks to [Daniel Thill](https://lists.torproject.org/pipermail/tor-mirrors/2014-August/000651.html) for running a mirror of the Tor Project website!

ban [mentioned](https://lists.torproject.org/pipermail/tor-relays/2014-August/005073.html) a new service collecting donations for the Tor network. [OnionTip](https://oniontip.com/), set up by Donncha O’Cearbhaill, will collect bitcoins and redistribute them to relay operators who put a bitcoin address in their contact information. As the redistribution is currently done according to the consensus weight, Sebastian Hahn [warned](https://lists.torproject.org/pipermail/tor-relays/2014-August/005077.html) that this might encourage people to “cheat the consensus weight” because that now means “more money from oniontip”.

Juha Nurmi sent [another update](https://lists.torproject.org/pipermail/tor-reports/2014-August/000620.html) on the ahmia.fi GSoC project.

News from Tor StackExchange
===========================

arvee wants to [redirect some TCP connections through Tor on OS X](https://tor.stackexchange.com/q/3802/88); [Redsocks](http://darkk.net.ru/redsocks/) should help to route packets for port 443 over Tor . mirimir explained that given the user's pf configuration, the setting “SocksPort 8888” was probably missing.

meee asked a question and offered a bounty for an answer: the circuit handshake entry in Tor’s log file contains some numbers, and meee wants to [know what their meaning is](https://tor.stackexchange.com/q/3213/88): “Circuit handshake stats since last time: 1833867/1833868 TAP, 159257/159257 NTor.”

Easy development tasks to get involved with
===========================================

The bridge distributor [BridgeDB](https://bridges.torproject.org/) usually gives out bridges by responding to user requests via HTTPS and email. A while ago, BridgeDB also gave out bridges to a very small number of people who would then redistribute bridges using their social network. We would like to resume sending bridges to these people, but only if BridgeDB can be [made to send them via GnuPG-encrypted emails](https://bugs.torproject.org/9332). If you’d like to dive into the BridgeDB code and add support for GnuPG-encrypted emails, please take a look at the ticket and give it a try.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, qbi, Karsten Loesing, harmony, and Philipp Winter.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
