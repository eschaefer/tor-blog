---
layout: post
title: "Tor Weekly News — January 15th, 2014"
permalink: tor-weekly-news--january-15th-2014
date: 2014-01-15 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the second issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Orbot 13 is out
===============

[Orbot](https://guardianproject.info/apps/orbot/) — the Guardian Project’s port of Tor on Android platforms — has received a [major update](https://lists.mayfirst.org/pipermail/guardian-dev/2014-January/002973.html). Version 13 includes “all the latest bling across the board” meaning Tor 0.2.4.20 and updated versions of OpenSSL and XTables. Nathan also mentions “some important fixes to the Orbot service, to ensure it remains running in the background, and the active notification keeps working, as well. Finally, we’ve changed the way the native binaries are installed, making it more reliable and clean across devices.”

After the initial release candidates, [13.0.1](https://lists.mayfirst.org/pipermail/guardian-dev/2014-January/003016.html), 13.0.2 and then 13.0.3 were quickly made available to fix various reported issues.

The new release is available from the [Guardian Project’s website](https://guardianproject.info/releases/), F-Droid repository or Google Play.

Who are the Tor Project’s website visitors?
===========================================

Last week’s [call for help regarding the Tor Project’s website](https://blog.torproject.org/blog/tor-website-needs-your-help) has seen a pretty impressive response. Discussions then quickly sparkled on the [newly created mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/www-team).

As one of the first concrete outcomes, Rey Dhuny contributed an initial set of “personas”, later improved by Max Jakob Maass, Silviu Riley with suggestions from others. [Quoting Wikipedia](https://en.wikipedia.org/wiki/Persona_%28user_experience%29): “personas are fictional characters created to represent the different user types within a targeted demographic, attitude and/or behavior set that might use a site, brand or product in a similar way.”

One can have a look at [the wiki page](https://trac.torproject.org/projects/tor/wiki/Website#Personas) to learn more about the seven different users of the Tor website that have been currently identified: The Student, The Journalist, The Researcher, The Donor, The Engineer, The Activist, The Dissident. These personas should probably be further refined, but are already a very useful tool to think about how to structure a new website.

For anyone interested in following the effort, Andrew Lewman has spent time triaging [all website related tickets](https://trac.torproject.org/projects/tor/report/45) and setting up [a new milestone](https://trac.torproject.org/projects/tor/milestone/Tor%20Website%203.0) to keep tabs on tasks and issues.

Let’s save Tor Weather!
=======================

The Tor network would not exist without all its volunteers — currently more than 3,000 all around the world — who run the 5,000+ relays anonymizing our connections.

Tor Weather is one of these small services run by the Tor Project that is meant to make the life of relay operators easier. It can warn them when their relay is down or when a new version of tor is available… and when they can receive the [rewarding t-shirt](https://www.torproject.org/getinvolved/tshirt.html). Unfortunately, Tor Weather has been unmaintained for quite a while, and [issues have accumulated](https://trac.torproject.org/projects/tor/query?component=Tor+Weather&order=status) over time.

Karsten Loesing has sent a [call for help](https://lists.torproject.org/pipermail/tor-dev/2014-January/006039.html) with suggestions on how the code can be simplified and improved. Abhiram Chintangal and Norbert Kurz have already stated their interests. Coordination is done through the [tor-dev mailing list ](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-dev) and a [design wiki page](https://trac.torproject.org/projects/tor/wiki/doc/weather-in-2014). Join them if you are up to some Python hacking or spiffing up the web interface!

More monthly status reports for December 2013
=============================================

The wave of regular monthly reports from Tor project members for the month of December 2013 continued this week as well with the [extended report form the Tails team](https://tails.boum.org/news/report_2013_12/) followed by reports from [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-January/000427.html), [Kevin P Dyer](https://lists.torproject.org/pipermail/tor-reports/2014-January/000428.html), and [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2014-January/000430.html).

Miscellaneous news
==================

The Tails team has put out a [call for testing the first release candidate for Tails 0.22.1](https://tails.boum.org/news/test_0.22.1-rc1/). The new version will bring several bugfixes, an updated kernel, and many improvements to the upgrader application.

Directory authorities are in [the process](https://bugs.torproject.org/10324) of upgrading their directory signing key to RSA 2048. This has been done for [five out of nine authorities](https://people.torproject.org/~linus/sign2048.html). The changes might result in some temporary error messages in logs of Tor relays, [as it did](https://lists.torproject.org/pipermail/tor-relays/2014-January/003592.html) when [gabelmoo](https://atlas.torproject.org/#details/F2044413DAC2E02E3D6BCF4735A19BCA1DE97281) changed its key on January 11th.

Nicolas Vigier has sent [a proposal](https://lists.torproject.org/pipermail/tor-dev/2014-January/006047.html) about replacing the current Gitian-based build system for the Tor Browser Bundle by a system based on [burps](http://burps.boklm.eu/). Nicolas also worked on [a prototype](https://github.com/boklm/burps-tor) to go with his proposal.

Nick Mathewson [mentioned](https://lists.torproject.org/pipermail/tor-dev/2014-January/006038.html) that the [“Sniper Attack” paper](http://www-users.cs.umn.edu/~jansen/papers/sniper-ndss2014.pdf) by Rob Jansen, Florian Tschorsch, Aaron Johnson, and Björn Scheuermann was now available. This paper describes serious Denial of Service attacks through memory exhaustion. The issue is fixed “thanks to advice from the paper’s authors, in Tor 0.2.4.x and later”.

In order to [prevent attacks](https://bugs.torproject.org/8244) on hidden services based on predicting which directory will be used, directory authorities need to periodically produce shared unpredictable random strings. To address the issue, Nicholas Hopper has sent [a threshold signature-based proposal for a shared RNG](https://lists.torproject.org/pipermail/tor-dev/2014-January/006053.html), now up for reviews.

The next session of low-hanging fruits for Tails [will happen](https://tails.boum.org/contribute/meetings/201401/) on February 8th in the \#tails IRC channel OFTC at 10:00 CET.

Thanks to [stalkr.net](https://lists.torproject.org/pipermail/tor-mirrors/2014-January/000439.html), [Maki Hoshisawa](https://lists.torproject.org/pipermail/tor-mirrors/2014-January/000442.html) and [cYbergueRrilLa AnonyMous NeXus](https://lists.torproject.org/pipermail/tor-mirrors/2014-January/000443.html) for running new mirrors of the Tor Project website.

Jaromil [announced](https://lists.torproject.org/pipermail/tor-talk/2014-January/031632.html) the release of [Dowse](http://dyne.org/software/dowse), “a transparent proxy setup supporting Tor”. One feature is that it detects “all URLs whose domain ends in .onion, routing them directly to Tor, effectively making the onion network accessible without any plugin or software installed.” The transport proxy approach has [known issues](https://lists.torproject.org/pipermail/tor-talk/2013-July/028833.html) but can still be of interest to some users. Jaromil is seeking feedback and opinions from the community.

Microsoft’s Geoff McDonald wrote a [blog post](https://blogs.technet.com/b/mmpc/archive/2014/01/09/tackling-the-sefnit-botnet-tor-hazard.aspx) describing how they have helped remove half of the estimated [four millions of Tor clients](https://blog.torproject.org/blog/how-to-handle-millions-new-tor-clients) installed by the Sefnit botnet without the computer owner’s knowledge.

Koumbit has been working on [Torride](https://redmine.koumbit.net/projects/torride), a live distribution to run Tor relays — not unlike [Tor-ramdisk](http://opensource.dyc.edu/tor-ramdisk/) — but based on Debian. Version 1.1.0 has been [released](https://redmine.koumbit.net/news/17) on January 10th.

Tor help desk roundup
=====================

Many users have been emailing for clarification on the Tor Browser’s interface. The first time Tor Browser is started, users are asked if their network is free of obstacles. Many users do not know if their network is free of obstacles or not. A network is free of obstacles if it does not censor connections to the Tor network. Ticket [\#10610](https://bugs.torproject.org/10610) has been opened to discuss possible improvements.

A number of users have reported problems using the Tor Browser in Backtrack Linux. Backtrack is unusual among Linux distributions in that the user can only log in as root; there are no other user accounts. The Tor Browser cannot be run as root. One solution for Backtrack users is to create a new account with the `useradd` command and then run the Tor Browser as that user with the `sudo` command.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, dope457, Sandeep, Karsten Loesing, Nicolas Vigier, Philipp Winter and the Tails developers.

Tor Weekly News needs reviewers! 24 hours before being published, the content of the next newsletter is frozen so there is time to improve the language. We are really missing native or good English speakers who could spend just about 20 minutes each week. See the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
