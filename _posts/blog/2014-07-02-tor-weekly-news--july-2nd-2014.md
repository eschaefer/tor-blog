---
layout: post
title: "Tor Weekly News — July 2nd, 2014"
permalink: tor-weekly-news--july-2nd-2014
date: 2014-07-02 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the twenty-sixth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Tor Weekly News turns one
=========================

The very [first issue](https://lists.torproject.org/pipermail/tor-talk/2013-July/028770.html) of [Tor Weekly News](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews) was released on July 3rd last year. Since then, we have been able to provide you news about the Tor community every week (except one).

Tor Weekly News is a community newsletter, so let’s all appreciate everyone who contributed so far: Andreas Jonsson, bastik, Colin, Damian Johnson, David Fifield, David Stainton, dope457, Georg Koppen, George Kadianakis, harmony, Jacob Appelbaum, Jesse Victors, Johannes Fürmann, Karsten Loesing, Kostas Jakeliūnas, Lunar, luttigdev, malaparte, Matt Pagan, Mike Perry, moskvax, murb, Nick Mathewson, Nicolas Vigier, nicoo, Nima, Paul Feitzinger, Peter Palfrader, Philipp Winter, Phoul, qbi, ra, rey, Roger Dingledine, Sandeep, sqrt2, the Tails developers, velope, whabib, Yawning, and several anonymous contributors.

[Join us](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team)! The Tor community is always growing and there are always interesting topics to report about!

2014 Summer Tor meeting
=======================

Dedicated Tor contributors are having a [five day meeting](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014SummerDevMeeting) this week in Paris. Expect less online activity while keyboards are put away in favor of unmediated human interactions.

[Pictures of post-it-note-based brainstorming sessions](https://people.torproject.org/~isis/2014-summer-tor-dev-meeting.postits.tar.xz) can already be seen online, and more minutes should be coming soon.

Unfortunately, due to several factors, there will be no widely open event around meeting this time.

Tails user experience experiments
=================================

Tails is experimenting on how to improve its user experience.

u. [reported on the first Tails UX experiments session](https://mailman.boum.org/pipermail/tails-dev/2014-June/006200.html). Five people attended, trying to realize three different missions: “create a new encrypted document of your choice […], and save it to Tails, using persistence”, “find out the number of Tails downloads this month, and pass on this information using GPG via email”, “find one or more images [… and] clean up these files to erase any metadata”.

Some of what has been learned by watching users has already been converted into concrete bugs and enhancement proposals. For the rest, read the detailed and insightful report!

In the meantime, the first dialog window that appears when using Tails — also known as “the greeter” — is being redesigned. A first round of test images is now [ready](https://mailman.boum.org/pipermail/tails-dev/2014-June/006194.html) for your feedback.

Monthly status reports for June 2014
====================================

While Kevin Dyer sent out his [report for May](https://lists.torproject.org/pipermail/tor-reports/2014-June/000565.html), the wave of regular monthly reports from Tor project members for the month of June has started. [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-June/000569.html) released his report first, followed by reports from [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2014-June/000570.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-June/000572.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2014-June/000573.html), and [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-June/000574.html).

Lunar reported [on behalf of the help desk](https://lists.torproject.org/pipermail/tor-reports/2014-July/000575.html).

Miscellaneous news
==================

Lunar [shared some highlights](https://lists.torproject.org/pipermail/tor-reports/2014-June/000568.html) on a trip to Calafou, near Barcelona, to attend [Backbone 409](http://backbone409.calafou.org/), an event for “projects actively building infrastructures for a free Internet from an anti-capitalist point of view”. Topics under discussion included hosting websites in the face of legal threats; secure operating systems; and the logistics of running a Torservers.net partner organization.

Juha Nurmi submitted a [status report for the ahmia.fi Google Summer of Code project](https://lists.torproject.org/pipermail/tor-reports/2014-June/000571.html).

Nusenu [warned](https://lists.torproject.org/pipermail/tor-talk/2014-June/033463.html) users of the Tor Project’s RPM repository that an updated package available in the official Fedora repo will cause their tor to stop working, and set out two ways in which they can solve the problem.

starlight [gave an account](https://lists.torproject.org/pipermail/tor-relays/2014-June/004821.html) of their experience running a tor relay using versions of OpenSSL and libevent that had been hardened with AddressSanitizer.

While the [fteproxy](https://fteproxy.org/) pluggable transport has been integrated into the Tor Browser, documentation on how to setup bridges was lacking. A problem fixed by Colin who took the time to document [how to setup FTE bridges](https://trac.torproject.org/projects/tor/wiki/doc/fte/setup).

George Kadianakis gave an [insightful answer](https://lists.torproject.org/pipermail/tor-relays/2014-June/004823.html) to Rick Huebneron’s questions about the status of the “UpdateBridgesFromAuthority” feature. The latter should allow bridge users to automatically update the IP address of their bridge when it changes. But the feature is currently turned off by default as several problems are currently preventing it to be useful. Have a look at George’s summary if you want to scratch that itch.

Tor help desk roundup
=====================

The help desk has been asked about the “ethics” behind Tor. Tor’s technical design decisions are laid out in [the various design documents](https://gitweb.torproject.org/torspec.git), but to understand the social and cultural motivations for the Tor Project, videos like [Roger’s talk at Internet Days](https://media.torproject.org/video/tor-internet-days-2010.mp4), or Jake and Roger’s talks at the Chaos Communications Congress [in 2011](https://media.torproject.org/video/28c3-4800-en-how_governments_have_tried_to_block_tor_h264.mp4) and [2013](https://media.torproject.org/video/30C3_-_5423_-_en_-_saal_1_-_201312272030_-_the_tor_network_-_jacob_-_arma_concat_.mp4) are good resources.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, and Rob Jansen.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
