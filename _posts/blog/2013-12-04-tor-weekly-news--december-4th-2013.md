---
layout: post
title: "Tor Weekly News — December 4th, 2013"
permalink: tor-weekly-news--december-4th-2013
date: 2013-12-04 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the twenty-third issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Next-Generation Hidden Services reach draft proposal state
==========================================================

Nick Mathewson has been working on turning a “revamp of the hidden services protocol” into a [formal proposal](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/001-process.txt). Last Saturday, Nick blessed the tor-dev mailing list with a post of the [current draft for proposal 224](https://lists.torproject.org/pipermail/tor-dev/2013-November/005877.html), dubbed “Next-Generation Hidden Services in Tor”.

Nick currently lists 25 different people who made writing the new proposal possible, and there will be probably some more to add before the proposal reaches completion. We will spare the reader a full list, but [Tor Weekly News’ archives](https://blog.torproject.org/category/tags/tor-weekly-news) attest that George Kadianakis deserves a special mention for his repeated efforts to move things forward.

The proposal aims to replace “the [current rend-spec.txt](https://gitweb.torproject.org/torspec.git/blob/refs/heads/master:/rend-spec.txt), rewritten for clarity and for improved design.” The most user visible change from the current hidden services protocol is the new address format. In order to prevent the enumeration of hidden services, the new protocol derives a “blinded key” (section 1.3) from an Ed25519 master identity key. The blinding operation operates on the full key (and not just a truncated hash, as before). With a base 32 encoding of the entire 256 bits (section 1.2), “a new name following this specification might look like: `a1uik0w1gmfq3i5ievxdm9ceu27e88g6o7pe0rffdw9jmntwkdsd.onion`”. Other encodings might still be worth consideration as long as they make valid hostnames.

Less visible changes include the departure from RSA1024, DH1024, and SHA1 to prefer Ed25519, Curve25519, and SHA256 as the cryptographic primitives (section 0.3).

The selection of directories responsible for a hidden service will now depend on a periodic “collaboratively generated random value” provided by the Tor directory authorities. This way the directories of a hidden service are not predictable in advance, which prevents targeted denial of service attacks (see [ticket \#8244](https://bugs.torproject.org/8244) and [proposal 225](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/225-strawman-shared-rand.txt) for a possible scheme).

The new proposal also introduces the possibility of keeping the master identity key offline (section 1.7).

The proposal is completely unfinished when it comes to scaling hidden services to multiple hosts (section 1.5). There have been [discussions on this topic](https://lists.torproject.org/pipermail/tor-dev/2013-October/005556.html), but there is no final decision on what the final scheme should be. The problem with naive scaling schemes is that information about the number of hidden service nodes can leak to adversarial clients or introduction points.

In order to move the proposal forward from the current draft, Nick Mathewson told the readers: “I’d like to know what doesn’t make sense, what I need to explain better, and what I need to design better. I’d like to fill in the gaps and turn this into a more full document. I’d like to answer the open questions. Comments are most welcome, especially if they grow into improvements.” The document is still sprinkled with many TODO items, so feel free to jump in if you want to help!

Tor relay operators meeting at 30C3
===================================

Moritz Bartl [announced](https://lists.torproject.org/pipermail/tor-relays/2013-December/003449.html) that a meeting of Tor relay operators and organizations will be held as part of the first day of the 30th Chaos Communication Congress in Hamburg on the 27th December. He asked major relay operators and Torservers.net partner organizations to prepare some slides explaining their activities; the German partner organization, Zwiebelfreunde e.V., will hold its own meeting directly afterwards.

Monthly status reports for November 2013
========================================

The wave of regular monthly reports from Tor project members for the month of November has begun. [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2013-November/000387.html) released their report first , followed by reports from [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2013-December/000388.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2013-December/000389.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2013-December/000390.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2013-December/000391.html), [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2013-December/000393.html), [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2013-December/000394.html), and [Ximin Luo](https://lists.torproject.org/pipermail/tor-reports/2013-December/000395.html).

Miscellaneous news
==================

The [first release candidate for Tails 0.22](https://tails.boum.org/news/test_0.22-rc1/) is out. The new version features a browser based on Firefox 24 and has reached beta stage for incremental updates, among other things. Tests are most welcome, as always!

The Tails team called for translators to help with the strings both [for Tails 0.22](https://mailman.boum.org/pipermail/tails-l10n/2013-December/000774.html), as well as [for the new incremental upgrade software](https://mailman.boum.org/pipermail/tails-l10n/2013-November/000771.html). The strings for translation are now available in the [Tails Git repository](https://git-tails.immerda.ch/iuk/), and hopefully should also be up [on Transifex](https://www.transifex.com/projects/p/torproject/) soon.

Damian Johnson sent out a link to a [recording of his talk on the Tor ecosystem](https://lists.torproject.org/pipermail/tor-dev/2013-November/005867.html) at TA3M in Seattle.

David Goulet [called for assistance](https://lists.torproject.org/pipermail/tor-dev/2013-November/005870.html) with the code-review process for the Torsocks 2.0 release candidate, and offered some guidance on where to begin.

Erinn Clark and Peter Palfrader [upgraded the Tor Bug Tracker & Wiki to Trac version 1.0](https://lists.torproject.org/pipermail/tor-dev/2013-November/005871.html).

intrigeri [began](https://mailman.boum.org/pipermail/tails-dev/2013-November/004353.html) compiling a [glossary](https://tails.boum.org/contribute/glossary/) of words that Tails and its developers use for particular concepts, to assist contributors who might not be familiar with these special meanings.

In order to remove “a full database of relays on our already overloaded metrics machine”, Karsten Loesing is [asking for those using the “relay-search service” to speak up](https://lists.torproject.org/pipermail/tor-talk/2013-December/031310.html) before the decommissioning of the service by the end of the year.

Philipp Winter followed up on his [experiments in exit scanning](https://lists.torproject.org/pipermail/tor-dev/2013-November/005863.html)and released [exitmap](https://github.com/NullHypothesis/exitmap), which uses Stem to control the tor daemon in creating circuits to all exit nodes.

[Orchid](http://www.subgraph.com/orchid.html), a Tor client implementation written in pure Java, silently reached the 1.0 milestone on November 27th. Nathan Freitas is [looking for comment](https://lists.torproject.org/pipermail/tor-dev/2013-November/005884.html) from the community as he is “thinking about having Orbot use it by default, and then offering ARM and x86 binaries as add-on enhancements.” His main argument is that it “would make the core Tor on Android experience more lightweight for client only use.”

The Electronic Frontier Foundation helped a student group in Iowa convince their university that they should be allowed to hold discussions about Tor on campus. The EFF’s [open letter to universities](https://www.eff.org/deeplinks/2013/12/open-letter-urging-universities-encourage-conversation-about-online-privacy) and their [“Myths and Facts About Tor”](https://www.eff.org/document/tor-myths-and-facts) document make useful advocacy material.

Tor help desk roundup
=====================

Multiple users asked about using Tor for PC gaming. Tor can only transport TCP, which is how web pages are transmitted. Many video games rely on UDP or other protocols to transport data because of the lower latency. Information these games transport over protocols besides TCP would not be sent over Tor. Also any software used with Tor needs to be tested for proxy obedience. Untested applications might send information without using Tor even if they appear to be configured correctly, and  
 without the user realizing it.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, dope457, George Kadianakis, Nick Mathewson, sqrt2 and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
