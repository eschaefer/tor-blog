---
layout: post
title: "Tor Weekly News — July 30th, 2014"
permalink: blog/tor-weekly-news-%E2%80%94-july-30th-2014
date: 2014-07-30
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the thirtieth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tor Browser 3.6.3 is out

A [new pointfix release for the 3.6 series of the Tor Browser](https://blog.torproject.org/blog/tor-browser-363-released) is out. Most components have been updated and a couple of small issues fixed. Details are available in the release announcement.

The release fixes [import security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.7) from Firefox. Be sure to [upgrade](https://www.torproject.org/download/download-easy.html)! Users of the experimental [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek) bundles have [not been forgotten](https://people.torproject.org/~dcf/pt-bundle/3.6.3-meek-1/).

# New Tor stable and alpha releases

Two new releases of Tor are out. The new [0.2.5.6-alpha release](https://lists.torproject.org/pipermail/tor-talk/2014-July/034180.html) “brings us a big step closer to slowing down the risk from guard rotation, and fixes a variety of other issues to get us closer to a release candidate”.

Once directory authorities have upgraded, they will “assign the Guard flag to the fastest 25% of the network”. Some experiments showed that “for the current network, this results in about 1100 guards, down from 2500.”

The complementary change to [moving the number of entry guards down to one](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/236-single-guard-node.txt) is the introduction of two new consensus parameters. _NumEntryGuards_ and _NumDirectoryGuards_ will respectively set the number of entry guards and directory guards that clients will use. The default for _NumEntryGuards_ is currently three, but this will allow a reversible switch to one in a near future.

Several important fixes have been backported to the stable branch in the [0.2.4.23 release](https://lists.torproject.org/pipermail/tor-announce/2014-July/000093.html). Source packages are available at the regular location . Binary packages have already landed in Debian ( [unstable](https://tracker.debian.org/news/560607), [experimental](https://tracker.debian.org/news/560611)) and the rest should follow shortly.

# Security issue in Tails 1.1 and earlier

[Several vulnerabilities have been discovered in I2P which is shipped in Tails 1.1 and earlier](https://tails.boum.org/security/Security_hole_in_I2P_0.9.13/). [I2P](https://geti2p.net/) is an anonymous overlay network with many similarities to Tor. There was quite some confusion around the disclosure process of this vulnerability. Readers are encouraged to read [what the Tails team has written about it](https://tails.boum.org/news/On_0days_exploits_and_disclosure/).

Starting I2P in Tails normally requires a click on the relevant menu entry. Once started, the security issues can lead to the deanonymization of a Tails user who visits a malicious web page. As a matter of precaution, the Tails team recommends removing the “i2p” package each time Tails is started.

I2P has fixed the issue in [version 0.9.14](https://geti2p.net/en/blog/post/2014/07/26/0.9.14-Release). It is likely to be included in the next Tails release, but the team is also [discussing](https://mailman.boum.org/pipermail/tails-dev/2014-July/006459.html) implementing more in-depth protections that would be required in order to keep I2P in Tails.

# Reporting bad relays

“Bad” relays are malicious, misconfigured, or otherwise broken Tor relays. As anyone is free to volunteer bandwidth and processing power to spin up a new relay, users can encounter such bad relays once in a while. Getting them out of everyone’s circuits is thus important.

Damian Johnson and Philipp Winter have been working on [improving and documenting](https://trac.torproject.org/projects/tor/wiki/doc/ReportingBadRelays) the process of reporting bad relays. “While we do regularly scan the network for bad relays, we are also dependent on the wider community to help us spot relays which don’t act as they should” [wrote](https://blog.torproject.org/blog/how-report-bad-relays) Philipp.

When observing unusual behaviors, one way to learn about the current exit relay before reporting it is to use the [Check](https://check.torproject.org/) service. This method can be inaccurate and tends to be a little bit cumbersome. The good news is that Arthur Edelstein is [busy integrating](https://trac.torproject.org/projects/tor/ticket/8641#comment:12) more feedback on Tor circuits being used directly into the Tor Browser.

# Miscellaneous news

The Tor Project, Inc. has completed its [standard financial audit for the year 2013](https://blog.torproject.org/blog/transparency-openness-and-our-2013-financials). [IRS Form 990](https://www.torproject.org/about/findoc/2013-TorProject-Form990.pdf), [Massachusetts Form PC](https://www.torproject.org/about/findoc/2013-TorProject-FormPC.pdf), and the [Financial Statements](https://www.torproject.org/about/findoc/2013-TorProject-FinancialStatements.pdf) are now available for anyone to review. Andrew Lewman explained: “we publish all of our related tax documents because we believe in transparency. All US non-profit organizations are required by law to make their tax filings available to the public on request by US citizens. We want to make them available for all.”

CJ [announced](https://lists.torproject.org/pipermail/tor-talk/2014-July/034006.html) the release of [orWall](https://orwall.org/) (previously named Torrific), a new Android application that “will force applications selected through Orbot while preventing unchecked applications to have network access”.

The [Thali project](http://www.thaliproject.org/mediawiki/index.php?title=Main_Page) aims to use hidden services to host web content. As part of the effort, they have written a [cross-platform Java library](https://github.com/thaliproject/Tor_Onion_Proxy_Library). “The code handles running the binary, configuring it, managing it, starting a hidden service, etc.” [wrote](https://lists.torproject.org/pipermail/tor-talk/2014-July/034046.html) Yaron Goland.

Gareth Owen [released](https://lists.torproject.org/pipermail/tor-dev/2014-July/007232.html) a Java-based Tor research framework . The goal is to enable researchers to try things out without having to deal with the full tor source. “At present, it is a fully functional client with a number of examples for hidden services and SOCKS. You can build arbitrary circuits, build streams, send junk cells, etc.” wrote Gareth.

Version 0.2.3 of [BridgeDB](https://bridges.torproject.org/) has been deployed. Among other [changes](https://gitweb.torproject.org/bridgedb.git/blob/2a6d5463:/CHANGELOG), [owners of riseup.net email accounts can now request bridges through email](https://bugs.torproject.org/11139#comment:15).

The first candidate for Orbot 14.0.5 has been released. “This update includes improved management of the background processes, the ability to easily change the local SOCKS port (to avoid conflicts on some Samsung Galaxy and Note devices), and the fancy new notification dialog, showing your current exit IPs and country” [wrote](https://lists.mayfirst.org/pipermail/guardian-dev/2014-July/003667.html) Nathan Freitas.

While working on guard nodes, George Kadianakis realized that “the data structures and methods of the guard nodes code are not very robust”. Nick Mathewson and George have been busy trying to [come up with better abstractions](https://bugs.torproject.org/12595). More brains working on the problem would be welcome!

Mike Perry [posted](https://lists.torproject.org/pipermail/tor-dev/2014-July/007246.html) “a summary of the primitives that Marc Juarez aims to implement for his Google Summer of Code project on prototyping defenses for Website Traffic Fingerprinting and follow-on research”. Be sure to have a look if you want to help prevent website fingerprint attacks.

A new draft proposal “for making all relays also be directory servers (by default)” has been [submitted](https://lists.torproject.org/pipermail/tor-dev/2014-July/007247.html) by Matthew Finkel. Among the motivations, Matthew wrote: “In a network where every router is a
directory server, the profiling and partitioning attack vector is reduced to the guard (for clients who use them), which is already in a privileged position for this. In addition, with the increased set size, relay descriptors and documents are more readily available and it diversifies the providers.” This change might make the transition to a single guard safer. Feedback welcome!

Noah Rahman [reported](https://lists.torproject.org/pipermail/tor-dev/2014-July/007248.html) on the progress of the Stegotorus Google Summer of Code project.

# Tor help desk roundup

A number of Iranian Tor users have reported that Tor no longer works out of the box in Iran, and the Tor Metrics portal shows a corresponding [drop in the number of directly-connecting users there](https://metrics.torproject.org/users.html?graph=userstats-relay-country&start=2014-04-30&end=2014-07-28&country=ir&events=on#userstats-relay-country). Collin Anderson investigated the situation and reported that the Telecommunication Company of Iran had begun [blocking the Tor network by blacklisting connections to Tor’s directory authorities](https://bugs.torproject.org/12727). Tor users can circumvent this block by getting bridges from [BridgeDB](https://bridges.torproject.org/) and entering the bridge addresses they receive into their Tor Browser.

* * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, harmony, and Philipp Winter.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

