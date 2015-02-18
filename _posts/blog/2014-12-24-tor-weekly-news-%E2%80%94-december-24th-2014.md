---
layout: post
title: "Tor Weekly News — December 24th, 2014"
permalink: tor-weekly-news-—-december-24th-2014
date: 2014-12-24 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the fifty-first issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Stem 1.3 is out
===============

“After months down in the engine room”, Damian Johnson [announced](https://blog.torproject.org/blog/stem-release-13) version 1.3 of [Stem](https://stem.torproject.org/), the Tor controller library written in Python. Among the many improvements in this release, Damian singled out the new set of controller methods for working with hidden services, as well as the 40% increase in descriptor parsing speed.

Please see the [changelog](https://stem.torproject.org/change_log.html#version-1-3) for full details of all the new features.

Miscellaneous news
==================

The team of researchers working on the collection of [hidden service statistics](https://bugs.torproject.org/13509) asked relay operators for help by enabling these statistics on their relays in the coming days and weeks. They included a step-by-step [tutorial](https://lists.torproject.org/pipermail/tor-relays/2014-December/005953.html) for enabling this feature, which has recently been merged into Tor’s main branch.

Building on Andrea Shepard’s recently-merged work on [global cell scheduling](https://bugs.torproject.org/9262), Nick Mathewson [announced](https://lists.torproject.org/pipermail/tor-dev/2014-December/008001.html) that the KIST socket management algorithm proposed [earlier this year](http://www.robgjansen.com/publications/kist-sec2014.pdf) to reduce congestion in the Tor network is now “somewhat implemented” for Linux. You can follow the testing and reviews on the associated [ticket](https://bugs.torproject.org/12890).

Nick also asked for [feedback](https://lists.torproject.org/pipermail/tor-dev/2014-December/008007.html) on the proposal to increase the interval at which Tor relays report their bandwidth usage statistics from fifteen minutes to four hours [](https://bugs.torproject.org/13988): “Will this break anything you know about?”

Moritz Bartl [invited](https://lists.torproject.org/pipermail/tor-relays/2014-December/005958.html) Tor relay operators to a [meet-up](https://events.ccc.de/congress/2014/wiki/Session:Tor_Relay_Operators_Meetup) at the upcoming Chaos Communication Congress in Hamburg: “We will do quick presentations on recent and future activities around Torservers.net, talk about events relevant to the Tor relay community, and what lies ahead.”

Thanks to Thomas White for keeping the community [updated](https://lists.torproject.org/pipermail/tor-talk/2014-December/036067.html) following a brief period of suspicious activity around his exit relays and Onionoo application mirrors!

This week in Tor history
========================

[A year ago this week](https://lists.torproject.org/pipermail/tor-news/2013-December/000026.html), Tor Browser hit version 3.5, bringing with it a pioneering [deterministic build system](https://blog.torproject.org/blog/deterministic-builds-part-one-cyberwar-and-global-compromise) that set a new standard in software distribution security, and has since drawn interest from many other projects, including the [Debian operating system](https://wiki.debian.org/ReproducibleBuilds). It also laid the long-obsolete Vidalia graphical controller to rest, replacing it with the faster, sleeker Tor Launcher. The privacy-preserving browser is now approaching version 4.5, and users can look forward to a [security slider](https://bugs.torproject.org/9387) offering finer-grained tuning of security preferences, as well as features that restore some of Vidalia’s [circuit-visualization capabilities](https://bugs.torproject.org/8641).

* * * * *

This issue of Tor Weekly News has been assembled by Harmony and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
