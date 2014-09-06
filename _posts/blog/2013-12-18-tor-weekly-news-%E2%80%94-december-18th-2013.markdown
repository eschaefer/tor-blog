---
layout: post
title: "Tor Weekly News — December 18th, 2013"
permalink: blog/tor-weekly-news-%E2%80%94-december-18th-2013
date: 2013-12-18
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the twenty-fifth issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the ever-updating Tor community.

# Tor 0.2.4.19 is out

After more than a year in the making, Roger Dingledine [announced](https://lists.torproject.org/pipermail/tor-talk/2013-December/031392.html) the first stable release in the Tor 0.2.4 series, as well as the dedication of this series to the memory of Aaron Swartz (1986-2013).

Tor 0.2.4 boasts a large number of major new features, among them a new circuit handshake, improved link encryption, a flexible approach to the queueing of circuit creation requests, and the use of “directory guards” to defend against client-enumeration attacks. You can consult the full changelog in Roger’s announcement, and [download the source code](https://www.torproject.org/dist/) from the website.

As no code changes have been made since the previous release candidate, there is no reasons for users of tor 0.2.4.18-rc to upgrade in a hurry.

# Tor Browser Bundle 3.5rc1 is out

Mike Perry [announced](https://blog.torproject.org/blog/tor-browser-bundle-35rc1-released) the first release candidate in the Tor Browser Bundle 3.5 series, and strongly encouraged users to update in anticipation of the imminent end-of-life of both the 2.x stable and 3.0 series, following Mozilla's deprecation of Firefox 17 ESR, on which both are based.

This release also includes a number of important security updates, alongside various bugfixes and usability improvements; for this reason as well, users should upgrade as soon as possible.

# Tails 0.22 is out

Tails saw its [35th release](https://tails.boum.org/news/version_0.22/) on December 11th. It incorporates many major and minor improvements and bugfixes, and opens up the new incremental-upgrade feature for beta-testing.

As this is the first release to feature a browser based on the Firefox 24 ESR series, some small inconveniences found their way in. Have a look at the known issues before giving it a go.

Nevertheless, it fixes [several important security issues](https://tails.boum.org/security/Numerous_security_holes_in_0.21/), so it is recommended that all users upgrade as soon as possible.

# Torservers.net awarded $250,000 grant

The Torservers.net team [announced](https://blog.torservers.net/20131213/torservers-awarded-250000-by-digital-defenders.html) that they have received a $250,000 organizational grant, to be spread over two years, from the [Digital Defenders Partnership](http://digitaldefenders.org/), which in its own words was “established to provide rapid response to threats to internet freedom.”

With this grant, wrote Moritz Bartl, “participating Torservers organizations will be able to sustain at least 3 Gbit/s of exit traffic, and 2000 fast and up-to-date bridges.”

In order to make the most efficient use of this significant contribution to the Tor network while maintaining its diversity, [wrote Moritz](https://lists.torproject.org/pipermail/tor-relays/2013-December/003495.html), “we need to find seven more organizations that are willing to rent servers for a period of at least 2 years”, [adding](https://mailman.stanford.edu/pipermail/liberationtech/2013-December/012376.html) that “we really want to avoid having organizations run both high bandwidth exit relays and a larger number of Tor bridges: An operator should not see both traffic entering the Tor network and traffic leaving the Tor network” .

For this reason, he called for groups interested in supporting the Tor network to get in contact, in order to discuss how they can best set up and maintain Tor services. The first such partnership will be with the [Institute for War and Peace Reporting's Cyber Arabs group](https://www.cyber-arabs.com/).

If you represent an organization that could make this much-needed contribution to the Tor network, please contact the Torservers.net team, or join them at the [Tor relay operators meetup during the upcoming Chaos Communication Congress in Hamburg](https://events.ccc.de/congress/2013/wiki/Session:Torservers_Meetup).

# Miscellaneous news

The Tails team reported on the vast amount of [activity that occurred during November 2013](https://tails.boum.org/news/report_2013_11/). Coming up in the next few Tails releases are an updated I2P, a new clock applet with configurable timezone, better localization, incremental upgrades, safer persistence, MAC spoofing…

meejah [announced](https://lists.torproject.org/pipermail/tor-dev/2013-December/005927.html) the release of txtorcon 0.8.2, and warned users that they should upgrade if they use that program’s TCP4HiddenServiceEndpoint feature, in order to fix a bug that allows listening on hosts other than 127.0.0.1.

Kevin P Dyer [announced](https://lists.torproject.org/pipermail/tor-dev/2013-December/005953.html) the 0.2.2 release of fteproxy, which “includes the removal of gmpy as a dependency, additional documentation to explain the significance of language theoretical algorithms, and bounds checking of the input/output of our (un)ranking algorithms”; this [hot on the heels of 0.2.1](https://lists.torproject.org/pipermail/tor-dev/2013-December/005929.html), in which he “focused on breaking away from heavyweight dependencies: OpenFST and boost”.

Mike Perry [shared his thoughts](https://lists.torproject.org/pipermail/tor-dev/2013-December/005923.html) regarding the presence of the Tor Browser Bundle in centralized repositories such as the Apple App Store or Google Play, and the possibilities for attack that these stores open up.

Ondrej Mikle [warned users of Enterprise Linux 5](https://lists.torproject.org/pipermail/tor-talk/2013-December/031408.html) that Tor RPM packages will no longer be built for their platform, owing to an “increasing number of required workarounds”.

Karsten Loesing published a [summary of the past, present and the future of the Tor Metrics project](https://lists.torproject.org/pipermail/tor-dev/2013-December/005948.html), which he maintains, offering some context for the various changes that have recently been announced.

Lunar sent reports from the Tor help desk for [October](https://lists.torproject.org/pipermail/tor-reports/2013-December/000404.html) and [November](https://lists.torproject.org/pipermail/tor-reports/2013-December/000405.html).

Jacob Appelbaum recapped his work over the last few months — from June to December — in a slew of reports ( [June](https://lists.torproject.org/pipermail/tor-reports/2013-December/000407.html), [July](https://lists.torproject.org/pipermail/tor-reports/2013-December/000408.html), [August](https://lists.torproject.org/pipermail/tor-reports/2013-December/000409.html), [September](https://lists.torproject.org/pipermail/tor-reports/2013-December/000410.html), [October](https://lists.torproject.org/pipermail/tor-reports/2013-December/000411.html), [November](https://lists.torproject.org/pipermail/tor-reports/2013-December/000412.html), [December](https://lists.torproject.org/pipermail/tor-reports/2013-December/000413.html)).

# Tor help desk roundup

Occasionally users who need the Pluggable Transports Tor Browser Bundle will download the Vidalia Bridge Bundle instead, which is less useful for users trying to circumvent state censorship. The Vidalia Bridge Bundle is only available for Windows and is configured by default to turn the client machine into a bridge. None of the Vidalia Bundles are designed to use Pluggable Transports.

* * *

This issue of Tor Weekly News has been assembled by harmony, Lunar, dope457, and Matt Pagan.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

