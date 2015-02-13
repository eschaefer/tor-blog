---
layout: post
title: "Tor Weekly News — April 30th, 2014"
permalink: tor-weekly-news--april-30th-2014
date: 2014-04-30 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the seventeenth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Tor 0.2.5.4-alpha is released
=============================

The latest incarnation of the current development branch of Tor, dubbed 0.2.5.4-alpha, was [released on April 26th](https://lists.torproject.org/pipermail/tor-talk/2014-April/032817.html). This release brings mainly security and performance improvements for clients and relays.

As a preventive measure (there being no evidence that the keys have been compromised), authority signing keys that were used while susceptible to the OpenSSL “heartbleed” bug are now blacklisted.

Other improvements include fixing two expensive functions on busy relays, better TLS ciphersuite preference lists, support for run-time hardening on compilers that support [AddressSanitizer](https://code.google.com/p/address-sanitizer/), and more work on the Linux sandbox code. There are also several usability fixes for clients (especially clients that use bridges), two new TransPort protocols supported (one on OpenBSD, one on FreeBSD), and various other bugfixes.

As Nick Mathewson wrote: “This release marks end-of-life for Tor 0.2.2.x; those Tor versions have accumulated many known flaws”.

Source code is available at the [usual location](https://www.torproject.org/dist/) and binary packages have already started to be updated.

Introducing the 2014 Google Summer of Code projects
===================================================

As [announced in February](https://blog.torproject.org/blog/tor-google-summer-code-2014), Tor is once again participating in Google’s Summer of Code program, allowing students and aspiring developers the chance to work on a Tor-related project with funding from Google and expert guidance from Tor Project members. After several months of coordination and discussion, this summer’s successful proposals have now been chosen, and some of the students took to the tor-dev mailing list to introduce themselves and their upcoming work.

[Juha Nurmi](https://lists.torproject.org/pipermail/tor-dev/2014-April/006739.html) will continue to work on the already-operational ahmia.fi hidden service search engine, while [Marc Juarez](https://lists.torproject.org/pipermail/tor-dev/2014-April/006741.html) will be “implementing the building blocks for a future padding-based website fingerprinting countermeasure as a pluggable transport”. [Daniel Martí](https://lists.torproject.org/pipermail/tor-dev/2014-April/006744.html) has taken up the challenge of [implementing proposal 140](https://gitweb.torproject.org/torspec.git/blob_plain/refs/heads/master:/proposals/140-consensus-diffs.txt), which aims to considerably reduce the size of the network consensus data that Tor clients fetch every hour, and [Israel Leiva](https://lists.torproject.org/pipermail/tor-dev/2014-April/006745.html) plans to spruce up the neglected GetTor service, which allows users to download the Tor Browser Bundle even if the Tor website and its mirrors are inaccessible. [Amogh Pradeep](https://lists.torproject.org/pipermail/tor-dev/2014-April/006748.html) will be contributing to the Guardian Project’s development of Orfox, a new Android web browser to be used with Orbot, while [Kostas Jakeliunas](https://lists.torproject.org/pipermail/tor-dev/2014-April/006749.html) returns to Tor GSoC to construct a new BridgeDB distributor, serving bridge addresses to users in censored areas over Twitter, and possibly other channels as well. [Quinn Jarrell](https://lists.torproject.org/pipermail/tor-dev/2014-April/006777.html) will be working on building a pluggable transports combiner that “will allow transports to be chained together to form more varieties of transports and make them harder to detect and block”. [Sreenatha Bhatlapenumarthi](https://lists.torproject.org/pipermail/tor-dev/2014-April/006752.html) will pick up the effort of rewriting Tor Weather.

You can read more about each proposal in the respective introductory messages and their replies; a full list of accepted projects is available on the [Google Summer of Code website](https://www.google-melange.com/gsoc/org2/google/gsoc2014/tor). As Daniel wrote, “comments are very welcome”!

Miscellaneous news
==================

Meejah [released version 0.9.2 of txtorcon](https://lists.torproject.org/pipermail/tor-dev/2014-April/006766.html) — the Tor controller library for the Twisted Python framework: “this release adds a few minor bug-fixes and a few API enhancements”.

The Tails team is [looking for enthusiasts equipped with a Bluetooth keyboard and mouse](https://mailman.boum.org/pipermail/tails-testers/2014-April/000010.html) to ensure that Tails works properly with such hardware.

Matthew Finkel forwarded a copy of the [email that was sent to bridge operators ](https://lists.torproject.org/pipermail/tor-relays/2014-April/004428.html) to warn them about the “Heartbleed” vulnerability, and the actions that should be taken as a result. If you know any bridge operator who might not have filled in their contact information, please forward the message!

Karsten Loesing has been working on switching Onionoo — the web service to retrieve information about the Tor network — to use the Gson library instead of plain string concatenation to format its JSON output. As the change might break some applications, client authors should [test their applications](https://lists.torproject.org/pipermail/tor-dev/2014-April/006772.html) and see if everything still works as it should.

Tor help desk roundup
=====================

The help desk has been asked why the Tor Project’s hidden service site mirrors are offline. The sites were taken down during the fallout from the Heartbleed security vulnerability. New hidden service addresses were not generated. The sysadmin team has expressed that they [no longer wish to maintain these services](https://bugs.torproject.org/11567).

News from Tor StackExchange
===========================

Kristopher Ives is working on a card game using Tor. Each user accepts inbound connections through hidden services, and [also needs to make outbound connections](https://tor.stackexchange.com/q/1592/88). Tom Ritter acknowledged it was possible to use only one Tor daemon to do both.

Dan [gets the error message “Cannot load XPCOM” whenever Tor Browser is started](https://tor.stackexchange.com/q/2012/88). Jens Kubieziel pointed to the discussion at [\#10789](https://bugs.torproject.org/10789). The culprit is WebRoot Internet Security as it prevents the proper loading of all browser components; either [uninstalling it or adding DLL files to the whitelist has helped other users](https://blog.torproject.org/blog/tor-browser-352-released#comment-47052).

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, qbi, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
