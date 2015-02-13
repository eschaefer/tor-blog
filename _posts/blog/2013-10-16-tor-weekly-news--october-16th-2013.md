---
layout: post
title: "Tor Weekly News — October 16th, 2013"
permalink: tor-weekly-news--october-16th-2013
date: 2013-10-16 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the sixteenth issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the venerable Tor community.

Making hidden services more scalable and harder to locate
=========================================================

Christopher Baines [started a discussion](https://lists.torproject.org/pipermail/tor-dev/2013-October/005556.html) on tor-dev on the scaling issues affecting the current design of Tor hidden services. Nick Mathewson later described Christopher’s initial proposal as “single hidden service descriptor, multiple service instances per intro point” along with three other alternatives. Nick and Christopher also teamed up to produce a set of seven goals that a new hidden service design should aim for regarding scalability.

There’s probably more to discuss regarding which goals are the most desirable, and which designs are likely to address them, without — as always — harming anonymity.

George Kadianakis also [called for help](https://lists.torproject.org/pipermail/tor-dev/2013-October/005621.html) concerning “the guard enumeration attack that was described by the [Trawling for Tor Hidden Services: Detection, Measurement, Deanonymization](http://www.ieee-security.org/TC/SP2013/papers/4977a080.pdf) paper (in section VII).”

The most popular solution so far seems to be enabling a client or hidden service to reuse some parts of a circuit that cannot be completed successfully in order to connect to new nodes. This should “considerably [slow the attack](https://bugs.torproject.org/9001)”, but “might result in unexpected attacks” as George puts it.

These problems could benefit from everyone’s attention. Free to read the threads in full and offer your insights!

Detecting malicious exit nodes
==============================

Philipp Winter [asked](https://lists.torproject.org/pipermail/tor-dev/2013-October/005593.html) for feedback on the technical architecture of “a Python-based exit relay scanner which should detect malicious and misbehaving exits.”

Aaron took the opportunity to [mention his plans](https://lists.torproject.org/pipermail/tor-dev/2013-October/005596.html) to leverage the work done as part of [OONI](https://ooni.torproject.org/) to detect network interference. Aaron’s intention is to “provide Tor network tests as part of ooni-probe’s standard set of tests, so that many individuals will measure the Tor network and automatically publish their results, and so that current and future network interference tests can be easily adapted to running on the Tor network.”

Detecting misbehaving exits so they can be [flagged “BadExit”](https://trac.torproject.org/projects/tor/wiki/doc/badRelays) by the operators of the directory authorities is important to make every Tor user safer. Getting more users to run tests against our many exit nodes would benefit everyone — it makes it more likely that bad behavior will be caught as soon as possible.

Hiding location at the hardware level
=====================================

One of Tor’s goals is to hide the location of its users, and it does a reasonably good job of this for Internet connections. But when your threat model includes an adversary that can monitor which equipment is connected to a local network, or monitor Wi-Fi network probes received by many access points, extra precautions must be taken.

Ethernet and Wi-Fi cards ship with a factory-determined hardware address (also called a MAC address) that can uniquely identify a computer across networks. Thankfully, most devices allow their hardware address to be changed by an operating system.

As the Tails live operating system aims to protect the privacy and anonymity of its users, it has [long been suggested](https://labs.riseup.net/code/issues/5421) that it should automatically randomize MAC addresses. Some important progress has been made, and this week anonym [requested comments](https://mailman.boum.org/pipermail/tails-dev/2013-October/003835.html) on a detailed analysis of why, when and how Tails should randomize MAC addresses.

In this analysis, anonym describes a Tails user wanting to hide their geographical movement and not be identified as using Tails, but who also wants to “avoid alarming the local administrators (imagine a situation where security guards are sent to investigate an ‘alien computer’ at your workplace, or similar)” and “avoid network connection problems due to MAC address white-listing, hardware or driver issues, or similar”.

The analysis then tries to understand when MAC address should be randomized depending on several combinations of locations and devices. The outcome is that “this feature is enabled by default, with the possibility to opt-out.” anonym then delves into user interface and implementation considerations.

If you are interested in the analysis, or curious about how you could help with the proposed implementation, be sure to have a look!

Tor Help Desk Roundup
=====================

The Tor project wishes to expand its support channels to text-based instant messaging as part of the [Boisterous Otter](https://trac.torproject.org/projects/tor/wiki/org/sponsors/Otter/Boisterous) project. Lunar and Colin C. came up with a [possible implementation](https://trac.torproject.org/projects/tor/wiki/org/sponsors/Otter/Boisterous/WebChat) based on the XMPP protocol, [Prosody](https://prosody.im/) for the server side, and [Prodromus](http://forge.webpresso.net/projects/prodromus) as the basis for the web based interface.

This week, multiple people asked if Tor worked well on the Raspberry Pi. Although the Tor Project does not have any documentation directed specifically at the Raspberry Pi (yet!), the [issue was raised on Tor’s StackExchange page](http://tor.stackexchange.com/questions/242/how-to-run-tor-on-raspbian-on-the-raspberry-pi). Tor relay operators are encouraged to share their experiences or ask for help on the [tor-relays public mailing list](https://lists.torproject.org/pipermail/tor-relays/).

Miscellaneous news
==================

Ten years ago, on October 8th, 2003, Roger Dingledine [announced](https://lists.torproject.org/pipermail/tor-dev/2003-October/002185.html) the first release of tor as free software on the or-dev mailing list.

Damian Johnson [announced](https://blog.torproject.org/blog/stem-release-11) the release of [Stem 1.1.0](https://stem.torproject.org/change_log.html#version-1-1). The new version of this “Python library for interacting with Tor” adds remote descriptor fetching, connection resolution and a myriad of small improvements and fixes.

Arlo Breault sent out a [detailed plan on how Mozilla Instantbird could be turned into the Tor Messenger](https://lists.torproject.org/pipermail/tor-dev/2013-October/005616.html). Feedback would be welcome, especially with regard to sandboxing, auditing, and internationalization for right-to-left languages.

The Spanish and German version of the Tails website are outdated and [may soon be disabled ](https://mailman.boum.org/pipermail/tails-dev/2013-October/003879.html). Now is a good time to [help](https://tails.boum.org/contribute/how/translate/) if you want to keep those translations running!

adrelanos [announced](https://lists.torproject.org/pipermail/tor-talk/2013-October/030593.html) the release of Whonix 7, an operating system “based on Tor […], Debian GNU/Linux and the principle of security by isolation.” The new version includes tor 0.2.4, Tor Browser as the system default browser and a connection wizard, among other changes.

Lunar sent out a [report about the Dutch OHM2013 hacker camp](https://lists.torproject.org/pipermail/tor-reports/2013-October/000363.html) that took place in August.

Philipp Winter, Justin Bull and rndm made several improvements to [Atlas](https://atlas.torproject.org/), the web application for learning more about currently-running Tor relays. The HSDir flag is now properly displayed ([\#9911](https://bugs.torproject.org/9911)), full country names and flags are shown instead of two-letter codes ([\#9914](https://bugs.torproject.org/9914)) and it’s now easier to find out how long a relay has been down ([\#9814](https://bugs.torproject.org/9814)).

ra, one of Tor’s former GSoC students, proposed a [patch](https://bugs.torproject.org/9934) to add a command to the Tor control protocol asking tor to pick a completely new set of guards.

starlight [shared some simple shell snippets](https://lists.torproject.org/pipermail/tor-talk/2013-October/030607.html) that connect to the Tor control port in order to limit the bandwidth used by a relay while running backups.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, harmony, dope457, Damian Johnson and Philipp Winter.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
