---
layout: post
title: "Tor Weekly News — June 11th, 2014"
permalink: tor-weekly-news-%E2%80%94-june-11th-2014
date: 2014-06-11
author: harmony
category: blog
tags: ["tor weekly news"]
---

Welcome to the twenty-third issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tor Browser 3.6.2 is out

Version 3.6.2 of the Tor Browser has been  [released](https://blog.torproject.org/blog/tor-browser-362-released), featuring “a fix to allow the configuration of a local HTTP or SOCKS proxy with all included Pluggable Transports”, as well as important fixes to mitigate recent OpenSSL vulnerabilities, among other security updates. All users are advised to  [upgrade](https://www.torproject.org/download/download-easy.html) as soon as possible.

# The EFF announces its 2014 Tor Challenge

As part of the wider  [“Reset the Net” event](https://blog.torproject.org/blog/reset-net), the Electronic Frontier Foundation has  [launched](https://blog.torproject.org/blog/tor-challenge-2014) another in its occasional series of Tor Challenges. The goal of the campaign is to increase the Tor network’s capacity and diversity by encouraging members of the public to run relays, and directing them to the legal and technical guidance necessary to do so.

So far, over 600 relays have been started (or had their capacity increased) as part of the campaign: you can see a running total of relays and bytes transferred on the  [campaign page](https://www.eff.org/torchallenge/). Once you’ve set up your relay, you can register it on the page (anonymously or credited to your name); stickers and T-shirts are on offer for those who run relays of a certain size or for a certain period.

If you run into trouble setting up your relay, you can also find expert advice and discussion on the  [tor-relays mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-relays) or the #tor channel on irc.oftc.net.

# Tor and the “EarlyCCS” bug

Following April’s much-loved “Heartbleed” bug, another OpenSSL vulnerability was discovered — nicknamed  [“EarlyCCS”](http://ccsinjection.lepidum.co.jp/) — that could have an impact on the security of many internet services, including Tor. Nick Mathewson  [explained](https://lists.torproject.org/pipermail/tor-talk/2014-June/033161.html) that although “Tor is comparatively resilient to having one layer of crypto removed”, it may be affected to the extent that “an adversary in the position to run a MITM attack on a Tor client or relay could cause a TLS connection to be negotiated without real encryption or authentication.”

Tor users and relay operators should make sure to update their OpenSSL and Tor packages as soon as possible; those using a system tor (rather than or in addition to the Tor Browser) should ensure that they restart it once the updates are installed; otherwise they will not take effect.

# A new website for the directory archive

Karsten Loesing  [announced](https://lists.torproject.org/pipermail/tor-dev/2014-June/006942.html) the new  [CollecTor service](https://collector.torproject.org/), which spins off the directory archive section from the  [Metrics](https://metrics.torproject.org/) portal.

What’s different? Archive tarballs are now provided in a [directory structure](https://collector.torproject.org/archive/) rather than a single directory, recently published descriptors can now be accessed  [much more easily](https://collector.torproject.org/recent/), and the  [documentation of descriptor formats](https://collector.torproject.org/formats.html) has been updated.

The now obsolete rsync access to metrics-archive and metrics-recent will be discontinued on August 4, 2014.

# More monthly status reports for May 2014

The wave of regular monthly reports from Tor project members for the month of May continued, with reports from [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2014-June/000551.html), Isis Lovecruft (who submitted reports for both  [April](https://lists.torproject.org/pipermail/tor-reports/2014-June/000553.html) and  [May](https://lists.torproject.org/pipermail/tor-reports/2014-June/000552.html)),  [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-June/000554.html),  [Nicolas Vigier](https://lists.torproject.org/pipermail/tor-reports/2014-June/000556.html), and  [Roger Dingledine](https://lists.torproject.org/pipermail/tor-reports/2014-June/000559.html).

Roger also sent the report for  [SponsorF](https://lists.torproject.org/pipermail/tor-reports/2014-June/000558.html).

# Miscellaneous news

The Tails developers formally [announced](https://tails.boum.org/news/Join_us_at_the_Tails_HackFest_2014/) the upcoming Tails Hackfest, inviting absolutely “anyone interested in making Tails more usable and more secure” to join them in Paris on the 5th and 6th of July (immediately after the Tor dev meeting) and “learn about the challenges faced by Tails, and how you can be part of the solution”. Fuller details of the venue and timetable can be found on the  [Tails website](https://tails.boum.org/blueprint/HackFest_2014_Paris/).

Several of Tor’s Google Summer of Code students submitted their regular progress reports: Juha Nurmi on the  [ahmia.fi project](https://lists.torproject.org/pipermail/tor-reports/2014-June/000555.html), Israel Leiva on the  [GetTor revamp](https://lists.torproject.org/pipermail/tor-dev/2014-June/006959.html), Amogh Pradeep on the  [Orbot+Orfox project](https://lists.torproject.org/pipermail/tor-dev/2014-June/006960.html), Quinn Jarrell on the  [pluggable transport combiner](https://lists.torproject.org/pipermail/tor-dev/2014-June/006961.html), Marc Juarez on the  [link-padding pluggable transport development](https://lists.torproject.org/pipermail/tor-reports/2014-June/000557.html), Noah Rahman on the  [Stegotorus refactoring work](https://lists.torproject.org/pipermail/tor-dev/2014-June/006962.html), Sreenatha Bhatlapenumarthi on the  [Tor Weather rewrite](https://lists.torproject.org/pipermail/tor-dev/2014-June/006964.html), Daniel Martí on the  [implementation of consensus diffs](https://lists.torproject.org/pipermail/tor-dev/2014-June/006966.html), and Mikhail Belous on the  [multicore tor daemon](https://lists.torproject.org/pipermail/tor-dev/2014-June/006984.html).

Thanks to  [moparisthebest](https://lists.torproject.org/pipermail/tor-mirrors/2014-June/000612.html) for running a mirror of the Tor Project website!

Roger Dingledine  [asked](https://lists.torproject.org/pipermail/tor-relays/2014-June/004642.html) the tor-relays mailing list about the situation of Mac OS X users who would like to run Tor relays, and what steps should be taken to make it easier for them to do so “now that the Vidalia bundles are deprecated and hard to find”.

Isis Lovecruft has deployed  [BridgeDB version 0.2.2](https://gitweb.torproject.org/bridgedb.git/blob_plain/cb8b01bc:/CHANGELOG) which contains many fixes and translation updates. The email autoresponder should not reply with empty emails any more.

Damian Johnson has  [written up](https://lists.torproject.org/pipermail/tor-dev/2014-June/006970.html) several ideas regarding a possible rewrite of the  [ExoneraTor service](https://exonerator.torproject.org/) in Python.

HTTPS is sometimes heavily throttled by censors, making it hard to download the Tor Browser over an HTTPS link. Israel Leiva is  [asking for feedback](https://lists.torproject.org/pipermail/tor-dev/2014-June/006977.html) about making the GetTor email service reply with links to unencrypted HTTP servers as a work-around.

# Tor help desk roundup

The help desk has been asked for information on TorCoin, a proposed cryptocurrency. TorCoin is not affiliated with or endorsed by the Tor Project. The Tor Project publishes  [guidelines on the use of its trademark](https://www.torproject.org/docs/trademark-faq.html.en) to try to prevent confusing uses of the Tor name.

# Easy development tasks to get involved with

obfsproxy, the traffic obfuscator, opens the “authcookie” file for each new incoming connection. George Kadianakis suggests that it should instead  [read the file on startup and keep its content in memory during operation](https://bugs.torproject.org/9822). obfsproxy is written in Python/Twisted. The change should be pretty small, but if you like finding the right places that need changing, feel free to look at the ticket and post your patch there.

* * *
This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, Karsten Loesing, and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the  [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the  [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

