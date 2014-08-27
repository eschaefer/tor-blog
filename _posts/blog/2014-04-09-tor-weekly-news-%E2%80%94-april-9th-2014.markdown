---
layout: post
title: "Tor Weekly News — April 9th, 2014"
permalink: tor-weekly-news-%E2%80%94-april-9th-2014
date: 2014-04-09
author: harmony
category: blog
tags: ["tor weekly news"]
---

Welcome to the fourteenth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

# The Heartbleed Bug and Tor

OpenSSL bug [CVE-2014-0160](https://www.openssl.org/news/vulnerabilities.html#2014-0160), also known as the [Heartbleed bug](http://heartbleed.com/), “allows anyone on the Internet to read the memory of systems protected by the vulnerable versions of the OpenSSL software”, potentially enabling the compromise of information including “user names and passwords, instant messages, emails, and business critical documents and communication”. Tor is one of the very many networking programs that use OpenSSL to communicate over the Internet, so within a few hours of the bug’s disclosure Roger Dingledine posted a [security advisory](https://blog.torproject.org/blog/openssl-bug-cve-2014-0160) describing how it affects different areas of the Tor ecosystem.

[“The short version is: upgrade your openssl”](https://lists.torproject.org/pipermail/tor-talk/2014-April/032602.html). Tor Browser users should upgrade as soon as possible to the new [3.5.4 release](https://blog.torproject.org/blog/tor-browser-354-released), which includes OpenSSL 1.0.1g, fixing the vulnerability. “The browser itself does not use OpenSSL…however, this release is still considered an important security update, because it is theoretically possible to extract sensitive information from the Tor client sub-process”, wrote Mike Perry.

Those using a system Tor should upgrade their OpenSSL version and manually restart their Tor process. For relay operators, “best practice would be to update your OpenSSL package, discard all the files in keys/ in your DataDirectory, and restart your Tor to generate new keys”, and for hidden service administrators, “to move to a new hidden-service address at your convenience”. Clients, relays, and services using an older version of OpenSSL, including Tails, are not affected by this bug.

For mobile devices, Nathan Freitas [called for immediate testing](https://lists.mayfirst.org/pipermail/guardian-dev/2014-April/003383.html) of Orbot 13.0.6-beta-3, which not only upgrades OpenSSL but also contains a fix for the transproxy leak [described by Mike Perry](https://lists.torproject.org/pipermail/tor-talk/2014-March/032503.html) two weeks ago, in addition to smaller fixes and improvements from [13.0.6-beta-1](https://lists.mayfirst.org/pipermail/guardian-dev/2014-April/003375.html) and subsequently. You can obtain a copy of the .apk file directly from the Guardian Project’s [distribution page](https://guardianproject.info/releases/).

Ultimately, “if you need strong anonymity or privacy on the Internet, you might want to stay away from the Internet entirely for the next few days while things settle.” Be sure to read Roger’s post in full for a more detailed explanation if you are unsure what this bug might mean for you.

# A hall of Tor mirrors

Users the world over are increasingly aware of Tor’s leading reputation as a well-researched and -developed censorship circumvention tool — and, regrettably, so are censorship authorities. Events such as last month’s (short-lived) [disruption of access to the main Tor Project website](https://www.eff.org/deeplinks/2014/03/when-tor-block-not-tor-block) from some Turkish internet connections have reaffirmed the need for multiple distribution channels that users can turn to during a censorship event in order to acquire a copy of the Tor Browser, secure their browsing, and beat the censors. One of the simplest ways of ensuring this is to make a copy of the entire website and put it somewhere else.

Recent days have seen the establishment of a large number of new Tor website mirrors, for which thanks must go to [Max Jakob Maass](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000497.html), [Ahmad Zoughbi](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000499.html), [Darren Meyer](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000500.html), [Piratenpartei Bayern](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000501.html), [Bernd Fix](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000505.html), [Florian Walther](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000506.html), the [Electronic Frontier Foundation](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000507.html) (on a subdomain formerly housing the Tor Project’s official site), the [Freedom of the Press Foundation](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000508.html), [Caleb Xu](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000509.html), [George Kargiotakis](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000510.html), and [Tobias Markus](https://lists.torproject.org/pipermail/tor-mirrors/2014-April/000512.html), as well as to all the mirror operators of [longer standing](https://www.torproject.org/getinvolved/mirrors).

If you’d like to participate in the effort to render blocking of the Tor website even more futile, please see the [instructions for running a mirror](https://www.torproject.org/docs/running-a-mirror), and then come to the [tor-mirrors mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-mirrors) to notify the community!

# Mission Impossible: Hardening Android for Security and Privacy

On the Tor Blog, Mike Perry posted [another large and comprehensive hacking guide](https://blog.torproject.org/blog/mission-impossible-hardening-android-security-and-privacy), this time describing “the installation and configuration of a prototype of a secure, full-featured, Android telecommunications device with full Tor support, individual application firewalling, true cell network baseband isolation, and optional ZRTP encrypted voice and video support.” The walkthrough covers hardware selection and setup, recommended software, Google-free backups, and disabling the built-in microphone of a Nexus 7 tablet (with a screwdriver).

As it stands, following this guide may require a certain level of patience, but as Mike wrote, “it is our hope that this work can be replicated and eventually fully automated, given a good UI, and rolled into a single ROM or ROM addon package for ease of use. Ultimately, there is no reason why this system could not become a full fledged off the shelf product, given proper hardware support and good UI for the more technical bits.”

Mike has already added to and improved parts of the guide following contributions from users in the comments beneath the post. If you would like to work (or already are working) at the cutting-edge of research into mobile device security and usability, take a look at Mike’s suggestions for future work at the bottom of the guide, and please share your ideas with the community.

# More monthly status reports for March 2014

The wave of regular monthly reports from Tor project members for the month of March continued, with submissions from [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2014-April/000497.html), [Colin Childs](https://lists.torproject.org/pipermail/tor-reports/2014-April/000499.html), [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-April/000500.html), [Michael Schloh von Bennewitz](https://lists.torproject.org/pipermail/tor-reports/2014-April/000501.html), [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2014-April/000502.html), and [Kevin Dyer](https://lists.torproject.org/pipermail/tor-reports/2014-April/000503.html).

Arturo Filastò reported on behalf of the [OONI team](https://lists.torproject.org/pipermail/tor-reports/2014-April/000496.html), while Mike Perry did likewise for the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2014-April/000498.html).

# Miscellaneous news

David Goulet [announced](https://lists.torproject.org/pipermail/tor-dev/2014-April/006649.html) the seventh release candidate for [Torsocks 2.0.0](https://gitweb.torproject.org/torsocks.git), the updated version of the wrapper for safely using network applications with Tor. “Nothing major, fixes and some code refactoring went in”, said David. Please review, test, and report any issues you find.

Nathan Freitas [posted](https://lists.torproject.org/pipermail/tor-talk/2014-April/032574.html) a brief analysis of the role played by Orbot in the recent Turkish internet service disruption: “it might be good to think about Turkey’s Twitter block as a “censorship-lite” event, not unlike the UK or Indonesia, and then figure out how we can encourage more adoption.”

Jann Horn [drew attention](https://lists.torproject.org/pipermail/tor-relays/2014-March/004199.html) to a potential issue caused by some Tor relays sending out globally-sequential IP IDs. Roger Dingledine [linked](https://lists.torproject.org/pipermail/tor-relays/2014-April/004206.html) to an academic paper connected with the same question, while Daniel Bilik [suggested](https://lists.torproject.org/pipermail/tor-relays/2014-April/004207.html) one method of preventing this from happening on FreeBSD. Exactly how significant this issue is (or is not) for the Tor network is very much an open question; further research into which operating systems it affects, and how it might be related to known attacks against anonymity, would be very welcome.

As part of their current [campaign to fund usable encryption tools](https://pressfreedomfoundation.org/bundle/encryption-tools-journalists#donate) (including Tor) for journalists, the Freedom of the Press Foundation [published](https://pressfreedomfoundation.org/blog/2014/04/help-support-little-known-privacy-tool-has-been-critical-journalists-reporting-nsa) a blog post on the “little-known” Tails operating system, featuring quotes from three of the journalists most prominently associated with the recent Snowden disclosures (Laura Poitras, Glenn Greenwald, and Barton Gellman) attesting to the important role Tails has played in their ability to carry out their work. If you’re impressed by what you read, please donate to the campaign — or [become a Tails contributor!](https://tails.boum.org/contribute/index)

Two Tor-affiliated projects — the Open Observatory of Network Interference and Tails — have each submitted a proposal to this year’s [Knight News Challenge](https://www.newschallenge.org). The [OONI proposal](https://www.newschallenge.org/challenge/2014/submissions/global-internet-monitoring-project) involves further developing the ooni-probe software suite and deploying it in countries around the world, as well as working on analysis and visualization of the data gathered, in collaboration with the [Chokepoint Project](https://chokepointproject.net/); while [Tails’ submission](https://www.newschallenge.org/challenge/2014/submissions/improve-tails-to-limit-the-impact-of-security-flaws-isolate-critical-applications-and-provide-same-day-security-updates) proposes to “improve Tails to limit the impact of security flaws, isolate critical applications, and provide same-day security updates”. Voting is limited to the Knight Foundation’s trustees, but feel free to read each submission and leave your comments for the developers.

Robert [posted](https://lists.torproject.org/pipermail/tor-dev/2014-April/006627.html) a short proposal for “a prototype of a next-generation Tor control interface, aiming to combine the strengths of both the present control protocol and the state-of-the-art libraries”. The idea was originally destined for this year’s GSoC season, but in the end Robert opted instead to “get some feedback and let the idea evolve.”

After the end of the [Tails logo contest](https://tails.boum.org/blueprint/logo/) last week, sajolida [announced](https://mailman.boum.org/pipermail/tails-dev/2014-April/005390.html) that the winner will be declared by April 9th, after a week of voting by the most active Tails contributors.

Following last week’s progress on the Tor website redesign campaign, William Papper [presented](https://lists.torproject.org/pipermail/www-team/2014-April/000301.html) a functioning [beta version](http://wpapper.github.io/tor-download-web/) of the new download page that he and a team of contributors have been building. Have a look, and let the [www-team list](https://lists.torproject.org/cgi-bin/mailman/listinfo/www-team) know what works and what doesn’t!

Michael Schloh von Bennewitz began work on a [guide to configuring a virtual machine for building the Tor Browser Bundle](https://trac.torproject.org/projects/tor/wiki/doc/TorBrowser/VMSetup), and another to [building with Gitian](https://trac.torproject.org/projects/tor/wiki/doc/TorBrowser/BuildingWithGitian).

# Tor help desk roundup

Tor Browser users often try to set a proxy when they don’t need to. Many users think they can circumvent website bans or get additional security by doing this. Discussion on clarifying the tor-launcher interface is taking place on the [bug tracker](https://bugs.torproject.org/11405).

# News from Tor StackExchange

Tor’s StackExchange did its second site self-evaluation . Users were asked to review ten questions and their respective answers. This should help to improve the site's overall quality.

The question [“Why does GnuPG show the signature of Erinn Clark as not trusted?”](https://tor.stackexchange.com/q/1573/88) got the best rating. When a user verified the downloaded copy of Tor Browser Bundle, GnuPG showed Erinn’s signature as not-trusted. Jens Kubieziel explained the trust model of GnuPG in his answer, and gapz referred to the [handbook](http://gnupg.org/gph/en/manual/x334.html).

The following questions need better answers: [“How to validate certificates?”](https://tor.stackexchange.com/q/1584/88); [“Why does Atlas sometimes show a different IP address from https://check.torproject.org?”](https://tor.stackexchange.com/q/1439/88); [“Site login does not persist”](https://tor.stackexchange.com/q/1536/88); and [“My Atlas page is blank”](https://tor.stackexchange.com/q/1587/88).

If you know good answers to these questions, please help the users of Tor StackExchange.

* * *
This issue of Tor Weekly News has been assembled by harmony, Matt Pagan, qbi, Lunar, Roger Dingledine, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

