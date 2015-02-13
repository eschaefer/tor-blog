---
layout: post
title: "Tor Weekly News — September 10th, 2014"
permalink: tor-weekly-news--september-10th-2014
date: 2014-09-10 07:00:00
author: harmony
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the thirty-sixth issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

More monthly status reports for August 2014
===========================================

The wave of regular monthly reports from Tor project members for the month of August continued, with reports from [Yawning Angel](https://lists.torproject.org/pipermail/tor-reports/2014-September/000643.html), [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-September/000644.html), [Isis Lovecruft](https://lists.torproject.org/pipermail/tor-reports/2014-September/000646.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2014-September/000647.html), and [Griffin Boyce](https://lists.torproject.org/pipermail/tor-reports/2014-September/000648.html).

Arturo Filastò reported on behalf of the [OONI team](https://lists.torproject.org/pipermail/tor-reports/2014-September/000645.html).

Miscellaneous news
==================

Nathan Freitas [announced](https://lists.mayfirst.org/pipermail/guardian-dev/2014-September/003752.html) the release of Orbot 14.0.8, containing “some fixes for people who like to fiddle with transproxy/iptables settings, which can lead to the device getting into a bad network state”, as well as for “a common freak crash that was occuring on app exit in some cases.” See Nathan’s message for a full changelog and download links.

Mike Perry [asked for comments](https://lists.torproject.org/pipermail/tor-talk/2014-September/034606.html) on his proposal to drop Tor Browser support for Mac OS X 10.6, which is no longer receiving security updates from Apple. This means that the Tor Browser team would only have to distribute standard-sized 64-bit builds for Mac OS X rather than the oversized 32+64-bit set. Users who are unable to upgrade their operating system would still be able to use Tails for their Tor browsing needs.

Hartmut Haase [reported](https://lists.torproject.org/pipermail/tor-talk/2014-September/034666.html) that Tor Browser occasionally fails to open, despite a successful connection being made to the Tor network; several other users confirmed that they are also experiencing this problem. Georg Koppen [suggested](https://lists.torproject.org/pipermail/tor-talk/2014-September/034678.html) that the issue is the one covered by [bug ticket \#10804](https://bugs.torproject.org/10804): “Solving this is high on the priority list, but alas not as high as getting everything ready for the switch to ESR31.”

Thanks to [Peter Ludikovsky](https://lists.torproject.org/pipermail/tor-mirrors/2014-September/000681.html) and [goll](https://lists.torproject.org/pipermail/tor-mirrors/2014-September/000685.html) for running mirrors of the Tor Project website and software archive!

Andrew Lewman [published](https://lists.torproject.org/pipermail/tor-mirrors/2014-September/000690.html) the results of a test he ran to answer the question “Why not just use CloudFlare for mirrors of the Tor Project website?”: “The results are that using CloudFlare doesn’t offload the binaries, which are what make up the bulk of traffic on the mirror […] I’ve started to look at CDN providers to see if there are affordable services which can offload the entire site itself.”

As part of an ongoing effort to rescue the Tor blog from rot and ruin caused by broken Drupal code, ultrasandwich [set up](https://bugs.torproject.org/10022#comment:22) an [unofficial preview](http://tor-blog.deadhare.com/) of a possible blog based on the Jekyll static site generator. If you want to contribute to the revamp of the Tor Project website, including the blog, the [www-team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/www-team) awaits your comments and ideas!

Tor help desk roundup
=====================

Users want to know if their personal information is safe when they use Tor Browser. Personal accounts are no less secure using Tor Browser than they are using the web without Tor: the problem of authenticating websites and preventing eavesdropping has been addressed outside of the Tor context through HTTPS. That’s why the Tor Browser ships with the [HTTPS-Everywhere browser extension](https://www.eff.org/https-everywhere) — for every website you visit, HTTPS-Everywhere checks whether or not that website is known to have an HTTPS version, and if so it connects to the site using HTTPS instead of HTTP. Tor + HTTPS provides full end-to-end encryption when visiting any site that offers its content via HTTPS. Using HTTPS with Tor helps keep users’ web accounts secure.

Easy development tasks to get involved with
===========================================

If a single human or organization runs more than one relay, they should configure all their relays to be in the same “family”, the goal being to prevent clients from using more than one of these relays in the same circuit. However, the config option used for this, MyFamily, only accepts relay fingerprints that are preceeded by \$, unlike most other config options. It would be great if this option accepted fingerprints preceeded by \$, as well as without it. Nick Mathewson says this ticket would be pretty easy, so why not give it a try? It does sound like some fun C hacking. Be sure to post your patch to the [ticket](https://bugs.torproject.org/12093).

Back in the day, the tor daemon, which is the core of the Tor network, compiled and ran on Windows 98. But that’s history, and aren’t we all glad? Somebody should identify and drop support code for all Windows versions prior to Windows XP. Nick says “this is mainly going to be a matter of identifying cases where we use LoadLibrary and GetProcAddress to find always-present-functions in always-present DLLs.” If the previous sentence made any sense to you, maybe you’re a good person to help with this! Be sure to comment on the [ticket](https://bugs.torproject.org/11444) if you have a branch to review.

* * * * *

This issue of Tor Weekly News has been assembled by harmony, Matt Pagan, Karsten Loesing, and Lunar.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
