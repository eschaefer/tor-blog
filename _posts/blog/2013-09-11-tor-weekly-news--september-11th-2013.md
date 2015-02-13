---
layout: post
title: "Tor Weekly News — September, 11th 2013"
permalink: tor-weekly-news--september-11th-2013
date: 2013-09-11 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the eleventh issue of Tor Weekly News, the weekly newsletter that covers what is happening in the taut Tor community.

tor 0.2.4.17-rc is out
======================

There are now [confirmations](http://blog.fox-it.com/2013/09/05/large-botnet-cause-of-recent-tor-network-overload/) that the sudden influx of Tor clients which [started mid-August](https://lists.torproject.org/pipermail/tor-talk/2013-September/029822.html) is indeed coming from a botnet. “I guess all that work we’ve been doing on scalability was a good idea,” wrote Roger Dingledine in a blog post about [how to handle millions of new Tor clients](https://blog.torproject.org/blog/how-to-handle-millions-new-tor-clients).

On September 5th, Roger Dingledine [announced the release of the third release candidate for the tor 0.2.4 series](https://lists.torproject.org/pipermail/tor-talk/2013-September/029857.html). This is an emergency release “to help us tolerate the massive influx of users: 0.2.4 clients using the new (faster and safer) ‘NTor’ circuit-level handshakes now effectively [jump the queue](https://bugs.torproject.org/9574) compared to the 0.2.3 clients using ‘TAP’ handshakes”.

It also contains several minor bugfixes and some new status messages for better monitoring of the current situation.

Roger [asked relay operators to upgrade](https://lists.torproject.org/pipermail/tor-relays/2013-September/002701.html) to 0.2.4.17-rc : “the more relays that upgrade to 0.2.4.17-rc, the more stable and fast Tor will be for 0.2.4 users, despite the huge circuit overload that the network is seeing.”

For relays running Debian or Ubuntu, upgrading to the development branch can be done using the [Tor project’s package repository](https://www.torproject.org/docs/debian.html.en#development). [New versions of the beta branch of the Tor Browser Bundle](https://blog.torproject.org/blog/new-tor-02417-rc-packages) are also available since September 6th. The next Tails release, scheduled for [September 19th](https://mailman.boum.org/pipermail/tails-dev/2013-September/003622.html) will [also contain tor 0.2.4.17-rc](https://mailman.boum.org/pipermail/tails-dev/2013-September/003621.html).

Hopefully, this will be the last release candidate. What looks missing at this point to declare the 0.2.4.x series stable is simply enough time to finish the release notes.

The future of Tor cryptography
==============================

After the last round of revelations from Edward Snowden, [described as “explosive” by Bruce Schneier](https://www.schneier.com/blog/archives/2013/09/the_nsa_is_brea.html), several threads started on the tor-talk mailing list to discuss Tor cryptography.

A lot of what has been written is speculative at this point. But some have [raised concerns](https://lists.torproject.org/pipermail/tor-talk/2013-September/029917.html) about 1024 bit [Diffie–Hellman key exchange](https://en.wikipedia.org/wiki/Diffie–Hellman_key_exchange). This has already been addressed with the introduction of the [“ntor” handshake](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/216-ntor-handshake.txt) in 0.2.4 and Nick Mathewson [encourages everybody to upgrade](https://lists.torproject.org/pipermail/tor-talk/2013-September/029930.html).

[Another thread](https://lists.torproject.org/pipermail/tor-talk/2013-September/029927.html) prompted Nick to [summarize](https://lists.torproject.org/pipermail/tor-talk/2013-September/029941.html) his views on the future of Tor cryptography. Regarding public keys, “with Tor 0.2.4, forward secrecy uses 256-bit ECC, which is certainly better, but RSA-1024 is still used in some places for signatures. I want to fix all that in 0.2.5 — see [proposal 220](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/220-ecc-id-keys.txt), and George Kadianakis’ draft hidden service improvements ([descriptors](https://lists.torproject.org/pipermail/tor-dev/2013-August/005279.html), [identity keys](https://lists.torproject.org/pipermail/tor-dev/2013-August/005280.html)), and so forth.” Regarding symmetric keys, Nick wrote: “We’re using AES128. I’m hoping to move to XSalsa20 or something like it.” In response to a query, Nick clarifies that he doesn’t think AES is broken: only hard to implement right, and only provided in TLS in concert with modes that are somewhat (GCM) or fairly (CBC) problematic.

The effort to design better cryptography for the Tor protocols is not new. More than a year ago, Nick Mathewson presented [proposal 202](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/202-improved-relay-crypto.txt) outlining two possible new relay encryption protocols for Tor cells. Nick mentioned that he’s waiting for a promising paper to get finished here before implementation.

A [third question was raised](https://lists.torproject.org/pipermail/tor-talk/2013-September/029933.html) regarding the trust in algorithms certified by the [US NIST](https://en.wikipedia.org/wiki/National_Institute_of_Standards_and_Technology). Nick’s speculations put aside, he also [emphasized](https://lists.torproject.org/pipermail/tor-talk/2013-September/029937.html) that several NIST algorithms were “hard to implement correctly”.

Nick also [plans to change more algorithms](https://lists.torproject.org/pipermail/tor-talk/2013-September/029929.html): “Over the 0.2.5 series, I want to move even more things (including hidden services) to curve25519 and its allies for public key crypto. I also want to add more hard-to-implement-wrong protocols to our mix: Salsa20 is looking like a much better choice to me than AES nowadays, for instance.”

Nick concluded one of his emails with the words: “these are interesting times for crypto”, which sounds like a good way to put it.

Toward a better performance measurement tool
============================================

“I just finished […] sketching out the requirements and a software design for a new Torperf implementation“ [announced](https://lists.torproject.org/pipermail/tor-dev/2013-September/005386.html) Karsten Loesing on the tor-dev mailing list.

The report begins with: “Four years ago, we presented a simple tool to measure performance of the Tor network. This tool, called Torperf, requests static files of three different sizes over the Tor network and logs timestamps of various request substeps. These data turned out to be quite useful to observe user-perceived network [performance over time](https://metrics.torproject.org/performance.html). However, static file downloads are not the typical use case of a user browsing the web using Tor, so absolute numbers are not very meaningful. Also, Torperf consists of a bunch of shell scripts which makes it neither very user-friendly to set up and run, nor extensible to cover new use cases.”

The specification lays out the various requirements for the new tool, and details several experiments like visiting high profile websites with an automated graphical web browser, downloading static files, crafting a canonical web page, measuring hidden service performance, and checking on upload capacity.

Karsten added “neither the requirements nor the software design are set in stone, and the implementation, well, does not exist yet. Plenty of options for giving feedback and helping out, and most parts don’t even require specific experience with hacking on Tor. Just in case somebody’s looking for an introductory Tor project to hack on.”

Sathya already [wrote](https://lists.torproject.org/pipermail/tor-dev/2013-September/005388.html) that this was enough material to get the implementation started. The project needs enough work that anyone interested should get involved. Feel free to join him!

More monthly status reports for August 2013
===========================================

The wave of regular monthly reports from Tor project members continued this week with [Sukhbir Singh](https://lists.torproject.org/pipermail/tor-reports/2013-September/000326.html), [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2013-September/000327.html), [Ximin Luo](https://lists.torproject.org/pipermail/tor-reports/2013-September/000328.html), [mrphs](https://lists.torproject.org/pipermail/tor-reports/2013-September/000329.html), [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2013-September/000330.html), [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2013-September/000331.html), [Mike Perry](https://lists.torproject.org/pipermail/tor-reports/2013-September/000332.html), [Kelley Misata](https://lists.torproject.org/pipermail/tor-reports/2013-September/000333.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2013-September/000334.html), [Jason Tsai](https://lists.torproject.org/pipermail/tor-reports/2013-September/000335.html), [Tails](https://lists.torproject.org/pipermail/tor-reports/2013-September/000336.html), [Aaron](https://lists.torproject.org/pipermail/tor-reports/2013-September/000337.html), and [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2013-September/000338.html).

Miscellaneous news
==================

Not all new Tor users are computer programs! According to their [latest report](https://lists.torproject.org/pipermail/tor-reports/2013-September/000336.html), Tails is now booted twice as much as it was six months ago (from 100,865 to 190,521 connections to the security feed).

Thanks to [Frenn vun der Enn](http://enn.lu/) for setting up a [new mirror](https://lists.torproject.org/pipermail/tor-mirrors/2013-September/000351.html) of the Tor project website.

With the Google Summer of Code ending in two weeks, the students have sent their penultimate reports: Kostas Jakeliunas for the [Searchable metrics archive](https://lists.torproject.org/pipermail/tor-dev/2013-September/005380.html), Johannes Fürmann for [EvilGenius](https://lists.torproject.org/pipermail/tor-dev/2013-September/005394.html), Hareesan for the [Steganography Browser Extension](https://lists.torproject.org/pipermail/tor-dev/2013-September/005409.html), and Cristian-Matei Toader for [Tor capabilities ](https://lists.torproject.org/pipermail/tor-dev/2013-September/005412.html).

Damian Johnson [announced](https://lists.torproject.org/pipermail/tor-reports/2013-September/000338.html) that he had completed the rewrite of [DocTor](https://gitweb.torproject.org/doctor.git) in Python, “a service that pulls hourly consensus information and checks it for a host of issues (directory authority outages, expiring certificates, etc). In the case of a problem it notifies  
 [tor-consensus-health@](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-consensus-health), and we in turn give the authority operator a heads up.”

Matt Pagan has [migrated](https://svn.torproject.org/cgi-bin/viewvc.cgi/Tor?view=revision&revision=26333) several [Frequently-Asked Questions](https://www.torproject.org/docs/faq.html) from the wiki to the official Tor website. This should enable more users to find the answers they need!

In his [previous call for help to collect more statistics](https://lists.torproject.org/pipermail/tor-relays/2013-August/002477.html), addressed to bridge operators, George Kadianakis forgot to mention that an extra line with “ExtORPort 6669” [needed to be added to the tor configuration file](https://lists.torproject.org/pipermail/tor-relays/2013-September/002691.html). Make sure you do have it if you are running a bridge on the tor master branch.

For the upgrade of tor to the 0.2.4.x series in Tails, a tester [spotted a regression](https://mailman.boum.org/pipermail/tails-dev/2013-September/003617.html) while “playing with an ISO built from experimental, thanks to our Jenkins autobuilder”. This marks a significant milestone in the work on [automated builds](https://labs.riseup.net/code/issues/5324) done by several members of the Tails team in the course of the last year!

Tails’ [next “low-hanging fruit” session](https://mailman.boum.org/pipermail/tails-dev/2013-September/003566.html) will be on September 21st at 08:00 UTC. Mark the date if you want to get involved!

David Fifield gave some tips on [how to setup a test infrastructure](https://lists.torproject.org/pipermail/tor-dev/2013-September/005402.html) for [flash proxy](https://crypto.stanford.edu/flashproxy/).

Marek Majkowski [reported](https://lists.torproject.org/pipermail/tor-dev/2013-September/005403.html) on how one can use his [fluxcapacitor](https://github.com/majek/fluxcapacitor.git) tool to get a test Tor network started with [Chutney](https://gitweb.torproject.org/chutney.git) ready in only 6.5 seconds. A vast improvement over the 5 minutes he [initially](https://lists.torproject.org/pipermail/tor-dev/2013-September/005413.html) had to wait!

Eugen Leitl [drew attention](https://lists.torproject.org/pipermail/tor-talk/2013-September/029856.html) to a [new research paper](http://cryptome.org/2013/09/tor-analysis-hidden-services.pdf) which aims to analyze the content and popularity of Hidden Services by Alex Biryukov, Ivan Pustogarov, and Ralf-Philipp Weinmann from the University of Luxembourg.

Tor Help Desk roundup
=====================

The Tor help desk had a number of emails this week asking about the recent stories in the New York Times, the Guardian, and ProPublica regarding NSA’s cryptographic capabilities. Some users asked whether there was a backdoor in Tor. Others asked if Tor’s crypto was broken.

There is absolutely no backdoor in Tor. Tor project members have been [vocal in the past](https://blog.torproject.org/blog/calea-2-and-tor) about how tremendously irresponsible it would be to backdoor our users. As it is a frequently-asked question, users have been encouraged to read [how the project would respond to institutional pressure](http://www.torproject.org/docs/faq.html.en#Backdoor).

The Tor project does not have any more facts about NSA’s cryptanalysis capabilities than what has been published in newspapers. Even if there is no actual evidence that Tor encryption is actually broken, the idea is to remain on the safe side by using more trusted algorithms for the Tor protocols. See above for a more detailed write-up.

Help the Tor community!
=======================

Tor is about protecting everyone’s freedom and privacy. There are [many ways to help](https://www.torproject.org/getinvolved/volunteer.html.en) but getting involved in such a busy community can be daunting. Here’s a selection of tasks on which one could get started:

[Get tor to log the source of control port connections](https://bugs.torproject.org/9698). It would help in developing controller applications or libraries (like Stem [](https://stem.torproject.org/)) to know which program is responsible for a given access to the control facilities of the tor daemon. Knowledge required: C programming, basic understanding of network sockets.

[Diagnose what is currently wrong with Tor Cloud images](https://lists.torproject.org/pipermail/tor-dev/2013-September/005417.html). [Tor Cloud](https://cloud.torproject.org/) is an easy way to deploy bridges and it looks like the automatic upgrade procedure caused problems. Let’s make these virtual machines useful again for censored users. Knowledge required: basic understanding of Ubuntu system administration.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, mttp, malaparte, harmony, Karsten Loesing, and Nick Mathewson.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
