---
layout: post
title: "Tor Weekly News — November 26th, 2014"
permalink: blog/tor-weekly-news-—-november-26th-2014
date: 2014-11-26 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the forty-seventh issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

A new Tor directory authority
=============================

Tor, being free software, can be used by anyone to set up their own anonymity network, as Tom Ritter [demonstrated last month](https://lists.torproject.org/pipermail/tor-dev/2014-October/007613.html); but “the Tor network” as we know it today consists of the 6500+ relays voted on by [nine](https://gitweb.torproject.org/tor.git/blob/HEAD:/src/or/config.c#l823) [“directory authorities”](https://www.torproject.org/docs/faq#KeyManagement) (or “dirauths”), operated by trusted members of the Tor development team and community.

As Mike Perry, a longtime directory authority operator, wished to retire his machine, “turtles”, without unbalancing the number of authorities producing the [consensus](https://metrics.torproject.org/about.html#consensus), a new authority named “[longclaw](https://en.wikipedia.org/wiki/Longclaw)” was brought online by the autonomous tech collective [Riseup](https://help.riseup.net/), which has been offering free and secure methods of communication (most of them now [available as hidden services](https://help.riseup.net/en/security/network-security/tor#riseups-tor-hidden-services)) since 1999.

Thanks to Riseup for playing this key role in the operation of the Tor network!

Miscellaneous news
==================

Nathan Freitas [announced](https://lists.mayfirst.org/pipermail/guardian-dev/2014-November/004068.html) the release of Orbot 14.1.3, which includes improved handling of background processes; it builds on the earlier [14.1.0](https://lists.mayfirst.org/pipermail/guardian-dev/2014-November/004036.html), which brought with it support for Android 5.0 Lollipop, as well as stability fixes. Orweb was brought up to version 0.7, also introducing support for the new Android release.

George Kadianakis [sent out](https://lists.torproject.org/pipermail/tor-dev/2014-November/007863.html) a co-authored draft of a proposal for statistics concerning hidden service activity that relays could collect and publish without harming the anonymity or security of users and hidden services, and which might “be useful to Tor developers and to people who want to understand hidden services and the onionspace better.”

Tom Ritter drafted a [proposal](https://lists.torproject.org/pipermail/tor-dev/2014-November/007853.html) exploring methods a hidden service operator might use to prove to certificate authorities that they control the service’s private key when requesting SSL certificates.

Karsten Loesing [spruced up](https://lists.torproject.org/pipermail/tor-dev/2014-November/007834.html) the documentation on the [Tor Metrics portal](https://metrics.torproject.org/), including a handy glossary of [frequently-used Tor-specific terms](https://metrics.torproject.org/about.html).

Damian Johnson sketched out a [roadmap](https://lists.torproject.org/pipermail/tor-dev/2014-November/007831.html) for further development of [Stem](https://stem.torproject.org/), the Tor controller library in Python, welcoming “more general ideas on directions to take Stem, the tor-prompt, and this whole space”.

Andrew Lewman [reported](https://lists.torproject.org/pipermail/tor-mirrors/2014-November/000781.html) on his experiments in mirroring the Tor Project website using the Fastly CDN as well as the BitTorrent Sync application.

Following a [suggestion](https://bugs.torproject.org/13703) that a guide to server hardening should be distributed with the tor software package, Libertas [drafted](https://lists.torproject.org/pipermail/tor-relays/2014-November/005846.html) a sample document and asked for reviews. “Please share any opinions or contributions you have. This was written in a little more than an hour, so it’s still a work in progress.”

Libertas also [scanned](https://lists.torproject.org/pipermail/tor-relays/2014-November/005759.html) a large number of currently-running Tor relays to check which ssh access authentication methods their servers supported, finding 2051 relays that still permitted password-based ssh authentication. “Generally, it is far more secure to allow only public key auth. The Ubuntu help pages have a good [guide](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) on setting up key-based auth”.

SiNA Rabbani [noted](https://lists.torproject.org/pipermail/tor-relays/2014-November/005806.html) that a large proportion of Tor exit relays are located in Europe, and called for relay operators to consider running nodes with US hosts. “I am not sure if the reason is lack of Tor-friendly ISPs or people are just too freaked out about the summer of Snowden. I think it’s very wrong to assume that EU countries are not part of the world-wide-wiretap, packets are going through a few internet exchanges anyways.”

Thanks to [Andy Weber](https://lists.torproject.org/pipermail/tor-mirrors/2014-October/000738.html), [Matt Kraai](https://lists.torproject.org/pipermail/tor-mirrors/2014-October/000741.html), [Alexander Dietrich](https://lists.torproject.org/pipermail/tor-mirrors/2014-October/000746.html), [James Murphy](https://lists.torproject.org/pipermail/tor-mirrors/2014-October/000751.html), [Jesse Victors](https://lists.torproject.org/pipermail/tor-mirrors/2014-November/000763.html), [Lucid Networks](https://lists.torproject.org/pipermail/tor-mirrors/2014-November/000783.html), [mirror-server.de](https://lists.torproject.org/pipermail/tor-mirrors/2014-November/000784.html), [NTU Open Source Society](https://lists.torproject.org/pipermail/tor-mirrors/2014-November/000762.html), and [Justaguy](https://lists.torproject.org/pipermail/tor-mirrors/2014-November/000764.html) for running mirrors of the Tor Project’s website and software!

Tor help desk roundup
=====================

The help desk commonly sees questions from users who get error messages when using Vidalia, the graphical Tor controller. Vidalia is unmaintained and many of its features simply do not work any more, so it has been [deprecated](https://www.torproject.org/docs/faq.html#WhereDidVidaliaGo). For web browsing, only the latest version of [Tor Browser](https://www.torproject.org/projects/torbrowser.html) should be used. If you were trying to use the (now also defunct) Vidalia Bridge or Relay Bundles, documentation for how to set up [bridges](https://www.torproject.org/projects/obfsproxy-instructions) and regular [relays](https://www.torproject.org/docs/tor-relay-debian) more effectively without Vidalia can be found on the website.

* * * * *

This issue of Tor Weekly News has been assembled by Harmony, Matt Pagan, Roger Dingledine, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
