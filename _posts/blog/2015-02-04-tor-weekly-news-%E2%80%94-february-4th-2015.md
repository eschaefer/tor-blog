---
layout: post
title: "Tor Weekly News — February 4th, 2015"
permalink: tor-weekly-news-—-february-4th-2015
date: 2015-02-04
author: harmony
category: blog
tags: ["tor weekly news"]
---

Welcome to the fifth issue in 2015 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Mozilla’s Tor relays go live
============================

Late last year, Mozilla [announced](https://lists.torproject.org/pipermail/tor-news/2014-November/000071.html) its partnership with the Tor Project in the [Polaris Privacy Initiative](https://blog.mozilla.org/privacy/2014/11/10/introducing-polaris-privacy-initiative-to-accelerate-user-focused-privacy-online/), a program aimed at “giving users more control, awareness and protection in their Web experiences”. One of the two Tor-related “experiments” Mozilla planned to carry out was the operation of several high-capacity middle relays, and last week Mozilla’s Network Engineering team announced that the [new nodes](https://globe.torproject.org/#/search/query=mozilla) had been running for several weeks, in a [blog post](https://blog.mozilla.org/it/2015/01/28/deploying-tor-relays/) that explores the technical decisions and challenges they faced in setting them up.

The team discussed the hardware and infrastructure chosen for the relays, configuration management using Ansible (publishing their [playbook](https://github.com/XioNoX/moz-tor-relays/) at the same time), and security practices, as well as announcing their intention to continue posting about their experiences and findings during the experiment.

Thanks to Mozilla for this contribution to the Tor network!

Monthly status reports for January 2015
=======================================

The wave of regular monthly reports from Tor project members for the month of January has begun. [Juha Nurmi](https://lists.torproject.org/pipermail/tor-reports/2015-January/000748.html) released his report first, followed by reports from [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2015-January/000749.html), [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2015-February/000750.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2015-February/000751.html), [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2015-February/000752.html), and [David Goulet](https://lists.torproject.org/pipermail/tor-reports/2015-February/000753.html).

Miscellaneous news
==================

meejah [announced](https://lists.torproject.org/pipermail/tor-dev/2015-February/008227.html) version 0.12.0 of txtorcon, the Tor controller client in Twisted; please see the announcement for a full list of improvements.

Nick Mathewson submitted a draft of [proposal 241](https://lists.torproject.org/pipermail/tor-dev/2015-February/008223.html), which aims to protect users against adversaries who are able to attack their connectivity to the Tor network and force them to use malicious guard nodes. Roger Dingledine [offered](https://lists.torproject.org/pipermail/tor-dev/2015-February/008226.html) some further thoughts.

Nick also set out the schedule for the Tor 0.2.6 [feature freeze](https://lists.torproject.org/pipermail/tor-dev/2015-January/008216.html).

After reports from users that Tor Browser’s default obfs4 bridges are no longer usable in China, David Fifield [estimated](https://lists.torproject.org/pipermail/tor-dev/2015-February/008222.html) the time it takes for the “Great Firewall” to react to new circumvention systems as lying “between 2 and 10 weeks”, and asked for additional data to narrow the range further.

Isis Lovecruft “would be super stoked if we could make it as easy and seamless as possible for the bridge operators who are still running obfs2 (!!) to move to supporting better, newer pluggable transports”, such as obfs4, and [wondered](https://lists.torproject.org/pipermail/tor-relays/2015-February/006346.html) how to make it possible for operators running Debian stable to get the necessary dependencies onto their system without extensive backporting: “If someone has done this, or has another simple solution, would you mind writing up some short how-to on the steps you took, please?”

The Tails team continued to [discuss](https://mailman.boum.org/pipermail/tails-dev/2015-February/008003.html) the advantages and disadvantages of removing AdBlock Plus from Tails’ version of Tor Browser.

Sadia Afroz compiled a timeline of Tor blocking events, and [shared](https://lists.torproject.org/pipermail/ooni-dev/2015-February/000241.html) it with the ooni-dev mailing list, along with a request for missing data points; Collin Anderson [responded](https://lists.torproject.org/pipermail/ooni-dev/2015-February/000242.html) with some additional information.

Patrick Schleizer [announced](https://lists.torproject.org/pipermail/tor-talk/2015-February/036675.html) that the Whonix team is looking for “a sponsor who is willing to donate a suitable sized virtual or root server”, and gave a list of planned requirements. If you can meet this need, please see Patrick’s message for next steps.

Konstantin Müller [shared](https://lists.torproject.org/pipermail/tor-talk/2015-February/036709.html) a report written as part of a Master’s degree, offering an introduction to “the past, present, and future” of Tor hidden services.

News from Tor StackExchange
===========================

Windy wanted to know [how often a client fetches consensus data from a directory server](https://tor.stackexchange.com/q/6087/88). Jens Kubieziel provided some information by walking through the source code, and concluded: “every minute it is checked if the consensus document is too old. If it is older than the current time a new one will be fetched.”

* * * * *

This issue of Tor Weekly News has been assembled by qbi and Harmony.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the project page [](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the team mailing list [](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
