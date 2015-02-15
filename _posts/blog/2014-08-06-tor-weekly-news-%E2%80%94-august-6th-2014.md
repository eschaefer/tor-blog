---
layout: post
title: "Tor Weekly News — August 6th, 2014"
permalink: tor-weekly-news-—-august-6th-2014
date: 2014-08-06 07:00:00
author: lunar
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the thirty-first issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Tor and the RELAY\_EARLY traffic confirmation attack
====================================================

Roger Dingledine ended several months of concern and speculation in the Tor community with a security advisory posted to the [tor-announce mailing list](https://lists.torproject.org/pipermail/tor-announce/2014-July/000094.html) and the [Tor blog](https://blog.torproject.org/blog/tor-security-advisory-relay-early-traffic-confirmation-attack).

In it, he gave details of a five-month-long active attack on operators and users of Tor hidden services that involved a variant of the so-called “Sybil attack”: the attacker signed up “around 115 fast non-exit relays” (now removed from the Tor network), and configured them to inject a traffic header signal consisting of RELAY\_EARLY cells to “tag” any hidden service descriptor requests received by malicious relays — a tag which could then be picked up by other bad nodes acting as [entry guards](https://www.torproject.org/docs/faq#EntryGuards), in the process identifying clients which requested information about a particular hidden service.

The attack is suspected to be linked to a [now-cancelled talk that was due to be delivered at the BlackHat security conference](https://blog.torproject.org/blog/recent-black-hat-2014-talk-cancellation). There have been several fruitful and positive research projects involving theoretical attacks on Tor’s security, but this was not among them. Not only were there problems with the process of responsible disclosure, but, as Roger wrote, “the attacker encoded the name of the hidden service in the injected signal (as opposed to, say, sending a random number and keeping a local list mapping random number to hidden service name)”, thereby “[putting] users at risk indefinitely into the future”.

On the other hand, it is important to note that “while this particular variant of the traffic confirmation attack allows high-confidence and efficient correlation, the general class of passive (statistical) traffic confirmation attacks remains unsolved and would likely have worked just fine here”. In other words, the tagging mechanism used in this case is the innovation; the other element of the attack is a known weakness of low-latency anonymity systems, and defending against it is a much harder problem.

“Users who operated or accessed hidden services from early February through July 4 should assume they were affected” and act accordingly; in the case of hidden service operators, this may mean changing the location of the service. Accompanying the advisory were two new releases for both the stable and alpha tor branches (0.2.4.23 and 0.2.5.6-alpha); both include a fix for the signal-injection issue that causes tor to drop circuits and give a warning if RELAY\_EARLY cells are detected going in the wrong direction (towards the client), and both prepare the ground for clients to move to single entry guards (rather than sets of three) in the near future. Relay operators should be sure to upgrade; a point-release of the Tor Browser will offer the same fixes to ordinary users. Nusenu [suggested](https://lists.torproject.org/pipermail/tor-relays/2014-August/005046.html) that relay operators regularly check their logs for the new warning, “even if the attack origin is not directly attributable from a relay’s point of view”. Be sure to read the full security advisory for a fuller explanation of the attack and its implications.

Why is bad-relays a closed mailing list?
========================================

Damian Johnson and Philipp Winter have been working on improving the process of [reporting bad relays](https://trac.torproject.org/projects/tor/wiki/doc/ReportingBadRelays). The process starts by having users report odd behaviors to the bad-relays mailing list.

Only a few trusted volunteers receive and review these reports. Nusenu [started a discussion on tor-talk](https://lists.torproject.org/pipermail/tor-talk/2014-July/034198.html) advocating for more transparency. Nusenu argues that an open list would “likely get more confirm/can’t confirm feedback for a given badexit candidate”, and that it would allow worried users to act faster than operators of directory authorities.

Despite being “usually on the side of transparency”, Roger Dingledine [described](https://lists.torproject.org/pipermail/tor-talk/2014-July/034219.html) being “stuck” on the issue, “because the arms race is so lopsidedly against us”.

Roger explains: “we can scan for whether exit relays handle certain websites poorly, but if the list that we scan for is public, then exit relays can mess with other websites and know they’ll get away with it. We can scan for incorrect behavior on various ports, but if the list of ports and the set of behavior we do is public, then again relays are free to mess with things we don’t look for.”

A better future and more transparency probably lies in adaptive test systems run by multiple volunteer groups. Until they come to existence, as a small improvement, Philipp Winter [wrote](https://lists.torproject.org/pipermail/tor-talk/2014-July/034216.html) it was probably safe to publish why relays were disabled, through “short sentence along the lines of ‘running HTTPS MitM’ or ‘running sslstrip’”.

Monthly status reports for July 2014
====================================

Time for monthly reports from Tor project members. The July 2014 round was opened by [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2014-July/000598.html), followed by [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2014-July/000599.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-August/000601.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2014-August/000603.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-August/000604.html), [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2014-August/000605.html), [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-August/000608.html), [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2014-August/000609.html), [Isis Lovecruft](https://lists.torproject.org/pipermail/tor-reports/2014-August/000610.html), [Griffin Boyce](https://lists.torproject.org/pipermail/tor-reports/2014-August/000611.html), [Arthur Edelstein](https://lists.torproject.org/pipermail/tor-reports/2014-August/000612.html), and [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2014-August/000614.html).

Lunar reported on behalf of the [help desk](https://lists.torproject.org/pipermail/tor-reports/2014-August/000602.html) and Mike Perry for the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2014-August/000607.html).

Miscellaneous news
==================

Anthony G. Basile announced a new release of tor-ramdisk, an i686 or x86\_64 uClibc-based micro Linux distribution whose only purpose is to host a Tor server. [Version 20140801](http://opensource.dyc.edu/pipermail/tor-ramdisk/2014-August/000132.html) updates Tor to version 0.2.4.23, and the kernel to 3.15.7 with Gentoo’s hardened patches.

meejah has [announced](https://lists.torproject.org/pipermail/tor-dev/2014-August/007295.html) a new command-line application. [carml](https://github.com/meejah/carml) is a versatile set of tools to “query and control a running Tor”. It can do things like “list and remove streams and circuits; monitor stream, circuit and address-map events; watch for any Tor event and print it (or many) out; monitor bandwidth; run any Tor control-protocol command; pipe through common Unix tools like grep, less, cut, etcetera; download TBB through Tor, with pinned certs and signature checking; and even spit out and run xplanet configs (with router/circuit markers)!” The application is written in Python and uses the [txtorcon library](https://txtorcon.readthedocs.org/). meejah describes it as early-alpha and warns that it might contain “serious, anonymity-destroying bugs”. Watch out!

Only two weeks left for the Google Summer of Code students, and the last round of reports but one: Juha Nurmi on the [ahmia.fi project](https://lists.torproject.org/pipermail/tor-reports/2014-August/000600.html), Marc Juarez on [website fingerprinting defenses](https://lists.torproject.org/pipermail/tor-reports/2014-August/000606.html), Amogh Pradeep on [Orbot and Orfox improvements](https://lists.torproject.org/pipermail/tor-dev/2014-August/007282.html), Zack Mullaly on the [HTTPS Everywhere secure ruleset update mechanism](https://lists.eff.org/pipermail/https-everywhere/2014-August/002199.html), Israel Leiva on the [GetTor revamp](https://lists.torproject.org/pipermail/tor-dev/2014-August/007284.html), Quinn Jarrell on the [pluggable transport combiner](https://lists.torproject.org/pipermail/tor-dev/2014-August/007285.html), Daniel Martí on [incremental updates to consensus documents](https://lists.torproject.org/pipermail/tor-dev/2014-August/007287.html), Noah Rahman on [Stegotorus enhancements](https://lists.torproject.org/pipermail/tor-dev/2014-August/007288.html), and Sreenatha Bhatlapenumarthi on the [Tor Weather rewrite](https://lists.torproject.org/pipermail/tor-dev/2014-August/007293.html).

The Tails team is looking for testers to solve a possible incompatibility in one of the recommended installation procedures. If you have a running Tails system, a spare USB stick and some time, [please help](https://mailman.boum.org/pipermail/tails-testers/2014-July/000059.html). Don’t miss the [recommended command-line options](https://mailman.boum.org/pipermail/tails-testers/2014-July/000060.html)!

The [Citizen Lab Summer Institute](https://citizenlab.org/summerinstitute/2014.html) took place at the University of Toronto from July 28 to 31. The event brought together policy and technology researchers who focus on Internet censorship and measurement. A lot of great work was presented including but not limited to a proposal to measure the chilling effect, ongoing work to deploy [Telex](http://freehaven.net/anonbib/cache/usenix11-telex.pdf), and several projects to measure censorship in different countries. Some Tor-related work was also presented: Researchers are working on understanding how the Tor network is used for political purposes. Another project makes use of TCP/IP side channels to [measure the reachability of Tor relays from within China](https://arxiv.org/pdf/1312.5739.pdf).

The Electronic Frontier Foundation wrote two blog posts to show why Tor is important for universities and how universities can help the Tor network. The [first part](https://www.eff.org/deeplinks/2014/08/tor-campus-part-i-its-been-done-and-should-happen-again) explains why Tor matters, gives several examples of universities already contributing to the Tor network, and outlines a few reasons for hosting new Tor nodes. The [second part](https://www.eff.org/deeplinks/2014/08/tor-campus-part-ii-icebreakers-and-risk-mitigation-strategies) gives actual tips on where to start, and how to do it best.

Tor help desk roundup
=====================

Users occasionally ask if there is any way to set Tor Browser as the default browser on their system. Currently this is not possible, although it [may be possible](https://bugs.torproject.org/12763) in a future Tor Browser release. In the mean time, Tails provides another way to prevent accidentally opening hyperlinks in a non-Tor browser.

Easy development tasks to get involved with
===========================================

Tor Launcher is the Tor controller shipped with Tor Browser written in JavaScript. Starting with Firefox 14 the “nsILocalFile” interface has been [deprecated and replaced with the “nsIFile” interface](https://bugs.torproject.org/10573). What we should do is replace all instances of “nsILocalFile” with “nsIFile” and see if anything else needs fixing to make Tor Launcher still work as expected. If you know a little bit about Firefox extensions and want to give this a try, clone the [repository](https://gitweb.torproject.org/tor-launcher.git), make the necessary changes, run “make package”, and tell us whether something broke in interesting ways.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, Philipp Winter, David Fifield, Karsten Loesing, and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
