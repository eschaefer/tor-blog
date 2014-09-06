---
layout: post
title: "Tor Weekly News — July 3rd, 2013"
permalink: blog/tor-weekly-news-%E2%80%94-july-3rd-2013
date: 2013-07-03
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the very first issue of Tor Weekly News, the weekly newsletter meant to cover what is happening in the vibrant Tor community.

# Deterministic, independently reproduced builds of Tor Browser Bundle

Mike Perry, Linus Nordberg and Georg Koppen each independently built identical binaries of the [Tor Browser Bundle 3.0 alpha 2 release](https://blog.torproject.org/blog/tor-browser-bundle-30alpha2-released), now [available for download at the Tor Package Archive](https://archive.torproject.org/tor-package-archive/torbrowser/3.0a2/).

The [build system](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/README.build), first adopted for the release of 3.0 alpha 1, uses [Gitian](http://gitian.org/) to enable anyone to produce byte-identical Tor Browser Bundle binary packages from source. This represents a major improvement in the security of the Tor software build and distribution processes against targeted attacks. The motivations and technical details of this work will appear in future Tor Project blog posts.

# Minor progress on datagram-based transport

[As Steven Murdoch explained in 2011](https://blog.torproject.org/blog/moving-tor-datagram-transport), in the current implementation of Tor, “when a packet gets dropped or corrupted on a link between two Tor nodes, […], all circuits passing through this pair of nodes will be stalled, not only the circuit corresponding to the packet which was dropped.” This is because traffic from multiple circuits heading into an OR node are multiplexed by default into a single TCP connection. However, when the reliability and congestion control requirements of TCP streams are enforced (by the operating system) on this multiplexed connection, a situation is created in which one poor quality circuit can disproportionately slow down the others.

This shortcoming could be worked around by migrating Tor from TCP to a datagram-based transport protocol. Nick Mathewson opened [#9165](https://bugs.torproject.org/9165) to track progress on the matter.

Late last year, Steven Murdoch began an [experimental Tor branch using uTP](https://gitweb.torproject.org/sjm217/tor.git/shortlog/refs/heads/utp), a protocol “which provides reliable, ordered delivery while maintaining minimum extra delay”, and is already [used by uTorrent for peer-to-peer connections](http://www.bittorrent.org/beps/bep_0029.html). Nick Mathewson finally got to review his work and wrote several comments on [#9166](https://bugs.torproject.org/9166). The code isn’t close to production-quality right now; it is just good enough for performance testing.

# obfsproxyssh

Yawning Angel sent out [a request for comments](https://lists.torproject.org/pipermail/tor-dev/2013-June/005083.html) on the very first release of [obfsproxyssh](https://github.com/Yawning/obfsproxyssh), a pluggable transport that uses the ssh wire protocol to hide Tor traffic. Its behavior would appear to potential eavesdroppers to be “identical to a user sshing to a host, authenticating with a RSA public/private key pair and opening a direct-tcp channel to the ORPort of the bridge.”

The announcement contains several open issues and questions. Feel free to have a look and voice your comments!

# Crowdfunding for Tor exit relays and bridges

Moritz Bartl announced that he has started a [crowdfunding campaign for Tor exit relays and bridges](http://www.indiegogo.com/projects/tor-anti-censorship-and-anonymity-infrastructure/).

The donations will be distributed equally among all Torservers.net partner organizations (Zwiebelfreunde e.V., DFRI, Nos Oignons, Swiss Privacy Foundation, Frënn vun der Ënn and NoiseTor).

For a faster and better network, chip in and spread the word!

# Tails 0.19 is out, new stable Tor Browser Bundles

On Wednesday, June 26, two of the most popular Tor projects both made new releases: the Tor Browser Bundle, and Tails, The Amnesiac Incognito Live System. Users are encouraged to upgrade as soon as possible.

The [stable Tor Browser Bundle was updated to version 2.3.25-10](https://blog.torproject.org/blog/new-tor-browser-bundles-and-tor-02414-alpha-packages), and includes fixes from upstream Firefox 17.0.7esr. [Tails 0.19](https://tails.boum.org/news/version_0.19/) includes the new stable Tor Browser, along with an updated 3.9.5 kernel and minor security improvements to wireless, GNOME and GnuPG defaults.

# Jenkins + Stem catching their first regression

Quoting [Damian Johnson’s June status report](https://lists.torproject.org/pipermail/tor-reports/2013-June/000262.html): “Our automated
Jenkins test runs caught their first instance of tor regression. This
concerned LOADCONF’s behavior after merging a branch for ticket #6752”.
A [new ticket](https://bugs.torproject.org/9122) was opened after Damian properly identified the issue.

# First round of reports from GSoC projects

[Johannes Fürmann reported](https://lists.torproject.org/pipermail/tor-dev/2013-June/005078.html) on his project, a virtual network environment intended to simulate censorship for OONI (dubbed “Evil Genius”, after Descartes). [Hareesan reported](https://lists.torproject.org/pipermail/tor-dev/2013-June/005082.html) on the steganography browser addon. [Cristian-Matei Toader is working](https://lists.torproject.org/pipermail/tor-dev/2013-June/005085.html) on adding capabilities-based sandboxing to Tor on Linux, using the kernel’s seccomp syscall filtering mechanism. [Chang Lan implemented](https://lists.torproject.org/pipermail/tor-dev/2013-June/005086.html) a HTTP proxy-based transport using CONNECT as the first step in his efforts to implement a general Tor-over-HTTP pluggable transport.

# Monthly status reports for June 2013

The wave of regular monthly reports from Tor project members for the month of June has begun. [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2013-June/000262.html)’s was the first, followed soon after by reports from [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2013-June/000263.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2013-July/000264.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2013-July/000266.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2013-July/000267.html), [Moritz Bartl](https://lists.torproject.org/pipermail/tor-reports/2013-July/000268.html), [Jason Tsai](https://lists.torproject.org/pipermail/tor-reports/2013-July/000269.html), [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2013-July/000270.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2013-July/000271.html), [Kelley Misata](https://lists.torproject.org/pipermail/tor-reports/2013-July/000272.html), [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2013-July/000273.html), and [Andrea Shepard](https://lists.torproject.org/pipermail/tor-reports/2013-July/000276.html).

# Tor on StackExchange

The [proposed StackExchange Q&A page for Tor](http://area51.stackexchange.com/proposals/56447/tor-online-anonymity-privacy-and-security) has left the “initial definition” stage and has entered the “commitment” stage on Area 51. During [this stage](https://lists.torproject.org/pipermail/tor-talk/2013-June/028473.html), interested users are asked to digitally “sign” the proposal with their name to help ensure the site will have an active community during its critical early days.

# Forensic analysis of the Tor Browser Bundle

On Friday, June 28, Runa Sandvik published Tor Tech Report 2013-06-001, titled [Forensic Analysis of the Tor Browser Bundle on OS X, Linux, and Windows](https://research.torproject.org/techreports/tbb-forensic-analysis-2013-06-28.pdf), as part of a deliverable project for two Tor sponsors. The report is a detailed write-up of the forensic experiments Sandvik has been [documenting on her blog](http://encrypted.cc/post/51552592311/forensic-analysis-of-tor-on-os-x), the goal of which was “to identify traces left behind by the Tor Browser Bundle after extracting, using, and deleting the bundle”.

In short, each platform indeed retains forensic traces of the existence of the Tor Browser Bundle. Many “are related to default operating system settings, some of which the bundle might not be able to remove. We therefore [propose the creation of a document](https://bugs.torproject.org/7033) which lists steps our users can take to mitigate these traces on the different operating systems.”

Of course, Tor Browser Bundle users wishing to take immediate action to prevent the creation of forensic traces are not out of luck: “the easiest way to avoid leaving traces on a computer system is to use [The Amnesiac Incognito Live System (Tails)](https://tails.boum.org/).”

# Miscellaneous development news

David Goulet is [making good progress](https://lists.torproject.org/pipermail/tor-dev/2013-June/005069.html) on his [rewrite of torsocks](https://lists.torproject.org/pipermail/tor-dev/2013-June/004959.html) and should have a beta ready in a couple of weeks. He awaits your code reviews, comments and contributions.

Leo Unglaub ran into some trouble with a dependency just as he was about to publish the [work-in-progress code for his Vidalia replacement](https://lists.torproject.org/pipermail/tor-dev/2013-June/005084.html).

Nick Mathewson did some analysis on [possible methods for reducing the volume of fetched directory information](https://bugs.torproject.org/7009), by running some scripts over the last month of consensus directories.

# A vulnerability affecting microdescriptors in Tor?

On Friday, June 28 an anonymous individual [contacted Tor developers](https://twitter.com/ewrwerwtretetet/status/350815079882686464) over Twitter [claiming to have found a vulnerability](http://pastebin.com/pRiMx0CW) in the way microdescriptors are validated by Tor clients which would allow “determination of the source and end-point of a given [victim’s] tor connection with little more than a couple relays and some rogue directory authorities [both controlled by the adversary].”

[Detailed](https://lists.torproject.org/pipermail/tor-talk/2013-June/028699.html) [testing](https://lists.torproject.org/pipermail/tor-talk/2013-June/028700.html) by Nick Mathewson could not reproduce the behavior in the Tor client that was claimed to enable such an attack. After a lengthy Twitter debate with Mathewson, the reporter disappeared, no bugs have been filed, and it appears the vulnerability was nothing of the sort. Without being able to verify the existence of the claimed vulnerability, Mathewson [concluded](https://lists.torproject.org/pipermail/tor-talk/2013-June/028701.html) that the reporter’s described attack was equivalent “at worst… to the ‘request filtering’ attack… which has defenses”.

The issue was also [mentioned](http://seclists.org/fulldisclosure/2013/Jun/245) (and likewise dismissed) on the security mailing list, Full Disclosure.

For anyone interested in reporting vulnerabilities in Tor software, please avoid following that example. Until a process gets [documented](https://bugs.torproject.org/9186), the best way to report the discovery of a vulnerability is to get in touch with one of the Tor core developers using encrypted email.

* * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, moskvax, Mike Perry, Nick Mathewson, mttp, and luttigdev.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteer writers who watch the Tor community and report about what is going on. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews) and write down your name if you want to get involved!

