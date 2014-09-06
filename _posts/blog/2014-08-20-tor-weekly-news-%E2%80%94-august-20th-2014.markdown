---
layout: post
title: "Tor Weekly News — August 20th, 2014"
permalink: blog/tor-weekly-news-%E2%80%94-august-20th-2014
date: 2014-08-20
author: harmony
category: blog
tags: ["tor weekly news"]
---

Welcome to the thirty-third issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the community around Tor, [Aphex Twin’s favorite anonymity network](https://www.dailydot.com/entertainment/aphex-twin-deep-web-album-syro/).

# Tor Browser 3.6.4 and 4.0-alpha-1 are out

Erinn Clark took to the [Tor Blog](https://blog.torproject.org/blog/tor-browser-364-and-40-alpha-1-are-released) to announce two new releases by the Tor Browser team. The stable version (3.6.4) contains fixes for several new OpenSSL bugs, although since Tor should only be vulnerable to one of them, and “as this issue is only a DoS”, it is not considered a critical security update. This release also brings Tor Browser users the fixes that give log warnings about the RELAY\_EARLY traffic confirmation attack explained [last month](https://blog.torproject.org/blog/tor-security-advisory-relay-early-traffic-confirmation-attack). Please be sure to upgrade as soon as possible.

Alongside this stable release, the first alpha version of Tor Browser 4.0 is now available. Among the most exciting new features of this series is the inclusion of the [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek) pluggable transport. In contrast to the bridge-based transports already available in Tor Browser, meek relies on a principle of “too big to block”, as its creator David Fifield [explained](https://blog.torproject.org/blog/how-use-%E2%80%9Cmeek%E2%80%9D-pluggable-transport#comment-70044): “instead of going through a bridge with a secret address, you go through a known domain ( [www.google.com](http://www.google.com "www.google.com") for example) that the censor will be reluctant to block. You don’t need to look up any bridge addresses before you get started”. meek currently supports two “front domains”, Google and Amazon Web Services; it may therefore be especially useful for users behind extremely restrictive national or local firewalls. David posted a fuller explanation of meek, and how to configure it, in a [separate blog post](https://blog.torproject.org/blog/how-use-%E2%80%9Cmeek%E2%80%9D-pluggable-transport).

This alpha release also “paves the way to [the] upcoming autoupdater by reorganizing the directory structure of the browser”, as Erinn wrote. This means that users upgrading from any previous Tor Browser series cannot extract the new version over their existing Tor Browser folder, or it will not work.

You can consult the full list of changes and bugfixes for both versions in Erinn’s post, and download the new releases themselves from the [Tor website](https://www.torproject.org/dist/torbrowser/).

# The Tor network no longer supports designating relays by name

Since the [very first versions of Tor](https://gitweb.torproject.org/tor.git/blob/161d7d1:/src/config/torrc.in#l20), relay operators have been able to specify “nicknames” for their relays. Such nicknames were initially meant to be unique across the network, and operators of directory authorities would manually “bind” a relay identity key after verifying the nickname. The process became formalized with the “Named” flag introduced in the [0.1.1 series](https://gitweb.torproject.org/torspec.git/blob/HEAD:/attic/dir-spec-v2.txt#l427), and later automated with the 0.2.0 series. If a relay held a unique nickname for long enough, the authoritywould recognize the binding, and subsequently reserve the name for half a year.

Nicknames are useful because it appears humans are not very good at thinking using long strings of random bits. Initially, they made it possible to understand what was happening in the network more easily, and to designate a specific relay in an abbreviated way. Having two relays in the network with the same nickname is not really problematic when one is looking at nodes, or a list in [Globe](https://globe.torproject.org/#/search/query=Unnamed), as relays can always be differentiated by their IP addresses or identity keys.

But complications arise when nicknames are used to specify one relay to the exclusion of another. If the wrong relay gets selected, it can become a security risk. Even though [real efforts](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/122-unnamed-flag.txt) have been made to improve the situation, properly enforcing uniqueness has always been problematic, and a burden for the few directory authorities that handle naming.

Back in April, the [“Heartbleed” bug](https://blog.torproject.org/blog/openssl-bug-cve-2014-0160) forced many relays to switch to a new identity key, thus losing their “Named” flag. Because this meant that anyone designating relays by their nickname would now have a hard time continuing to do so, Sebastian Hahn decided to use the opportunity to [get rid of the idea entirely](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/235-kill-named-flag.txt).

This week, Sebastian [wrote](https://lists.torproject.org/pipermail/tor-dev/2014-August/007348.html): “Code review down to 0.2.3.x has shown that the naming-related code hasn’t changed much at all, and no issues were found which would mean a Named-flag free consensus would cause any problems. gabelmoo and tor26 have stopped acting as Naming Directory Authorities, and — pending any issues — will stay that way.”

This means that although you can still give your relay a nickname in its configuration file, designating relays by nickname for any other purpose (such as telling Tor to avoid using certain nodes) has now stopped working. “If you — in your Tor configuration file — refer to any relay by name and not by identity hash, please change that immediately. Future versions of Tor will not support using names in the configuration at all”, [warns Sebastian](https://lists.torproject.org/pipermail/tor-talk/2014-August/034380.html).

# Miscellaneous news

meejah [announced](https://lists.torproject.org/pipermail/tor-dev/2014-August/007375.html) the release of version 0.11.0 of txtorcon, a Twisted-based Python controller library for Tor. This release brings several API improvements; see meejah’s message for full release notes and instructions on how to download it.

Mike Perry posted an [overview](https://blog.torproject.org/blog/isec-partners-conducts-tor-browser-hardening-study) of a recent report put together by iSEC Partners and commissioned by the Open Technology Fund to explore “current and future hardening options for the Tor Browser”. Among other things, Mike’s post addresses the report’s immediate hardening recommendations, latest thoughts on the proposed Tor Browser “security slider”, and longer-term security development measures, as well as ways in which the development of Google Chrome could inform Tor Browser’s own security engineering.

Nick Mathewson asked for [comments](https://lists.torproject.org/pipermail/tor-dev/2014-August/007355.html) on Trunnel, “a little tool to automatically generate binary encoding and parsing code based on C-like structure descriptions” intended to prevent “Heartbleed”-style vulnerabilities from creeping into Tor’s binary-parsing code in C. “My open questions are: Is this a good idea? Is it a good idea to use this in Tor? Are there any tricky bugs left in the generated code? What am I forgetting to think of?”, wrote Nick.

George Kadianakis followed up his [journey to the core](https://lists.torproject.org/pipermail/tor-dev/2014-June/007042.html) of what Tor does when trying to connect to entry guards in the absence of a network connection with [another post](https://lists.torproject.org/pipermail/tor-dev/2014-August/007346.html) running through some possible improvements to Tor’s behavior in these situations: “I’m looking forward to some feedback on the proposed algorithms as well as improvements and suggestions”.

Arturo Filastò [requested feedback](https://lists.torproject.org/pipermail/tor-dev/2014-August/007353.html) on some proposed changes to the format of the “test deck” used by ooni-probe, the main project of the Open Observatory of Network Interference. “A test deck is basically a way of telling it ‘Run this list of OONI tests with these inputs and by the way be sure you also set these options properly when doing so’…This new format is supposed to overcome some of the limitations of the old design and we hope that a major redesign will not be needed in the near future”, wrote Arturo.

Tor’s importance to users who are at risk, for a variety of reasons, makes it an attractive target for creators of malware, who distribute fake or modified versions of Tor software for malicious purposes. Following a recent report of a fake Tor Browser in circulation, Julien Voisin carried out an investigation of the compromised software, and posted a [detailed analysis](http://dustri.org/b/torbundlebrowserorg.html) of the results. To ensure you are protected against this sort of attack, make sure you [verify](https://www.torproject.org/docs/verifying-signatures) any Tor software you download before running it!

Arlo Breault submitted a [status report for July](https://lists.torproject.org/pipermail/tor-reports/2014-August/000622.html).

As the annual Google Summer of Code season draws to a close, Tor’s GSoC students are submitting their final reports. Israel Leiva reported on the [revamp of GetTor](https://lists.torproject.org/pipermail/tor-dev/2014-August/007368.html), Marc Juarez on the [framework for website fingerprinting countermeasures](https://lists.torproject.org/pipermail/tor-reports/2014-August/000623.html), Juha Nurmi on [ahmia.fi](https://lists.torproject.org/pipermail/tor-reports/2014-August/000624.html), Noah Rahman on [Stegotorus enhancement](https://lists.torproject.org/pipermail/tor-dev/2014-August/007377.html), Amogh Pradeep on [Orbot+Orfox](https://lists.torproject.org/pipermail/tor-dev/2014-August/007379.html), Daniel Martí on [consensus diffs](https://lists.torproject.org/pipermail/tor-dev/2014-August/007386.html), Mikhail Belous on the [multicore tor daemon work](https://lists.torproject.org/pipermail/tor-dev/2014-August/007389.html), Zack Mullaly on the [secure ruleset updater for HTTPS Everywhere](https://lists.eff.org/pipermail/https-everywhere/2014-August/002234.html), and Quinn Jarrell on [Fog, the pluggable transport combiner](https://lists.torproject.org/pipermail/tor-dev/2014-August/007393.html).

# Tor help desk roundup

The help desk has been asked if it is possible to set up an anonymous blog using Tor. The [Hyde project](https://github.com/kloesing/hyde/blob/master/publisher-manual/index.md), developed by Karsten Loesing, documents the step-by-step process of using Tor, Jekyll, and Nginx to host an anonymous blog as a hidden service.

# News from Tor StackExchange

The Tor StackExchange site is looking for another [friendly and helpful moderator](https://meta.tor.stackexchange.com/q/207/88). Moderators need to take care of flagged items (spam, me-too comments, etc.), and are liaisons between the community and StackExchange’s community team. So, if you’re interested, have a look at the [theory of moderation](http://blog.stackoverflow.com/2009/05/a-theory-of-moderation/) and post an answer to the question at the Tor StackExchange Meta site.

* * *
This issue of Tor Weekly News has been assembled by Lunar, harmony, David Fifield, qbi, Matt Pagan, Sebastian Hahn, Ximin Luo, and dope457.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

