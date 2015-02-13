---
layout: post
title: "Tor Weekly News — June 4th, 2014"
permalink: tor-weekly-news--june-4th-2014
date: 2014-06-04 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the twenty-second issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Tails moves to Wheezy
=====================

The [Tails live system](https://tails.boum.org/) is a [Debian derivative](https://wiki.debian.org/Derivatives) aiming at preserving the privacy and anonymity of its users.

The first Tails releases were based on Debian [Lenny](https://www.debian.org/releases/lenny/) (2009-2012); since version 0.7, Tails has been based on Debian [Squeeze](https://www.debian.org/releases/squeeze/) (2011-). Meanwhile, Debian has released a new stable version dubbed [Wheezy](https://www.debian.org/releases/wheezy/), and the upcoming Tails 1.1 will be the first release to be based on the latter.

The general set of features should not change much from the previous Tails release, but almost every software component has been updated. On  
 May 30th, the Tails team [released a beta image](https://tails.boum.org/news/test_1.1-beta1/); given the number of changes, testing is even more welcome than usual.

Testers can also try out the new UEFI support, which enables Tails to boot on recent hardware and on Macs.

[Several issues](https://tails.boum.org/news/test_1.1-beta1/#index3h1) with the current beta image have already been identified, so be sure to have a look at the list before [reporting](https://tails.boum.org/doc/first_steps/bug_reporting/).

The details of the release schedule are [still being discussed](https://mailman.boum.org/pipermail/tails-dev/2014-May/005917.html) at the time of writing, but Tails 1.1 is likely to be out by the end of July. Please help make it a great release!

Stem 1.2 brings interactive interaction with the Tor daemon
===========================================================

On June 1st, Damian Johnson [announced](https://blog.torproject.org/blog/stem-release-12) the release of [Stem](https://stem.torproject.org/) 1.2. Stem is a Python library for interacting with the Tor daemon. It is now used by [several applications](https://stem.torproject.org/tutorials/double_double_toil_and_trouble.html) like the [arm](https://www.atagar.com/arm/) status monitor and Philipp Winter’s [exit scanner](http://www.cs.kau.se/philwint/spoiled_onions/).

The new version brings an interactive control interpreter, “a new method for interacting with Tor’s control interface that combines an interactive python interpreter with raw access similar to telnet”. This should make Tor hackers happy by saving them from having to manually poke the control port through telnet or create complete Stem scripts.

For the complete list of changes, head over to the [changelog](https://stem.torproject.org/change_log.html#version-1-2).

Monthly status reports for May 2014
===================================

The wave of regular monthly reports from Tor project members for the month of May has begun. [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2014-May/000539.html) released their report first, followed by [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-May/000540.html), [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-June/000542.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-June/000543.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2014-June/000544.html), [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2014-June/000545.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2014-June/000546.html), [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2014-June/000548.html), and [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2014-June/000550.html).

Lunar also reported on behalf of the [help desk](https://lists.torproject.org/pipermail/tor-reports/2014-June/000541.html), while Arturo Filastò did likewise for the [OONI team](https://lists.torproject.org/pipermail/tor-reports/2014-June/000547.html), and Mike Perry for the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2014-June/000549.html).

Miscellaneous news
==================

Pups, a chat system implemented by Sherief Alaa for real-time invitation-based user support, has [gone live](https://bugs.torproject.org/11657), and can now be used by Tor’s support assistants when that method promises a quicker resolution of an issue.

In response to a question about the writing of unit tests for tor, Nick Mathewson [shared](https://lists.torproject.org/pipermail/tor-dev/2014-June/006933.html) a brief guide to identifying lines in tor’s codebase that have not yet been covered by tests.

Nick also put out a call ([relayed](https://lists.torproject.org/pipermail/tor-relays/2014-May/004617.html) by Moritz Bartl) for Tor relay operators running version 0.2.5.4-alpha or later to profile their relays, in order to identify potential bottlenecks. Basic instructions for doing so on Debian and Ubuntu can be found in the comments to the [relevant ticket](https://bugs.torproject.org/11332).

During a discussion on the role of JavaScript hooks in Tor Browser, Mike Perry [clarified](https://lists.torproject.org/pipermail/tbb-dev/2014-June/000074.html) the merits of writing direct C++ Firefox patches over using such hooks, as well as the possibility of incorporating Torbutton’s privacy features into either Firefox itself or a dedicated add-on.

Andrew Lewman [reported](https://lists.torproject.org/pipermail/tor-reports/2014-May/000538.html) on his trip to Stockholm to address Sida and the Stockholm Internet Forum.

Juha Nurmi sent the [second weekly report](https://lists.torproject.org/pipermail/tor-reports/2014-May/000537.html) for the ahmia.fi Google Summer of Code project .

Marc Juarez is working on website fingerprinting countermeasures in the form of a pluggable transport. Marc wants to “implement a set of primitives that any link padding-based defense would benefit of” and is [looking for feedback](https://lists.torproject.org/pipermail/tor-dev/2014-May/006918.html) on the envisaged primitives.

Philipp Winter [announced](https://lists.torproject.org/pipermail/tor-relays/2014-May/004620.html) that [Atlas](https://atlas.torproject.org), the web application to learn about currently running Tor relays, will now display information about a relay’s IPv6 exit policy, as well as the already-existing IPv4 exit summary.

Tor help desk roundup
=====================

Sometimes users with no network obstacles will email the help desk to ask how to configure their Tor Browser. Often these users will not need to configure anything, and clicking “Connect” is all that is necessary. Discussion on this problem is taking place on the [bug tracker](https://bugs.torproject.org/12164).

Easy development tasks to get involved with
===========================================

The [bridge distributor BridgeDB](https://bridges.torproject.org/) populates its database from the cached descriptor files copied over from the bridge authority. There’s a [small bug](https://bugs.torproject.org/11216) in BridgeDB where a line that is included in two different cached descriptor files gets added twice to the database. The ticket says this bug is easily reproducible and even contains commands for reproducing it. If you enjoy digging into unknown Python/Twisted codebases to find the few spots that need fixing, this bug may be for you. Be sure to comment on the ticket when you have a fix!

* * * * *

This issue of Tor Weekly News has been assembled by harmony, Lunar, Matt Pagan and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
