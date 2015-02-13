---
layout: post
title: "Tor Weekly News — September 4th, 2013"
permalink: tor-weekly-news--september-4th-2013
date: 2013-09-04 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the tenth issue of Tor Weekly News, the weekly newsletter that covers what is happening in the skyrocketing Tor community.

Serious network overload
========================

> \<borealis\> if it really is a coordinated attack from a bot twice the size of the regular tor network i'm much surprised tor is still usable at all

— borealis in \#tor, 2013-09-02 18:38 UTC

  

The tremendous [influx of new clients that started mid-August](https://metrics.torproject.org/users.html?graph=direct-users&start=2013-08-15&end=2013-09-02#direct-users) is stretching the current Tor network and software to its limits.

Several relay operators [reported their relays to be saturated](https://lists.torproject.org/pipermail/tor-relays/2013-August/002594.html) by the amount of connections and circuits that [relays currently have to handle](https://lists.torproject.org/pipermail/tor-relays/2013-August/002589.html).

Mike Perry wishing to “compare load characteristics since 8/19 for nodes with different types of flags” issued a [call to relay operators](https://lists.torproject.org/pipermail/tor-relays/2013-August/002612.html): “especially useful [are] links/graph images for connection counts, bandwidth, and CPU load since 8/19.”

It was reported on IRC that on some relays, only one circuit was successfully created out of four attempts. This unfortunately implies that clients retry to build more circuits, resulting in even more load on Tor relays.

The tor 0.2.4 series introduced a new circuit extension handshake dubbed “[ntor](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/216-ntor-handshake.txt)”. This new handshake is faster (especially on the relay side) than the original circuit extension handshake, “TAP”. Roger Dingledine came up with a [patch to prioritize circuit creations using ntor over TAP](https://bugs.torproject.org/9574#comment:10). Various observers reported that these overwhelming unidentified new clients were likely to be using Tor 0.2.3. Prioritizing ntor is then likely to make them less a burden for the network, and should help the network to function despite being overloaded by circuit creations.

Sathya and Isis both reported the patch to work. Nick Mathewson pointed out a [few issues](https://bugs.torproject.org/9574#comment:12) in the current implementation but overall it looks like a band-aid good enough for the time being.

Latest findings regarding traffic correlation attacks
=====================================================

Erik de Castro Lopo [pointed tor-talk readers](https://lists.torproject.org/pipermail/tor-talk/2013-September/029755.html) to a new well written paper named [Users Get Routed: Traffic Correlation on Tor by Realistic Adversaries](http://www.ohmygodel.com/publications/usersrouted-ccs13.pdf). To be presented at the upcoming [CCS 2013 conference](http://www.sigsac.org/ccs/CCS2013/) this November in Berlin, Aaron Johnson, Chris Wacek, Rob Jansen, Micah Sherr, and Paul Syverson describe their experiments on traffic correlation attacks.

This research paper follows on a long series of earlier research papers to better understand how Tor is vulnerable to adversaries controlling portions of the Tor network or monitoring users and relays at the network level.

Roger Dingledine [wrote to tor-talk readers](https://lists.torproject.org/pipermail/tor-talk/2013-September/029756.html): “Yes, a big enough adversary can screw Tor users. But we knew that. I think it’s great that the paper presents the dual risks of relay adversaries and link adversaries, since most of the time when people are freaking out about one of them they’re forgetting the other one. And we really should raise the guard rotation period. If you do their compromise graphs again with guards rotated every nine months, they look way different.”

One tricky question with [raising guard rotation period](https://bugs.torproject.org/8240) is: “How do we [keep clients properly balanced](https://bugs.torproject.org/9321) to match the guard capacities?” It is also probably another signal for any Tails supporter that wishes to help implementing [guard persistence](https://labs.riseup.net/code/issues/5462).

“I have plans for writing a blog post about the paper, to explain what it means, what it doesn’t mean, what we should do about it, and what research questions remain open” wrote Roger. Let’s stay tuned!

A peek inside the Pirate Browser
================================

Torrent-sharing website The Pirate Bay started shipping a custom browser — the Pirate Browser — on August 10th. They advertised using Tor to circumvent censorship but unfortunately did not provide any source code for their project.

Matt Pagan [examined the contents of the package](https://lists.torproject.org/pipermail/tor-talk/2013-August/029703.html) in order to get a better idea of what it was. He compared the contents of the Pirate Browser 0.6b archive using cryptographic checksums to the contents of the Tor Browser Bundle 2.3.25-12 (en-US version).

According to Matt’s findings the Pirate Browser includes unmodified versions of tor 0.2.3.25 and Vidalia 0.2.20. The tor configuration contains slight deviation from the one shipped with the Tor Browser Bundle. One section labeled “Configured for speed” unfortunately shows wrong understanding of the Tor network. Roger Dingledine [commented in a subsequent email](https://lists.torproject.org/pipermail/tor-talk/2013-August/029729.html): “Just for the record, the three lines here don’t help speed much (or maybe at all).”

The remaining configuration change that “probably has the biggest impact on performance“, according to Roger, excludes exit nodes from Denmark, Ireland, United Kindgom, the Netherlands, Belgium, Italy, China, Iran, Finland, and Norway. “Whether it improves or reduces performance [Roger] cannot say, though. Depends on a lot of complex variables around Internet topologies.”

The browser itself is based of Firefox 23.0, with FoxyProxy configured to use Tor only for a [few specific addresses](http://piratebrowser.com/piratebrowser_patterns.json), and a few extra bookmarks.

Later, Matt [also highlighted](https://lists.torproject.org/pipermail/tor-talk/2013-August/029707.html) that some important extensions of the Tor Browser, namely HTTPS Everywhere, NoScript, and Torbutton were also missing from the Pirate Browser.

In any cases, the Pirate Browser is unlikely to explain the sudden influx of new Tor clients. grarpamp forwarded [an email exchanged with the Pirate Browser admin contact](https://lists.torproject.org/pipermail/tor-talk/2013-August/029736.html) which shows that numbers (550 000 known direct downloads) and dates (“most downloads during the first week”) do not match.

Monthly status reports for August 2013
======================================

The wave of regular monthly reports from Tor project members for the month of August has begun. [Sherief Alaa released his report first](https://lists.torproject.org/pipermail/tor-reports/2013-September/000314.html), followed by reports from [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2013-September/000315.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2013-September/000316.html), [Arturo Filastò](https://lists.torproject.org/pipermail/tor-reports/2013-September/000317.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2013-September/000318.html), [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2013-September/000319.html), [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2013-September/000320.html), [Roger Dingledine](https://lists.torproject.org/pipermail/tor-reports/2013-September/000321.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2013-September/000322.html), and [Isis Lovecruft](https://lists.torproject.org/pipermail/tor-reports/2013-September/000323.html). The latter also caught up with [June](https://lists.torproject.org/pipermail/tor-reports/2013-September/000324.html), and [July](https://lists.torproject.org/pipermail/tor-reports/2013-September/000325.html).

Help Desk Roundup
=================

This week Tor help desk saw an increase in the number of users wanting to download or install Orbot. Orbot can be downloaded from the Google Play store, the Amazon App store, f-droid.org, and guardianproject.info. Guides on using Orbot can be found on the [Guardian Project’s Orbot page](https://guardianproject.info/apps/orbot/), or on the [Tor Project’s Android page](https://www.torproject.org/docs/android.html). It looks like Orbot is currently inaccessible from the Google Play store in Iran. Please join the [discussion on tor-talk](https://lists.torproject.org/pipermail/tor-talk/2013-August/029684.html) if you have input about the latter.

All versions of the Tor Browser Bundle which include tor 0.2.4.x have been reported to work in Iran. This includes the latest Pluggable Transport Bundle, the 3.0 alpha series, and the 2.4 beta series. Follow [our Farsi blog](https://fa-blog.torproject.org/) for more Iran related news.

Miscellaneous news
==================

The [next Tails contributors meeting](https://mailman.boum.org/pipermail/tails-dev/2013-August/003523.html) will happen on IRC on September 4th at 8pm UTC (10pm CEST). “Every one interested in contributing to Tails is welcome” to join \#tails-dev on the OFTC network.

Yawning Angel has been “designing a UDP based protocol to serve as the bulk data transport for something along the lines of ‘obfs3, but over UDP’.” They are soliciting feedback on their [initial draft of the Lightweight Obfuscated Datagram Protocol (LODP)](https://lists.torproject.org/pipermail/tor-dev/2013-August/005334.html).

Kévin Dunglas [announced](https://lists.torproject.org/pipermail/tor-dev/2013-August/005340.html) their work on a [PHP library for the Tor Control Port](https://github.com/dunglas/php-torcontrol/), released under the MIT license.

Kathy Brade and Mark Smith have [released a first patch](https://bugs.torproject.org/4234#comment:19) for Mozilla’s update mechanism which “successfully updated TBB on Linux, Windows, and Mac OS ‘in the lab’ using both incremental and ‘full replace’ updates.” This is meant for the 3.x series of the Tor Browser Bundle and is still a work a progress, but this is a significant milestone toward streamlined updates for TBB users.

Erinn Clark [announced](https://lists.torproject.org/pipermail/tor-dev/2013-August/005328.html) that the software powering trac.torproject.org has been upgraded to version 0.12.3. Among several other improvements, this new version allowed Erinn to [experiment with the often requested Git integration](https://lists.torproject.org/pipermail/tor-dev/2013-September/005346.html).

David Goulet has [released the second release candidate](https://lists.torproject.org/pipermail/tor-dev/2013-September/005359.html) for the 2.0 rewrite of Torsocks [43]: “Please continue to test, review and contribute it!”

Much to her surprise, Erinn Clark found a “[fraudulent PGP key with [her] email address](https://lists.torproject.org/pipermail/tor-dev/2013-September/005348.html)” on the keyservers. “Do not under any circumstances trust anything that may have ever been signed or encrypted with this key” of short id 0xCEE1590D. She reminded that the Tor Project official signatures are [listed on the project’s website](https://www.torproject.org/docs/signing-keys.html).

Philipp Winter published [the final paper version](http://www.cs.kau.se/philwint/pdf/wpes2013.pdf) of the [ScrambleSuit pluggable transport](http://www.cs.kau.se/philwint/scramblesuit/), dubbed “A Polymorphic Network Protocol to Circumvent Censorship”.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, mttp, malaparte, mrphs, bastik, Karsten Loesing, and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
