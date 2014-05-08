---
layout: post
title: "Tor Weekly News — July, 24th 2013"
permalink: tor-weekly-news-%E2%80%94-july-24th-2013
date: 07/24/2013
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the 4<sup>th</sup> issue of Tor Weekly News, the weekly newsletter that covers what is happening in the great Tor community.

The next newsletter is going to be posted to the resurrected [tor-news mailing-list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news). Just subscribe!

# Summer Development Meeting 2013

About 40 core Tor contributors gathered over July 22-23 at the [Technische Universität München](http://www.tum.de/) in Germany for [this year's Summer Development Meeting](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting). That's quite a number, and as could be expected, there are a huge number of topics up for discussion — the brainstorming session generated around 150. Gunner from [Aspiration Tech](http://aspirationtech.org/) is once again facilitating the meeting, helping everyone focus on the most pressing issues.

Rough notes from some of the break-out sessions are now up on the wiki. A list of the topics and a brief summary of the discussions are given below:

- [Love for volunteers](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/LoveForVolunteers): strategies for outreach and long-term support; identifying where they're most needed
- [Censorship and pluggable transports](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/PluggableTransports0): documenting the now-large number of pluggable transports; discussing countries' differing censorship strategies
- [Fundraising](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/Fundraising): funding outlook seems to be positive, although diversity in funding sources is needed to reduce dependency on single institutions like the US Government
- [Website Translation](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/WebsiteTranslation): notes from a discussion which led to the definition of a new translation review process and a list of actionables
- [Service infrastructure](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/ServiceInfrastructure): multiple fundamental services could use some more love: GetTor (TBB by email), website, Trac, check.tp.org, BridgeDB; shutting down unmaintained services
- [Operational security](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/OpSec): random notes on OpSec for Tor people

On the sidelines of the dev meeting, Roger and Jake are doing a public talk on the topic of [Tor and the Censorship Arms Race](https://gnunet.org/tor2013tum).

If you want to meet people who spend their day making Tor a reality, you can [join them for a public hack day](https://blog.torproject.org/blog/join-us-tor-hack-day-munich-germany) on Friday, July 26, 2013. Bring your ideas, questions, projects, and technical expertise with you!

# Remote descriptor fetching in Stem

[Damian Johnson announced](https://lists.torproject.org/pipermail/tor-dev/2013-July/005156.html) having implemented remote descriptor fetching in [Stem](https://stem.torproject.org/), a feature to [migrate more metrics measurement tools to Python](https://lists.torproject.org/pipermail/tor-dev/2013-May/004924.html). “Its usage is pleasantly simple” wrote Damian. See for yourself in the [excellent documentation](https://stem.torproject.org/api/descriptor/remote.html)!

# Orbot 12.0.1 call for beta testing

After a long interval, Nathan Freitas [announced the release of a new version of Orbot](https://lists.torproject.org/pipermail/tor-talk/2013-July/029063.html) — a client for the Tor network on Android mobile devices. For Orbot 12.0.1, the developers have “switched versioning styles to a simpler major.minor.bugfix model”, wrote Nathan.

He continues with a call for testing: “Since we haven't done a release in a while, and we have some new build tools, I mostly want to make sure I have not done something terribly wrong in the build process. Please confirm back if you are able to successfully use this release.”

Updates in 12.0.1:

- Updated to Tor 0.2.4.15-RC
- flashy screen bug fixed now shows traffic
- Stats in notification area
- better handling of preference settings
- Changes added superuser permission for Cyanogen

You can [download and start testing this release](https://guardianproject.info/releases/Orbot-release-12.0.1-beta-1.apk).

# Miscellaneous development news

Lunar reported on the [trip to Brussels for LSM 2013](https://lists.torproject.org/pipermail/tor-reports/2013-July/000292.html). To sum it up, “people are really supportive of what we do these days”.

anonym outlined the [release schedule for Tails 0.20](https://mailman.boum.org/pipermail/tails-dev/2013-July/003292.html).

intrigeri announced that [Tails has switched to a more conventional task manager](https://mailman.boum.org/pipermail/tails-dev/2013-July/003297.html). It might now be easier for you to see what needs to be done. Have a look at the current list of 496 [open issues](https://labs.riseup.net/code/projects/tails/issues), there might be something waiting just for you.

Tor developers would love to find an easier way to debug tor when the daemon crashes. Nick Mathewson came up with an initial piece of code that could (when complete) [dump stack traces](https://bugs.torproject.org/9299) on assertion, crash, or general trouble to the logs. There's more work to be done before it can be merged in Tor. Feel free to help — especially if you know how to do this on Windows or BSD.

Nick Mathewson along with Andrea created a wiki page for [initial 0.2.5 series ticket triage](https://trac.torproject.org/projects/tor/wiki/org/roadmaps/Tor/025/TicketTriage025). If you have your own agenda for 0.2.5, you should be talking to them now!

[Kostas Jakeliunas reported on their GSoC project](https://lists.torproject.org/pipermail/tor-dev/2013-July/005158.html) about producing a searchable metrics archive.

[Arturo reported](https://lists.torproject.org/pipermail/tor-reports/2013-July/000291.html) on his activities on Ooni probe in June.

[Pierre Lalet announced](https://lists.torproject.org/pipermail/tor-dev/2013-July/005161.html) that he started working on an implementation of the Tor protocol in Python. The intent is to have an independent implementation to test Tor. As the author puts it, "the purpose is NOT to implement a secure or robust implementation that could be an alternative to Tor." Have a look at [the code](https://github.com/cea-sec/TorPylle): "Comments, fixes and questions welcome!"

* * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, harmony, moskvax, malaparte, whabib, and David Fifield.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing-list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

