---
layout: post
title: "Tor Weekly News — May 14th, 2014"
permalink: tor-weekly-news--may-14th-2014
date: 2014-05-14 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the nineteenth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Tor Browser 3.6.1 is released
=============================

On May 7th, [version 3.6.1 of the Tor Browser was released](https://blog.torproject.org/blog/tor-browser-361-released). Apart from updating HTTPS Everywhere and NoScript, the new release mainly solves a [regression experienced by proxy users](https://trac.torproject.org/projects/tor/ticket/11658).

The new version should not error out with “You have configured more than one proxy type” anymore.

More monthly status reports for April 2014
==========================================

More monthly reports from Tor project members have arrived this week with submissions from [Nicolas Vigier](https://lists.torproject.org/pipermail/tor-reports/2014-May/000531.html) and [Roger Dingledine](https://lists.torproject.org/pipermail/tor-reports/2014-May/000533.html).

Roger also sent the report for [SponsorF](https://lists.torproject.org/pipermail/tor-reports/2014-May/000532.html). The [Tails team has released theirs](https://tails.boum.org/news/report_2014_04/).

Miscellaneous news
==================

[ooniprobe 1.0.2 has been released](https://lists.torproject.org/pipermail/ooni-dev/2014-May/000114.html). The new version brings security fixes, a manpage, a test for Tor bridge reachability among other improvements.

As the Tor blog should [migrate away from its current decaying software](https://bugs.torproject.org/10022), Eric Schaefer [wrote](https://lists.torproject.org/pipermail/www-team/2014-May/000316.html) to tell that he had extracted all blog posts in a format ready for a static site generator. Comments are also available. One option would be to import them in a dedicated commenting system. Tom Purl has [setup](https://lists.torproject.org/pipermail/www-team/2014-May/000318.html) a test Juvia instance for anyone who wish to give it a shot.

David Fifield [released](https://lists.torproject.org/pipermail/tor-qa/2014-May/000410.html) a new round of Tor Browser packages modified to include [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek). “Unlike previous bundles […], these ones aren’t configured to use meek automatically. You have to select ‘Configure’ on the network settings screen and then choose meek from the list of transports.” Please give them a try!

Isis Lovecruft [rewrote](https://lists.torproject.org/pipermail/tor-dev/2014-May/006856.html) the email bridge distributor in order to fix some fundamental design problems with the old code. Reviews are welcome.

Tor help desk roundup
=====================

A relay operator contacted the Tor Help Desk after seeing the following message in the Tor log: “http status 400 ("Fingerprint is marked rejected") response from dirserver '128.31.0.34:9131'”.

One might see this message is if one’s relay was found to be vulnerable to the Heartbleed OpenSSL bug and subsequently removed from the Tor consensus. [Instructions for upgrading one’s relay](https://blog.torproject.org/blog/openssl-bug-cve-2014-0160) are on the Tor project’s blog.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, Karsten Loesing and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
