---
layout: post
title: "Tor Weekly News — June 25th, 2014"
permalink: tor-weekly-news--june-25th-2014
date: 2014-06-25 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the twenty-fifth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the community around Tor, the “[fine-meshed net](https://lists.torproject.org/pipermail/tor-talk/2014-June/033358.html)”.

Tor 0.2.5.5-alpha is out
========================

Tor 0.2.5.5-alpha was [released](https://lists.torproject.org/pipermail/tor-talk/2014-June/033347.html), fixing “a wide variety of remaining issues in the Tor 0.2.5.x release series, including a couple of DoS issues, some performance regressions, a large number of bugs affecting the Linux seccomp2 sandbox code, and various other bugfixes”, in Nick Mathewson’s words. Among the major security improvements is an adjustment to the way Tor decides when to close TLS connections, which “should improve Tor’s resistance against some kinds of traffic analysis, and lower some overhead from needlessly closed connections”.

You can download the [source tarball](https://www.torproject.org/dist/), or install the package by following the [instructions for your system](https://www.torproject.org/docs/installguide). This release is also now available in the [Debian](http://packages.qa.debian.org/t/tor/news/20140619T120436Z.html) and [Tor Project](https://www.torproject.org/docs/debian.html.en#development) repositories.

Debian Wheezy’s tor version to be updated
=========================================

Following a [suggestion by Peter Palfrader](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=751977), Debian developers are preparing to update the version of tor found in the Debian stable repositories from 0.2.3.25 to 0.2.4.22. Among the chief motives for doing so is that “about a quarter of the Tor network (just considering the relays, not any clients), is on 0.2.3.25, presumably because they run Debian stable. If they all upgraded to the 0.2.4.x tree, the network as a whole would become a lot more secure as 0.2.4.x allows clients to use stronger crypto for connections built through these nodes.” Other benefits, including the various measures taken to defend against OpenSSL vulnerabilities discovered earlier this year, make this an attractive proposal.

The [update](https://lists.debian.org/debian-changes/2014/06/msg00072.html) will be shipped in the forthcoming point release (7.6) of Debian Wheezy, on July 12th.

Miscellaneous news
==================

Building on the [May release](https://lists.torproject.org/pipermail/tor-qa/2014-May/000414.html) of experimental Tor Browsers hardened with AddressSanitizer (ASan), Georg Koppen [announced](https://lists.torproject.org/pipermail/tor-qa/2014-June/000428.html) a new set of experimental Linux builds that include both AddressSanitizer and Undefined Behaviour Sanitizer (UBSan), asking for testing and feedback. See Georg’s message for download and build instructions, as well as a couple of known issues.

Nick Mathewson [reminded](https://lists.torproject.org/pipermail/tor-talk/2014-June/033376.html) Tor users, relay operators, and especially hidden service administrators that tor’s 0.2.2 series is no longer supported, and many features will soon stop working entirely; if you are affected, then please upgrade!

Several of Tor’s Google Summer of Code students submitted their regular progress reports: Daniel Martí on the [implementation of consensus diffs](https://lists.torproject.org/pipermail/tor-dev/2014-June/007030.html), Mikhail Belous on the [multicore tor daemon](https://lists.torproject.org/pipermail/tor-dev/2014-June/007034.html), Juha Nurmi on the [ahmia.fi project](https://lists.torproject.org/pipermail/tor-reports/2014-June/000564.html), Zack Mullaly on the [HTTPS Everywhere secure ruleset update mechanism](https://lists.eff.org/pipermail/https-everywhere/2014-June/002147.html), Amogh Pradeep on the [Orbot+Orfox project](https://lists.torproject.org/pipermail/tor-dev/2014-June/007036.html), Sreenatha Bhatlapenumarthi on the [Tor Weather rewrite](https://lists.torproject.org/pipermail/tor-dev/2014-June/007037.html), Marc Juarez on the [link-padding pluggable transport development](https://lists.torproject.org/pipermail/tor-reports/2014-June/000567.html), Israel Leiva on the [GetTor revamp](https://lists.torproject.org/pipermail/tor-dev/2014-June/007039.html), Quinn Jarrell on the [pluggable transport combiner](https://lists.torproject.org/pipermail/tor-dev/2014-June/007040.html), Kostas Jakeliunas on the [BridgeDB Twitter Distributor](https://lists.torproject.org/pipermail/tor-dev/2014-June/007041.html), and Noah Rahman on [Stegotorus security enhancement](https://lists.torproject.org/pipermail/tor-dev/2014-June/007043.html).

Researchers from the Internet Geographies project at the Oxford Internet Institute [produced a cartogram](http://geography.oii.ox.ac.uk/?page=tor) of Tor users by country, using archived data freely available from the Tor Project’s [own Metrics portal](https://metrics.torproject.org), along with an analysis of the resulting image. “As ever more governments seek to control and censor online activities, users face a choice to either perform their connected activities in ways that adhere to official policies, or to use anonymity to bring about a freer and more open Internet”, they conclude.

Andrew Lewman [reported](https://lists.torproject.org/pipermail/tor-relays/2014-June/004752.html) that users with email addresses at Yahoo and AOL have been removed from the [tor-relays mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-relays), as these addresses have been bouncing list emails.

Thanks to the [FoDT.it webteam](https://lists.torproject.org/pipermail/tor-mirrors/2014-June/000617.html) and [Maxanoo](https://lists.torproject.org/pipermail/tor-mirrors/2014-June/000619.html) for running mirrors of the Tor Project’s website!

fr33tux [shared](https://lists.torproject.org/pipermail/tor-talk/2014-June/033337.html) the [slides](http://fr33tux.org/data/prez.pdf) for a French-language presentation on Tor, delivered at Université de technologie Belfort-Montbéliard. The source code (in the LaTeX markup language) is [also available](http://git.fr33tux.org/conference_tor_utbm.git): “feel free to borrow whatever you want from it!”

Thanks to Ximin Luo, the server component of [Flashproxy](https://crypto.stanford.edu/flashproxy/) is now available in Debian in the [“pt-websocket” package](https://packages.debian.org/sid/pt-websocket).

A couple of weeks ago, Roger Dingledine wondered “how many relays are firewalling certain outbound ports (and thus messing with connectivity inside the Tor network)”. ra has just [published the results](https://bugs.torproject.org/12131#comment:11) of a three-week-long test of the interconnectivity between 6730 relays. Contacting the operators of problematic relays is probably the next step for those who wish to keep the network at its best.

George Kadianakis slipped on his storyteller costume to [guide us](https://lists.torproject.org/pipermail/tor-dev/2014-June/007042.html) through layers of the Tor core, motivated by the quest for knowledge. That accursed riddle, “Why does Roger have so many guards?”, now has an answer. Be prepared for a “beautiful stalagmite” and the “truly amazing” nature of Tor!

Tor help desk roundup
=====================

If the Tor Browser stalls while “loading the network status”, please double-check that the system clock is accurate; the same goes for the timezone and daylight saving time settings. Tor needs an accurate clock in order to prevent several classes of attacks on its protocol. It won’t work properly when the local time does not match the one used by other network participants.

Easy development tasks to get involved with
===========================================

When the tor daemon is configured to open a SOCKS port on a public address, it warns about this possible configuration problem twice: once when it reads the configuration file, and a second time when it opens the listener. One warning should be enough. We had a friendly volunteer two years ago who sketched out possible fixes and even wrote a patch, but then concluded that his patch had a problem and went away. If you’re up to some digging into tor’s configuration file handling, and want to clean up a two-year-old patch potentially to be included in tor 0.2.6, please [find the details in the ticket](https://bugs.torproject.org/4019). It’s tagged as easy, so how hard can it be?

* * * * *

This issue of Tor Weekly News has been assembled by harmony, Lunar, Matt Pagan, Karsten Loesing, and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
