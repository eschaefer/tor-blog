---
layout: post
title: "Tor Weekly News — August 27th, 2014"
permalink: tor-weekly-news--august-27th-2014
date: 2014-08-27 07:00:00
author: harmony
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the thirty-fourth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Orfox: a new Firefox-based secure browser for Android
=====================================================

With the growing popularity of pocket computers (also known as “phones”), users need to have access to censorship-circumvention and anonymity systems on these devices as well as on their desktop or laptop machines. While there is currently no supported implementation of Tor for Apple’s iOS, the [Guardian Project](https://guardianproject.info) works closely with the Tor Project to produce (amongst other software) a Tor client for Android named [Orbot](https://guardianproject.info/apps/orbot/). Mobile applications can be proxied through Orbot just as they can through the Tor client on other operating systems, but mobile web browsing potentially suffers from the same issues that the Tor Browser was designed to protect against, such as disk leaks and a large attack surface. The Guardian Project has therefore also been maintaining a dedicated mobile browser for use with Orbot under the name [Orweb](https://guardianproject.info/apps/orweb/).

Orweb is based on WebView, and is limited by that browser’s features; flaws such as the [potential HTML5 IP leak](https://guardianproject.info/2014/06/30/recent-news-on-orweb-flaws/), while possible to work around in the short term, have made it clear that the best future for secure mobile browsing lies in a switch to an application based on Firefox/Fennec/GeckoView.

Following a successful Google Summer of Code project by [Amogh Pradeep](https://lists.torproject.org/pipermail/tor-dev/2014-August/007379.html) and work by other Guardian Project members, Nathan Freitas [announced](https://lists.mayfirst.org/pipermail/guardian-dev/2014-August/003717.html) that “a real working version” of Orfox, the new Orbot-compatible mobile browser, is now available. “All the necessary defaults [have been] changed to match Tor Browser’s defaults as closely as possible”; the developers also “remove the Android permissions for things like camera, mic, GPS” and “turn off webrtc.”

“We still need to figure out which preferences and features map between the desktop mobile browser and the Android version, so there is quite a bit of work to do”, but you can download and test this initial version by following the links in Nathan’s email. “Over the next few months we hope to launch this as our new official browser for Orbot, and deprecate Orweb as quickly as possible”, he concluded.

Miscellaneous news
==================

A new release of ooniprobe, the network interference data collector for [OONI](https://ooni.torproject.org/), was [announced](https://lists.torproject.org/pipermail/ooni-dev/2014-August/000147.html) by Arturo Filastò. Version 1.1.0 introduces a new command line tool “for listing the reports that have not been published to a collector and that allows the probe operator to choose which ones they would like to upload”. The new version also improves the privacy of the reports by sanitizing file paths.

Developers of applications using [Onionoo](https://onionoo.torproject.org/) — the web service to learn about currently running Tor relays and bridges — are invited to join the new [onionoo-announce mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/onionoo-announce). Keeping the list low volume, Karsten Loesing plans on using it to announce major protocol changes, scheduled maintenance, major bug fixes, and other important news.

Yawning Angel has [made available](https://lists.torproject.org/pipermail/tor-dev/2014-August/007404.html) an experimental version of the Tor Browser that includes the latest version of the [obfs4](https://github.com/Yawning/obfs4) pluggable transport. Testing on Windows and OS X would be particularly welcome.

Fabian Keil [reported](https://lists.torproject.org/pipermail/tor-dev/2014-August/007412.html) that FreeBSD now includes ports of liballium and obfsclient.

JusticeRage [explained](https://lists.torproject.org/pipermail/tor-relays/2014-August/005168.html) how relay operators who offer exiting on port 25 can protect the reputation of their domain name by using the Sender Policy Framework.

Sreenatha Bhatlapenumarthi sent the [final GSoC report](https://lists.torproject.org/pipermail/tor-dev/2014-August/007399.html) for the Tor Weather rewrite project. Juha Nurmi sent [another report](https://lists.torproject.org/pipermail/tor-reports/2014-August/000625.html) on the development of ahmia.fi.

Thanks to s7r for hosting a new [mirror](https://lists.torproject.org/pipermail/tor-mirrors/2014-August/000669.html) of the Tor Project’s website and software!

Tor help desk roundup
=====================

Users of different VPN (Virtual Private Network) services have told the help desk that Tor Browser has difficulty connecting to Tor when a VPN is in use. Using Tor with a VPN is not supported. For a trusted entry into the Tor network, bridges and pluggable transports are recommended, while for anonymizing all network traffic coming from a computer, [Tails](https://tails.boum.org/) is recommended.

Easy development tasks to get involved with
===========================================

The bandwidth authority scanners measure the actual bandwidth offered by Tor relays in order to get accurate information into the Tor consensus. The measurement process currently splits up the set of relays that are to be measured into 4 subsets, with the goal that measuring each of these subsets should take [about the same time](https://bugs.torproject.org/3440). However, this is not the case. Measuring subsets 2 and 3 is about twice as fast as measuring subset 1, and subset 4 is twice as fast as subset 2 and 3. If you're up for doing some experiments to split up the set into more equal subsets, please let us know about your findings on the ticket.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, Karsten Loesing, and dope457.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
