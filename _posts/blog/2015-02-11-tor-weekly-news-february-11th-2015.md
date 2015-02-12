---
layout: post
title: "Tor Weekly News — February 11th, 2015"
permalink: blog/tor-weekly-news-february-11th-2015
date: 2015-02-11
author: harmony
category: blog
tags: ["tor weekly news"]
---

Welcome to the sixth issue in 2015 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) that covers what’s happening in the community around Tor, “[your online an-onionising software](https://theconversation.com/tor-the-last-bastion-of-online-anonymity-but-is-it-still-secure-after-silk-road-35395)”.

The 2015 Tor UX Sprint
======================

Many open-source privacy tools struggle with questions of usability: so much effort goes into ensuring they are secure that few resources are left over to work on the user experience. But as Linda Lee and David Fifield [write](https://blog.torproject.org/blog/ux-sprint-2015-wrapup), “usability is critical to security”: user interface issues “can degrade user experience, cause confusion, or even cause people to accidentally deanonymize themselves”.

To explore, and hopefully solve, some of these problems, a group of Tor developers, designers, users, and researchers [met](https://trac.torproject.org/projects/tor/wiki/org/meetings/2015UXsprint) at UC Berkeley at the start of the month. As part of the weekend, users were asked to walk through the process of installing and running Tor Browser, noting aloud their assumptions and reactions as they went.

Issues and “stopping points” (where users find the process too difficult to continue) discovered during these sessions were noted, and have been assigned tickets on Tor’s [bug tracker](https://trac.torproject.org/projects/tor/query?keywords=~uxsprint2015). For more details of the event and its outcomes, please see Linda and David’s post; “if you are interested in helping to improve the usability of Tor Browser, get in touch by email or IRC”.

Tor and the Library Freedom Project
===================================

As Tor Weekly News reported [last September](https://lists.torproject.org/pipermail/tor-news/2014-September/000063.html), Massachusetts librarian and activist Alison Macrina has been leading a campaign to educate colleagues and library patrons on the state of digital surveillance and the use of privacy-preserving software such as Tor and Tails. As Alison and April Glaser wrote at the time, “[libraries provide access to information and protect patrons’ right to explore new ideas, no matter how controversial or subversive](http://boingboing.net/2014/09/13/radical-librarianship-how-nin.html)”.

These initial workshops formed the basis for the [Library Freedom Project](https://libraryfreedomproject.org/), which has just [received](http://www.knightfoundation.org/grants/201450256/) a grant from the Knight Foundation to expand its activities beyond the New England region. In a guest post on the [Tor blog](https://blog.torproject.org/blog/guest-post-library-freedom-project-bringing-privacy-and-anonymity-libraries), Alison introduced the project, the motivations behind it, and its plans for the next few years, as well as suggesting some possible areas for collaboration with the Tor community in the future: “One specific way that librarians can help the Tor Project is with usability issues – we have lots of experience helping ordinary users with common usability problems […] Librarians can also run dev sprints, help update documentation, and generally advocate for tools that help safeguard privacy and anonymity.”

For more information on the Library Freedom Project, or to propose your own ideas, please see the project’s website. Thanks to Alison and colleagues for this important work!

Vidalia laid to rest
====================

Now that Vidalia, the graphical user interface for Tor, has been completely unmaintained ”for too long to be a recommended solution”, Sebastian Hahn has [removed](https://lists.torproject.org/pipermail/tor-talk/2015-February/036833.html) the last links to Vidalia-related content from the Tor Project website. If you are still using a version of Tor Browser (outside of Tails) that contains Vidalia, it is almost certainly too old to be safe, so please upgrade as soon as possible.

Vidalia is still shipped in the latest version of Tails, however, so the Tails team has been [working](https://mailman.boum.org/pipermail/tails-dev/2015-February/008066.html) on a [simple interface](http://git.tails.boum.org/alan/tor-monitor/) to replace one of the most-missed features of the defunct program, the circuit visualization window. The Tor Browser team have already implemented a similar per-site [circuit diagram](https://bugs.torproject.org/8641) in the current 4.5-alpha series, so there should soon be no reason at all for users to continue controlling their Tor through Vidalia.

More monthly status reports for January 2015
============================================

The wave of regular monthly reports from Tor project members for the month of January continued, with reports from [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2015-February/000754.html), [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2015-February/000755.html), [Michael Schloh von Bennewitz](https://lists.torproject.org/pipermail/tor-reports/2015-February/000756.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2015-February/000757.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2015-February/000758.html), and [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2015-February/000761.html).

Mike Perry reported on behalf of the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2015-February/000759.html), and George Kadianakis sent out the report for [SponsorR](https://lists.torproject.org/pipermail/tor-reports/2015-February/000760.html).

Miscellaneous news
==================

George Kadianakis [linked](https://lists.torproject.org/pipermail/tor-dev/2015-February/008228.html) to the technical report produced by the team working on statistics related to the amount of hidden service usage on the Tor network; Karsten Loesing [added](https://lists.torproject.org/pipermail/tor-dev/2015-February/008249.html) some more information regarding the fraction of network activity this represents. These are advanced calculations, so if you’re not experienced in data science but want to know more about this topic, the team will be back shortly with a more “casual-reader-friendly” analysis of the results.

“Fresh off a round of real-world intensive testing and debugging using spotty 2.5G coverage in the foothills of the Himalayas”, Nathan Freitas of the ever-intrepid Guardian Project [announced](https://lists.mayfirst.org/pipermail/guardian-dev/2015-February/004192.html) the first release candidate for version 14.1 of ChatSecure, the “most private” messaging client for Android and iOS, featuring numerous improvements to usability, stability, and network handling. Please see Nathan’s announcement for the full changelog.

Nathan also [shared](https://lists.mayfirst.org/pipermail/guardian-dev/2015-February/004183.html) a “very early” incarnation of PLUTO, “a simplified means for developers to include traffic obfuscation capabilities into their applications” with initial support for obfs4 and meek. “We think many apps could utilize this approach to defeat DPI filtering, and that this would be useful to offer decoupled from the way Tor integrates it”.

David Fifield posted a [tutorial](https://lists.torproject.org/pipermail/tor-dev/2015-February/008239.html) for configuring the meek pluggable transport to work with hard-to-block HTTPS websites interested in helping censored Tor users, rather than the large content delivery networks it currently uses, along with the regular [summary](https://lists.torproject.org/pipermail/tor-dev/2015-February/008235.html) of the costs incurred by meek’s infrastructure last month: “meek has so far been a smashing success. It’s the \#2 pluggable transport behind obfs3 and it moved over 5 TB of traffic last month. But the costs are starting to get serious.” If you have ideas for supporting this vitally important anti-censorship tool, please see David’s message for more details.

Also in meek news, Across The Great FireWall [published](http://www.atgfw.org/2015/02/torgfwpk1-meektor.html) a Chinese-language introduction to the concepts underpinning this pluggable transport. Other resources (in Chinese and other languages) are listed on the [wiki](https://trac.torproject.org/projects/tor/wiki/doc/meek#Quickstart).

Nick Mathewson took to the [Tor blog](https://blog.torproject.org/blog/tor-design-proposals-how-we-make-changes-our-protocol) to explain exactly what Tor design proposals are for and how they are written, and offered [status updates](https://gitweb.torproject.org/torspec.git/tree/proposals/proposal-status.txt) (and review recommendations) for some new and still-open proposals.

Nick also [asked](https://lists.torproject.org/pipermail/tor-relays/2015-February/006358.html) relay operators to contribute their advice to a [relay hardening guide](https://bugs.torproject.org/13703) that could be shipped with Tor.

Arturo Filastò [asked for help](https://lists.torproject.org/pipermail/ooni-dev/2015-February/000246.html) in coming up with a roadmap for the future of the Open Observatory of Network Interference, asking for opinions on a range of possible development, deployment, and research projects. Feel free to let the ooni-dev list know which of the ideas catches your attention.

After [soliciting feedback](https://lists.torproject.org/pipermail/tor-talk/2015-January/036549.html) on including newer pluggable transports in Tails, the Tails team [decided](https://mailman.boum.org/pipermail/tails-dev/2015-February/008069.html) to focus on obfs4 and then (“tentatively”) meek for upcoming versions of the anonymous live operating system.

Tom “TvdW” van der Woerdt wrote a detailed [report](http://www.tvdw.eu/blog/2015/01/24/implementing-a-tor-relay-from-scratch/) on his experience implementing a Tor client from scratch in the Go programming language, following Tor’s specification document. One instance of “GoTor” briefly broke the Tor relay speed record with 250 megabytes/second, but Tom ultimately decided that Go isn’t the right language for such a thing, as its library support doesn’t make it easy enough to do. Thanks to Tom for running the experiment, and catching some specification errors in the process!

Even though Tor Browser is not vulnerable to the recent WebRTC IP attack proof-of-concept [proof-of-concept](https://github.com/diafygi/webrtc-ips), Mike Perry nevertheless [invited](https://lists.torproject.org/pipermail/tor-talk/2015-February/036845.html) “interested parties to try harder to bypass Tor in a stock Firefox using WebRTC and associated protocols (RTSP, SCTP) with media.peerconnection.enabled set to false”, before a plan to enable WebRTC-based [QRCode bridge address resolution and sharing in Tor Launcher](https://bugs.torproject.org/14837) is implemented.

Shadow, the tool by Rob Jansen that allows full Tor network simulation, now has a new [website](https://shadow.github.io). As Rob [wrote](http://mailman.cs.umn.edu/archives/shadow-dev/2015-February/000081.html): “The new website still uses the Jekyll engine, and is a stripped down customized version of the open source SOLID theme. Please send me feedback if you have it.”

Jillian York of the EFF [discussed](http://jilliancyork.com/2015/02/06/there-are-other-funding-options-than-the-usg/) the problems of over-reliance on US government funding — and the dearth of other funding streams — for anti-surveillance tools, including Tor.

Seven of the eleven activists arrested last year in Spain for, amongst other things, having had email accounts with the technical collective Riseup — longtime Tor allies and [operators of one of the directory authorities](https://lists.torproject.org/pipermail/tor-news/2014-November/000073.html) — have been [released from prison](https://www.accessnow.org/blog/2015/01/20/spain-targets-vulnerable-users-on-eve-of-review-at-un-human-rights-council). As Riseup [wrote](https://help.riseup.net/en/about-us/press/security-not-a-crime) following the arrests, “security is not a crime”: “Giving up your basic right to privacy for fear of being flagged as a terrorist is unacceptable.”

Easy development tasks to get involved with
===========================================

Two problems confronting Mac users who want to download Tor Browser are the “disk image” format and Apple’s Gatekeeper security system. If these users try to run Tor Browser directly from the disk image window that opens after downloading, they will receive an error telling them “Firefox is already running”, and if they correctly move the program to the Applications folder, Gatekeeper will prevent them from running it directly anyway.

If you have access to a machine running the latest version of Mac OS X, and want to spend ten minutes making life easier for Tor users, the Tor Browser [download page](https://www.torproject.org/download/download-easy) would benefit from screenshots showing users how to drag the program to the Applications folder, and how to disable Gatekeeper by control-clicking on the Tor Browser icon when running for the first time. Please see the relevant [bug ticket](https://bugs.torproject.org/14838) for a nice set of example screenshots; your contribution will be gratefully received!

* * * * *

This issue of Tor Weekly News has been assembled by Harmony, Roger Dingledine, Kate Krauss, and David Fifield.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
