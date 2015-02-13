---
layout: post
title: "Tor Weekly News — December 11th, 2013"
permalink: tor-weekly-news--december-11th-2013
date: 2013-12-11 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the twenty-fourth issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Introducing a new Lead Automation Engineer
==========================================

The Tor Project welcomed a new member, Nicolas Vigier, in the role of Lead Automation Engineer. He swiftly got down to business by [putting out a call](https://lists.torproject.org/pipermail/tor-dev/2013-December/005906.html) for automation-related feedback “from developers of any tor components”, promising a summary of “the current status regarding build, packaging, testing, and what should be done” to improve the automated processes involved in Tor development, as well as “some proposals and a general plan for the work to be done during the coming months”, an [early version of which is already online](https://people.torproject.org/~boklm/automation/tor-automation-review.html). A warm welcome to him!

Freedom of the Press Foundation launch a support campaign for Tor
=================================================================

In his [report for November](https://lists.torproject.org/pipermail/tor-reports/2013-December/000396.html), Roger Dingledine wrote: “We've also been pondering lately how to do a fundraising or donations drive, to help move us off our reliance on government funders.” The good news is that Tor has many supporters.

The Freedom of the Press Foundation just started [a campaign to support encryption tools for journalists](https://pressfreedomfoundation.org/blog/2013/12/freedom-press-foundation-launches-campaign-support-encryption-tools-journalists) that is going to last for two months. The campaign is gathering funds for Tor core development work, the [Tails live system](https://tails.boum.org/), the encrypted mobile communication tools [RedPhone and TextSecure](https://whispersystems.org/), and the encrypted email platform [LEAP](https://leap.se/).

[Spread the word](https://pressfreedomfoundation.org/) and help make the campaign a success. Direct [donations to The Tor Project](https://www.torproject.org/donate/) are also always possible.

More monthly status reports for November 2013
=============================================

The wave of regular monthly reports from Tor project members for the month of November continued, with reports from [Roger Dingledine](https://lists.torproject.org/pipermail/tor-reports/2013-December/000396.html), [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2013-December/000397.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2013-December/000398.html), [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2013-December/000399.html), [Nicolas Vigier](https://lists.torproject.org/pipermail/tor-reports/2013-December/000400.html) [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2013-December/000401.html), [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2013-December/000402.html), and [Noel David Torres Taño ](https://lists.torproject.org/pipermail/tor-reports/2013-December/000403.html).

Miscellaneous news
==================

David Fifield has produced [updated “pluggable transport bundles”](https://blog.torproject.org/blog/pluggable-transports-bundles-2418-rc-1-pt1-and-2418-rc-2-pt1-firefox-17011esr) based on the 2.4.18 browser bundles. Be sure to upgrade!

David also [announced](https://lists.torproject.org/pipermail/tor-dev/2013-December/005913.html) great progress in integrating our current set of pluggable transports within the new Tor Browser 3 build infrastructure.

Thanks to Himanshu from India, Andrew Lewman was able to [deploy a new script](https://lists.torproject.org/pipermail/tor-mirrors/2013-December/000394.html) to list [mirrors of the Tor Project's website](https://www.torproject.org/getinvolved/mirrors.html.en). The new code will ensure that mirrored files are “100% the same as those on torproject.org (hashing, pgp signatures, etc)” and will remove and re-instate mirrors accordingly.

Thanks [BarkerJr](https://lists.torproject.org/pipermail/tor-mirrors/2013-October/000381.html), [DevRandom](https://lists.torproject.org/pipermail/tor-mirrors/2013-November/000384.html), and [Userzap](https://lists.torproject.org/pipermail/tor-mirrors/2013-November/000389.html) for setting up new mirrors!

Nathan Freitas [announced that Orfox was going to replace Orweb](https://lists.torproject.org/pipermail/tor-talk/2013-December/031331.html) in the Guardian Project set of secure communication tools. Orfox is based on the Firefox engine and is likely to behave more like the Tor Browser. “However, Orfox is still very early (not alpha yet) and has not been fully tested. I would either do your own testing and report back to us, or only use the app for non sensitive/critical browsing for now”, Nathan [added](https://lists.torproject.org/pipermail/tor-talk/2013-December/031340.html).

arkmd [reported](https://lists.torproject.org/pipermail/tor-dev/2013-December/005901.html) that TorBirdy was saving unencrypted drafts on the remote server on their system. Sukhbir Singh has [not been able to reproduce the issue so far](https://bugs.torproject.org/10309#comment:4) but he is thinking of [disabling the automatic save feature entirely](https://lists.torproject.org/pipermail/tor-dev/2013-December/005903.html).

Christian [announced](https://lists.torproject.org/pipermail/tor-talk/2013-December/031353.html) that Globe is “now officially hosted on the torproject servers”. Credits to Karsten Loesing and Peter Palfrader for setting up the infrastructure. Have a look at this [new Tor relay and bridge explorer](https://globe.torproject.org/)!

ghostmaker [advertised](https://lists.torproject.org/pipermail/tor-dev/2013-December/005908.html) “a small new tool for Windows called InjectSOCKS that can force other Windows software to do TCP connections via SOCKS.” InjectSOCKS source code and binaries are available from [the project page](http://sourceforge.net/projects/injectsocks).

The Tails team has issued a [call for testing regarding incremental upgrades](https://tails.boum.org/news/test_incremental_upgrades/) — one more step on the path to providing Tails users with easy upgrades.

The [release schedule for Tails 0.22.1](https://mailman.boum.org/pipermail/tails-dev/2013-December/004405.html) has been published by intrigeri. The expected release date for this point release is January 21th.

Tor help desk roundup
=====================

Multiple users have asked the help desk specifically for assistance with IPv6 bridges. Currently getting IPv6 bridges is not too easy, but the [issue is known](https://bugs.torproject.org/9127) and should be solved as the bridge distributor is improved. IPv6 bridges are functional in (at least part of) China, but we do not have many of them to distribute. Please set up an IPv6 bridge if you can: it's only [one “ORPort” line to add](https://people.torproject.org/~linus/ipv6-relay-howto.html) to the [usual configuration](https://www.torproject.org/docs/bridges.html.en#RunningABridge).

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, dope457, Matt Pagan, Roger Dingledine and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
