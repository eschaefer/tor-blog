---
layout: post
title: "Tor Weekly News — July, 31st 2013"
permalink: tor-weekly-news-%E2%80%94-july-31st-2013
date: 07/31/2013
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the 5<sup>th</sup> issue of Tor Weekly News, the weekly newsletter that covers what is happening in the busy Tor community.

# Summer Developer Meeting Wrap-up

The 2013 summer Tor development meeting happened at the [Technische Universität München](http://www.tum.de/). There were no formal talks during the meeting itself, but [slides were still involved](https://commons.wikimedia.org/wiki/File:050322-tumuenchen-parabeln.jpg)!

New minutes from sessions to add to those covered in the [last edition](https://blog.torproject.org/blog/tor-weekly-news-%E2%80%94-july-24th-2013) have been [posted to the wiki](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting). This includes a second discussion on [Pluggable Transports](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/PluggableTransports1), the role of the [Research Director](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/ResearchDirector), a summary of discussions with cryptographers Tanja Lange and djb about the [cryptographic aspects of Tor](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/TorCrypto), [timesheets for Tor contractors](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/Timesheets) and [mailing-lists](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/MailingLists).

Christian Grothoff organized a talk with Roger Dingledine and Jacob Appelbaum at the university. Their initial topic was the censorship arms race, but given the up-to-date knowledge of the students and other attendees, the talk got turned into a marathon 4-hour long Q&A session! Thanks to Christian, the [video is available](https://gnunet.org/tor2013tum-video) from the GNUnet website.

The following day was dedicated to more concrete hands-on discussions and coding. The public hackfest was well-attended, with more than 70 people focusing on everything to do with Tor. Some attendees had even traveled several hundred kilometers to be there! Discussions popped up everywhere, code was written and some newcomers were introduced to the many elements that make up the Tor project. Thanks to everyone who showed up!

# Comparing handshake protocols for Tor: Ace vs ntor

In WPES ’12, Esfandiar Mohammadi and Aniket Kate [introduced](https://lists.torproject.org/pipermail/tor-dev/2012-August/003901.html) [Ace, an alternative for Tor’s current handshake protocol ntor](http://www.infsec.cs.uni-saarland.de/~mohammadi/paper/owake.pdf).

Ace was already [discussed on tor-dev at the end of 2012](https://lists.torproject.org/pipermail/tor-dev/2013-July/005163.html), “but back then, no implementation for the double scalar multiplication operation (a \* b + c \* d) on Curve25519 was available. But recently, Robert Ransom implemented in his [celator library](http://www.infsec.cs.uni-saarland.de/~mohammadi/ace/celator.tar.gz) a highly efficient double scalar multiplication which is suitable for our handshake protocol Ace”, wrote Esfandiar.

From the comparative benchmarks that Shivanker Goel implemented and ran, using Ace could improve speed and CPU load compared to the current ntor implementation. Esfandiar Mohammadi’s email on tor-talk contains the methodology, remarks and concrete numbers.

The code for the [benchmark is available online](http://www.infsec.cs.uni-saarland.de/~mohammadi/ace/ace-benchmarks.tar.gz) along with a [Tor-style proposal or improving circuit-creation key exchange using Ace](http://www.infsec.cs.uni-saarland.de/~mohammadi/ace/ace-handshake.txt).

# New Globe web application to explore the Tor network

Christian made his [Globe web application available](http://globe.rndm.de/) at a new location. Globe is quite similar to [Atlas](https://atlas.torproject.org), and in fact uses the same data, but it also allows searching for bridges and is slightly more user-friendly.

Globe now uses dygraphs as a graphing engine which makes it even easier to select time intervals for its graphs. Feel free to try out Globe and give feedback on [its bug tracker](https://github.com/makepanic/globe/issues).

# Tor at OHM2013 — Netherlands

Several members of the Tor community will be at OHM2013: Observe, Hack, Make: “A five day outdoor international camping festival for hackers, makers, and those with an inquisitive mind”, according to [their website](https://ohm2013.org/). The event starts tomorrow with a few Tor-related meetings and activities.

Tom Lowenthal will be holding a [social event](https://program.ohm2013.org/event/307.html) at the Noisy Square village for Tor contributors and relay operators on August, 1st at 14:00.

Later that day, Tom will also go through “the development work, advocacy help, coordination, system administration, outreach, community support, and other [things that you can do to help the Tor Project](https://program.ohm2013.org/event/305.html) grow and improve” in the Lovelace Tent at 22:00.

Fabio Pietrosanti invited anyone interested to attend the [Tor2Web meeting](https://program.ohm2013.org/event/256.html) to: “outlook what we’ve done, how the network growth up discussing which could be the next major milestones to be reached in terms of software, network development, community involvement and fundraising.”

Last but not least, Moritz Bartl from torservers.net will be around with Tor stickers and posters, as well as collecting donations to create new exit nodes. Look around the [Noisy Square](https://noisysquare.com/)!

# Miscellaneous development news

GSoC students sent out a new round of status reports. Johannes Fürmann had made great progress on the framework for [EvilGenius](https://lists.torproject.org/pipermail/tor-dev/2013-July/005179.html) — a way to simulate censorship events: “The Genius is there, all we have to do now is make it more evil.”

Cristian-Matei Toader is moving forward on [limiting the set of allowed system calls by the tor daemon](https://lists.torproject.org/pipermail/tor-dev/2013-July/005180.html).

ra\_ sucessfully now has a “rttprober” script to [measure the RTT of Tor circuits](https://lists.torproject.org/pipermail/tor-dev/2013-July/005181.html).

Kostas Jakeliunas has a clean code base for the Tor Metrics Archive project that can import archival data and be queried with an Onionoo-like interface.

Hareesan did a quick report on the [steganography browser extension](https://lists.torproject.org/pipermail/tor-dev/2013-July/005185.html).

Chang Lan Status has returned to report some progress on the [HTTP pluggable transport](https://lists.torproject.org/pipermail/tor-dev/2013-July/005193.html).

[Karsten Loesing added a new “fields” parameter to Onionoo](https://gitweb.torproject.org/onionoo.git/commit/1c1dfa48). It can be used to restrict the response size when only a specific set of attributes are needed. This feature is used by the [bubble graphs](https://metrics.torproject.org/bubbles.html) showing diversity of the Tor network wrote by Lunar. The latter are now available on the metrics website, thanks to Karsten.

Kevin P Dyer released [Format-Transforming Encryption Pluggable Transport version v0.1.2-alpha](https://lists.torproject.org/pipermail/tor-dev/2013-July/005194.html). Source code, documentation and builds are available on the [FTE website](https://kpdyer.com/fte/).

[Damian Johnson has released two new monitoring scripts](https://lists.torproject.org/pipermail/tor-dev/2013-July/005209.html) based on the remote descriptor fetching support recently added to [Stem](https://stem.torproject.org/): one to check for malformed content in the descriptors, the other to monitor sudden influxes of new relays (potential Sybil attacks).

* * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, malaparte, harmony, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing-list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

