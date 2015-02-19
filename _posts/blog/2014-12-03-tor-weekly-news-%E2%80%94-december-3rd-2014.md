---
layout: post
title: "Tor Weekly News — December 3rd, 2014"
permalink: blog/tor-weekly-news-—-december-3rd-2014
date: 2014-12-03 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the forty-eighth issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

GetTor is back
==============

Some Tor users need to access the Internet from networks so heavily censored that they cannot reach the Tor Project website, or any of its mirrors, to download Tor in the first place; with these users in mind, [GetTor](https://www.torproject.org/projects/gettor), an alternative software distribution system for Tor Browser, was created.

After a period of neglect, GetTor has been revamped and redeployed: users can now email the name of their operating system to [gettor@torproject.org](mailto:gettor@torproject.org), and in return they will receive Dropbox download links for the latest Tor Browser and the package signature, as well as a checksum and the fingerprint of the key used to make the signature.

The lead developer on this project is Israel Leiva, who did most of the work on it during this year’s Google Summer of Code. Israel took to the [Tor blog](https://blog.torproject.org/blog/say-hi-new-gettor) to explain the background and outcome of the redevelopment work; please see that post for more information, or put GetTor to the test yourself and send your comments to the community!

Monthly status reports for November 2014
========================================

The wave of regular monthly reports from Tor project members for the month of November has begun. [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-November/000698.html) released his report first, followed by reports from [Juha Nurmi](https://lists.torproject.org/pipermail/tor-reports/2014-November/000699.html), [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-November/000701.html), [David Goulet](https://lists.torproject.org/pipermail/tor-reports/2014-November/000702.html), [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2014-November/000703.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-December/000704.html), [Tom Ritter](https://lists.torproject.org/pipermail/tor-reports/2014-December/000705.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-December/000706.html), [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2014-December/000708.html), [Griffin Boyce](https://lists.torproject.org/pipermail/tor-reports/2014-December/000709.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2014-December/000710.html), Andrew Lewman (for both [October](https://lists.torproject.org/pipermail/tor-reports/2014-December/000712.html) and [November](https://lists.torproject.org/pipermail/tor-reports/2014-December/000713.html)), [Noel Torres](https://lists.torproject.org/pipermail/tor-reports/2014-December/000714.html), and [Harmony](https://lists.torproject.org/pipermail/tor-reports/2014-December/000717.html).

George Kadianakis also sent out the [SponsorR report](https://lists.torproject.org/pipermail/tor-reports/2014-November/000700.html), while Colin C. reported on behalf of the [help desk](https://lists.torproject.org/pipermail/tor-reports/2014-December/000711.html), and Mike Perry for the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2014-December/000716.html).

Miscellaneous news
==================

Nathan Freitas [announced](https://lists.mayfirst.org/pipermail/guardian-dev/2014-November/004080.html) version 14.1.4 of Orbot, the Tor client for Android, which brings with it further improvements to background service operation, as well as theme and layout tweaks.

After much back-and-forth, work by Andrea Shepard to make Tor’s cell scheduling mechanism more efficient was finally [merged](https://bugs.torproject.org/9262). Although performance is not yet affected, these changes could form the basis of other improvements to managing congestion caused by “mismanaged socket output” in the Tor network, as discussed by Jansen et al. in “[Never Been KIST](http://www.robgjansen.com/publications/kist-sec2014.pdf)”.

Following a discussion with David Goulet, Nick Mathewson posted a [draft proposal](https://lists.torproject.org/pipermail/tor-dev/2014-December/007898.html) of possible improvements to integration testing for Tor.

Sebastian Hahn [informed](https://lists.torproject.org/pipermail/tor-dev/2014-November/007892.html) users of the Tor Project’s git repositories that cloning via the unauthenticated git:// protocol is no longer supported — secure https:// access has been and still is the preferred method for retrieving code.

Gareth Owen started a [discussion](https://lists.torproject.org/pipermail/tor-dev/2014-November/007870.html) of suspicious relay behaviors that automated Tor network tests could scan for, in addition to those that are already monitored.

Tor help desk roundup
=====================

The help desk has been asked how to set up a relay on a Windows laptop. We don’t recommend running a relay on a laptop: the relays that are most useful to the network have faster bandwidth than most home internet connections can offer. Relays also need to have as much uptime as possible, and a laptop that gets put to sleep and woken up once a week or more is not a good computing environment for a relay that should serve the network in a consistent way.

We are not able to provide much help to users who report errors when using any of the Vidalia bundles, as Vidalia is no longer maintained.

* * * * *

This issue of Tor Weekly News has been assembled by Matt Pagan, Nick Mathewson, Roger Dingledine, and Harmony.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
