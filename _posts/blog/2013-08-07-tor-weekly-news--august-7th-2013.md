---
layout: post
title: "Tor Weekly News — August, 7th 2013"
permalink: tor-weekly-news--august-7th-2013
date: 2013-08-07 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the 6<sup>th</sup> issue of Tor Weekly News, the weekly newsletter that covers what is happening in the resilient Tor community.

Large hidden services provider compromised, attacks older TBB versions
======================================================================

[Andrew Lewman wrote](https://blog.torproject.org/blog/hidden-services-current-events-and-freedom-hosting): “Around midnight on August 4th we were notified by a few people that a large number of hidden service addresses have disappeared from the Tor network.”

It turned out that Freedom Hosting, a company specializing in hosting websites accessible through Tor hidden services, was compromised. As Andrew puts it, “From what is known so far, the breach was used to configure the server in a way that it injects some sort of JavaScript exploit in the web pages delivered to users. This exploit is used to load a malware payload to infect user’s computers.” Andrew also reiterated that “the person, or persons, who run Freedom Hosting are in no way affiliated or connected to The Tor Project, Inc., the organization coordinating the development of the Tor software and research”.

The Tor Browser is currently based on Mozilla Firefox 17 ESR. With the [help of Mozilla](https://blog.mozilla.org/security/2013/08/04/investigating-security-vulnerability-report/) and [other researchers](http://tsyrklevich.net/tbb_payload.txt) it was understood that the exploit used a vulnerability in Firefox JavaScript engine to attack Windows users of the Tor Browser Bundle. This vulnerability was [fixed in Firefox 17.0.7 ESR](https://www.mozilla.org/security/announce/2013/mfsa2013-53.html) and subsequently in versions 2.3.25-10 ([released June 26 2013](https://blog.torproject.org/blog/new-tor-browser-bundles-and-tor-02414-alpha-packages)), 2.4.15-alpha-1 ([released June 26 2013](https://blog.torproject.org/blog/new-tor-browser-bundles-and-tor-02414-alpha-packages)) 3.0alpha2 ([released June 30 2013](https://blog.torproject.org/blog/tor-browser-bundle-30alpha2-released)) and 2.4.15-beta-1 ([released July 8 2013](https://blog.torproject.org/blog/tor-02415-rc-packages-available)).

Users running updated versions, and those who have disabled JavaScript, are not affected by the exploit.

Roger Dingledine issued a [security advisory](https://lists.torproject.org/pipermail/tor-announce/2013-August/000089.html) with advice to mitigate future issues: “be sure you’re running a recent enough Tor Browser Bundle”, “be sure to keep up-to-date in the future”, “consider disabling JavaScript”, “consider switching to a “live system” approach like Tails”, “be aware that many other vectors remain for vulnerabilities in Firefox”. It is strongly advised to read the advisory in full.

The versions of Firefox used in Pluggable Transport bundles are still vulnerable. Replacements have been built, with credit to David Fifield, but they are [yet to be released](https://trac.torproject.org/projects/tor/ticket/9391).

The press is running many stories covering these events, several containing false information. A better example is [Kevin Poulsen’s article](http://www.wired.com/threatlevel/2013/08/freedom-hosting/) published in Wired on August, 5th. It did however assert “the malware only targets Firefox 17 ESR, the version of Firefox that forms the basis of the Tor Browser Bundle”, in-fact most recent Tor Browser Bundle releases, with the exception of Pluggable Transports bundles, contained the patched version of Firefox ESR.

Monthly status reports for July 2013
====================================

The wave of regular monthly reports from Tor project members for the month of July has begun. [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2013-August/000294.html) was first this time, followed by reports from [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2013-August/000295.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2013-August/000296.html), [Noel David Torress Taño](https://lists.torproject.org/pipermail/tor-reports/2013-August/000299.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2013-August/000297.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2013-August/000298.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2013-August/000300.html), [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2013-August/000301.html), [Mike Perry](https://lists.torproject.org/pipermail/tor-reports/2013-August/000302.html), [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2013-August/000303.html), and [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2013-August/000304.html).

Miscellaneous news
==================

Tails developers issued a [call for testing](https://tails.boum.org/news/test_0.20-rc1/) of the first release candidate of the upcoming 0.20 [21]. Send them your reports!

Security researcher Jason Geffner presented a new tool to route all TCP/IP and DNS traffic through the Tor network on Windows called [Tortilla](https://www.blackhat.com/us-13/briefings.html#Geffner2) during Black Hat USA 2013 and subsequently on the [tor-talk mailing list](https://lists.torproject.org/pipermail/tor-talk/2013-August/029254.html). Binary and source code are [available](http://www.crowdstrike.com/community-tools/) and are awaiting reviews by the community.

Wendell [announced the first release of Tor.framework](https://lists.torproject.org/pipermail/tor-talk/2013-July/029150.html), a “Cocoa framework that allows developers to write apps for Mac OS X and iOS that work over the Tor onion routing network”. No comments have been made yet. Feel free to look at the [source code](https://github.com/grabhive/Tor.framework), review and experiment.

[Jerzy Łogiewa asked on tor-talk](https://lists.torproject.org/pipermail/tor-talk/2013-August/029203.html) if Tor hidden services could be made to work near the speed of the standard web. Arian Sanusi replied that speed of light was actually the limiting factor for latency issues: “if relays were homogeneous distributed among the globe, two random relays will be 1/4 earth circumference apart on average. […] That’s 400ms from finite speed of light. Switches, routers and relays along the way will add to that.”

Thanks to [Michael Marz](https://lists.torproject.org/pipermail/tor-commits/2013-August/060173.html) and [Neo](https://lists.torproject.org/pipermail/tor-commits/2013-August/060250.html) for running new mirrors of the Tor website.

* * * * *

This issue of Tor Weekly News has been assembled by dope457, malaparte, Lunar, harmony, and Yawning.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing-list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
