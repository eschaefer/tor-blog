---
layout: post
title: "Tor Weekly News — November 12th, 2014"
permalink: blog/tor-weekly-news-—-november-12th-2014
date: 2014-11-12 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the forty-fifth issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Mozilla announces Polaris Privacy Initiative
============================================

Mozilla, makers of the Firefox browser upon which Tor Browser is based, [announced](https://blog.mozilla.org/privacy/2014/11/10/introducing-polaris-privacy-initiative-to-accelerate-user-focused-privacy-online) a series of projects to “accelerate pragmatic and user-focused advances in privacy technology for the Web, giving users more control, awareness and protection in their Web experiences”. The Tor Project is one of Mozilla’s two partners in this Polaris Privacy Initiative, and the collaboration will involve looking at the Firefox codebase to see if its relationship to Tor Browser and the Tor development process can be made more efficient, giving Tor engineers more time to focus on other important issues. Mozilla also stated their intention to run several high-capacity Tor middle relays, contributing to a faster and more stable Tor network.

As Andrew Lewman [wrote](https://blog.torproject.org/blog/partnering-mozilla) on the Tor blog, “the Tor Browser is one of the best ways to protect privacy on the web and this partnership is a huge step in advancing people’s right to freedom of expression online”. Watch for more announcements as work on these two fronts continues.

Tor and Operation Onymous
=========================

An international coalition of law enforcement authorities [announced](https://www.europol.europa.eu/content/global-action-against-dark-markets-tor-network) the seizure of over 400 Tor hidden services allegedly engaging in illegal activity. Once the desired headlines had been written, something approaching the facts began to emerge, with the claimed number of seized services [dropping sharply to 27](http://www.dailydot.com/politics/oops-we-counted-wrong-silk-road-dark-net-tor/); more troublingly, several high-capacity Tor relays with no apparent connection to the hidden services were [also](https://blog.torservers.net/20141109/three-servers-offline-likely-seized.html) [seized](https://raided4tor.wordpress.com/). However, in contrast to the [last major takedown of hidden services](https://blog.torproject.org/blog/tor-security-advisory-relay-early-traffic-confirmation-attack), which involved one shared hidden service hosting platform, there was no obvious single feature linking all of the seized sites, leading to concern in the Tor community that an exploit against the Tor network may have been responsible for their discovery.

It could be that these services were deanonymized individually over a period of months using a variety of means, then all seized at once for maximum effect: as Andrew Lewman and others wrote in a [response](https://blog.torproject.org/blog/thoughts-and-concerns-about-operation-onymous) posted to the Tor blog, these methods could include operational security mistakes by service operators, exploitation of flaws in poorly-written website code, or attacks on the Bitcoin cryptocurrency that is widely used on hidden service marketplaces. On the other hand, if an attack on the Tor network itself is at play, it may be a variant of the class of attack known as “traffic confirmation”, like the one [observed earlier this year](https://lists.torproject.org/pipermail/tor-news/2014-August/000057.html). “Unfortunately,” as the blog post notes, ”the authorities did not specify how they managed to locate the hidden services”; even if they had, recent disclosures concerning [“parallel construction” in law enforcement](https://en.wikipedia.org/wiki/Parallel_construction) mean that the public would not necessarily be able to trust their explanation.

“Hidden services need some love” has become a familiar refrain in recent months, and even though the story behind these seizures may remain unknown, they have reinvigorated some long-running threads on improvements to the security of this important technology. George Kadianakis [coded](https://lists.torproject.org/pipermail/tor-dev/2014-November/007730.html) a patch that allows hidden service operators to “specify a set of nodes that will be pinned as middle nodes in hidden service rendezvous circuits”, while the theory behind this [continues to be discussed](https://lists.torproject.org/pipermail/tor-dev/2014-November/007726.html), as does the [hidden service authorization feature](https://lists.torproject.org/pipermail/tor-dev/2014-November/007735.html) and [how widely it is used in practice](https://lists.torproject.org/pipermail/tor-dev/2014-November/007744.html).

“The attention hidden services have received is minimal compared to their social value and compared to the size and determination of their adversaries.” If you are a hidden service operator concerned by these seizures, or you want to help ensure the possibility of free and uncensorable publishing online, see the group blog post for more details, and feel free to join in with the discussions on the tor-dev mailing list.

More monthly status reports for October 2014
============================================

The wave of regular monthly reports from Tor project members for the month of October continued, with reports from [Isis Lovecruft](https://lists.torproject.org/pipermail/tor-reports/2014-November/000693.html), [Nicolas Vigier](https://lists.torproject.org/pipermail/tor-reports/2014-November/000694.html), [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-November/000695.html), and [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2014-November/000696.html).

Roger Dingledine sent out the report for [SponsorF](https://lists.torproject.org/pipermail/tor-reports/2014-November/000697.html).

Miscellaneous news
==================

Arturo Filastò [reported](https://blog.torproject.org/blog/ooni-bridge-reachability-study-and-hackfest) on OONI’s ongoing study of Tor bridge reachability in different countries, and the recent hackfest on the same topic.

Karsten Loesing offered an [update](https://lists.torproject.org/pipermail/onionoo-announce/2014/000002.html) on developments in the world of Onionoo, including new mirrors and search improvements.

Help desk round up
==================

The help desk has been asked how to run Tor Browser on a Chromebook. ChromeOS does not allow any programs to be executed except Google Chrome, including other browsers like Tor Browser. The workaround for this is to install a Debian or Ubuntu environment within ChromeOS using [crouton](https://github.com/dnschneid/crouton). Once crouton is ready, Tor Browser for Linux can be downloaded and installed in the Debian or Ubuntu environment. Crouton users should seek support from the crouton team and not from the Tor help desk.

* * * * *

This issue of Tor Weekly News has been assembled by Harmony, Matt Pagan, Karsten Loesing, and Lunar.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
