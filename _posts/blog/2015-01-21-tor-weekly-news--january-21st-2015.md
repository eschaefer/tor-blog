---
layout: post
title: "Tor Weekly News — January 21st, 2015"
permalink: tor-weekly-news--january-21st-2015
date: 2015-01-21 07:00:00
author: harmony
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the third issue in 2015 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the [boring](https://guardianproject.info/2015/01/02/2015-is-the-year-of-bore-sec/) Tor community.

Tor Browser 4.0.3 and 4.5a3 are out
===================================

Georg Koppen announced two new releases by the Tor Browser team. [Version 4.0.3](https://blog.torproject.org/blog/tor-browser-403-released) of the privacy-preserving browser is based on Firefox 31.4.0esr, and also contains updates to NoScript, meek, and Tor Launcher.

The [third release in the 4.5-alpha series](https://blog.torproject.org/blog/tor-browser-45a3-released) allows the secure in-browser update mechanism to handle signed update files, and will reject unsigned ones from now on. It also restores functionality for meek, which was broken in previous 4.5-alpha releases, and offers other improvements and bugfixes — please see Georg’s announcement for the full changelog.

These releases contain important security updates, so users of both the stable and alpha series should upgrade as soon as possible. Furthermore, Tor Browser 4.5a3 is signed by a new Tor Browser Developers signing key rather than the personal key of an individual developer. If you want to verify your download of the new alpha (and you should!), you will need to retrieve the new key (fingerprint EF6E 286D DA85 EA2A 4BA7 DE68 4E2C 6E87 9329 8290) from a keyserver before doing so.

Miscellaneous news
==================

Anthony G. Basile [announced](https://lists.torproject.org/pipermail/tor-talk/2015-January/036526.html) version 20150114 of Tor-ramdisk, the uClibc-based micro Linux distribution whose only purpose is to host a Tor relay in an environment that maximizes security and privacy. This release includes updates to Tor, Libevent, and other key software.

Nik [announced](https://lists.torproject.org/pipermail/tor-dev/2015-January/008174.html) oppy, an onion proxy implemented in Python: “oppy works like a regular Tor client”, though “there are a number of simplifications made, with the major ones primarily centering around circuit management/build logic and how and when network status documents are collected”. Nik also asked for suggestions on how to take the project forward: “Whether or not I continue hacking on oppy to make it a solid piece of software (rather than just a prototype) or just leave it as is as a reference depends on whether or not the Tor development community sees any real uses or future potential for the project”.

meejah [announced](https://lists.torproject.org/pipermail/tor-dev/2015-January/008166.html) a new one-to-one encrypted and anonymous voice chat feature for “[carml](https://github.com/meejah/carml.git)”, the command-line Tor control utility: “ [It] essentially cross-connects the mic + speakers of each side via an Opus + OGG stream over a single Tor TCP connection.” As meejah warns, it is “NOT FOR REAL USE at all yet”, but if you have experience with gstreamer and/or OGG then please see meejah’s message for some unresolved questions.

Following suggestions from [Sebastian Urbach](https://lists.torproject.org/pipermail/tor-relays/2015-January/006240.html) and [grarpamp](https://lists.torproject.org/pipermail/tor-relays/2015-January/006248.html), Karsten Loesing [altered](https://bugs.torproject.org/14257) the main unit of data rate measurement for the [Tor Metrics portal](https://metrics.torproject.org/) from MiB/s (mebibytes per second) to the more common Gbit/s (gigabits per second).

Philipp Winter [published](https://lists.torproject.org/pipermail/tor-dev/2015-January/008156.html) preliminary statistics and analysis obtained by running a Go implementation of [Doctor](https://gitweb.torproject.org/doctor.git/)’s sybil-hunting script over archived consensuses: “I’ll have a more detailed analysis at some point in the future.”

The Tails team [published](https://mailman.boum.org/pipermail/tails-dev/2015-January/007919.html) instructions for running an nginx webserver as a hidden service using a copy of Tails: “Feedback is welcome!”

Thanks to [Frédéric Cornu](https://lists.torproject.org/pipermail/tor-mirrors/2015-January/000850.html) for running a mirror of the Tor Project’s website and software!

This week in Tor history
========================

[A year ago this week](https://lists.torproject.org/pipermail/tor-news/2014-January/000029.html), the “[Spoiled Onions](http://www.cs.kau.se/philwint/spoiled_onions/)” project published its preliminary technical report. The goal of the project was to monitor Tor exit relays in order to “expose, document, and thwart malicious or misconfigured relays”; the researchers turned up 65 such relays over the course of their investigation, with the culprits engaging in attacks such as “SSH and HTTPS MitM, HTML injection, SSL stripping, and traffic sniffing”, or unintentionally interfering with traffic as a result of upstream censorship.

Events such as the [RELAY\_EARLY traffic confirmation attack](https://blog.torproject.org/blog/tor-security-advisory-relay-early-traffic-confirmation-attack) and the [sybil attacks late last year](https://lists.torproject.org/pipermail/tor-consensus-health/2014-December/005381.html) have only highlighted the importance of monitoring for malicious relays in the Tor network. The [bad-relays mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/bad-relays) serves as a reporting channel for Tor community members who believe particular relays are up to no good (messages sent to the list are not publicly visible, for [various reasons](https://lists.torproject.org/pipermail/tor-news/2014-August/000057.html)); David Fifield has been experimenting with [data visualizations of significant network events](https://lists.torproject.org/pipermail/tor-dev/2015-January/008095.html); and Philipp Winter, a “Spoiled Onions” co-author, has been working on additional tools (such as the above-mentioned Go sybil hunter and “[zoossh](https://gitweb.torproject.org/user/phw/zoossh.git/)”, a speedy Tor network document parser) to make these checks more efficient — to give only a few examples of recent work by the community on this issue.

* * * * *

This issue of Tor Weekly News has been assembled by Harmony.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
