---
layout: post
title: "Tor Weekly News — November 20th, 2013"
permalink: tor-weekly-news-%E2%80%94-november-20th-2013
date: 11/20/2013
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the twenty-first issue of Tor Weekly News, the [weekly newsletter that covers what is happening in the Tor community.](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news/)

# tor 0.2.4.18-rc is out

On the 16th of November, Roger Dingledine [released the fourth release candidate for the tor 0.2.4.x series](https://lists.torproject.org/pipermail/tor-talk/2013-November/031110.html). As Roger puts it: “It takes a variety of fixes from the 0.2.5.x branch to improve stability, performance, and better handling of edge cases.” Readers curious for more details can look at the announcement for the complete list of changes.

The [source is available](https://www.torproject.org/dist/) as well as [updated Debian packages](https://www.torproject.org/docs/debian.html#development). All relay operators should upgrade. Updated Tor Browser Bundles are in the making and should be available shortly.

# USB Sticks for Tails

It is often recommended to run Tails from a read-only medium in order to prevent any malware to permanently mess with the system. “CD is best, but many devices these days don’t have an optical drive, and handling CDs is not as convenient as a USB stick” [wrote Moritz Bartl on tor-talk](https://lists.torproject.org/pipermail/tor-talk/2013-November/031092.html).

It looks like one of the very few specific brand of USB sticks available in Germany that had a proper hardware protection switch can no longer be used to boot Tails. Moritz ended up contacting various Chinese suppliers. “Even there, the selection of sticks with write protection is very limited” but eventually one model was found acceptable. Moritz intend to re-sell a bulk of them at the [upcoming 30C3 in Hamburg](https://events.ccc.de/congress/2013/).

Feel free to join the discussion or contact Moritz privately for more details.

# New version of check.torproject.org

On the 15th of November, regular users of the Tor Browser Bundle have probably noticed a change in their preferred welcome page. Andrew Lewman had just [switched check.torproject.org to a new version](https://lists.torproject.org/pipermail/tor-talk/2013-November/031126.html) [written by Arlo Breault in Go](https://bugs.torproject.org/9529). The [new codebase](https://gitweb.torproject.org/check.git) should allow the service to better handle the increasingly high number of connections. [Several fixes](https://trac.torproject.org/projects/tor/query?status=closed&changetime=2013-11-15..&component=Tor+Check) were also made during the reimplementation regarding wording, translations and other meaningful details.

Please report any issues you encounter to the “Tor Check” component of the Tor bug tracker.

# Current state of the proposals

In 2007, Tor developers settled on a [formal process](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/001-process.txt) for changes in Tor specifications or other major changes. At this heart of this process in the “proposal” documents that are discussed on the [tor-dev mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-dev) and archived in the [“torspec” Git repository](https://gitweb.torproject.org/torspec.git/tree/HEAD:/proposals).

Last week, Nick Mathewson took a closer look at what have changed since the [last round up](https://lists.torproject.org/pipermail/tor-dev/2012-June/003641.html) he did in June last year. [Since then](https://lists.torproject.org/pipermail/tor-dev/2013-November/005797.html), 16 proposals has been implemented in tor 0.2.3, 0.2.4 and 0.2.5 and two have been superseded or deemed unhelpful.

Nick subsequently [posted](https://lists.torproject.org/pipermail/tor-dev/2013-November/005798.html) a review of all “open”, “needs-revision”, and “needs-research” proposals. They are many different tasks to be picked by someone who wishes to help Tor in these 42 proposals, be it by doing research, code, leading discussions or more in-depth analysis.

# Miscellaneous news

Radu Rădeanu came up with a [workaround](https://bugs.torproject.org/9353#comment:38) for Tor users on Ubuntu 13.10 which temporarily fixes keyboard bug in 64-bit Tor Browser Bundles when used in combination with IBus.

Roger Dingledine [called for help](https://lists.torproject.org/pipermail/tor-talk/2013-November/031134.html) in the [collection](https://bugs.torproject.org/10182) of the new Tor related articles in the press. “According to [the website](https://www.torproject.org/press/press) the last time there was a meaningful article about Tor was July 1st. This is very far from the case.” If you want to help, just [edit the wiki page](https://trac.torproject.org/projects/tor/wiki/TorArticles).

Firefox 24 is soon going to replace version 17 as “stable” supported release by Mozilla. intrigeri has [completed his work](https://mailman.boum.org/pipermail/tails-dev/2013-November/004165.html) in updating Tails’ browser to the point where it “is good enough for Tails 0.22”. Builds from the “feature/ff24” are available for wider testing.

Andreas Jonsson [released](https://lists.torproject.org/pipermail/tor-talk/2013-November/031111.html) initial sandboxed version of the TBB 3.0 series which is [ready for testing](https://github.com/trams242/tor-browser-bundle). This security feature should prevent an exploit from stealing user data : the Tor Browser will not be allowed to execute any programs, nor will it be allowed to read or modify data on disk except in the users “downloads”-folder and its own profile. The sandbox is currently only supported on OS X 10.9 “but making it work all the way down to 10.6 is not unlikely”.

Check Mike Perry’s [latest report](https://lists.torproject.org/pipermail/tor-reports/2013-November/000384.html) to see what he has been up to in October.

# Tor help desk roundup

Users have asked the help desk for support connecting to IRC through Tor. There are some guides on sending IRC traffic through Tor on the wiki ( [1](https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO/InstantMessaging), [2](https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO/IrcSilc)). Tails also comes with [Pidgin preconfigured for IRC](https://tails.boum.org/doc/anonymous_internet/pidgin/). However, it will not matter if the IRC client is correctly configured if the if the intended IRC network blocks all Tor users. For example, users trying to connect to synIRC through Tor will receive a message telling them their computer is part of a botnet.

Users will occasionally ask for support using Tor on ChromeOS. ChromeOS is based on Linux, so it is theoretically possible to run the Linux Tor Browser Bundle on ChromeOS. In practice, the Chromebook prevents users from executing new software on their computers without putting their Chromebook into developer mode, and [making other modifications to their device](http://www.chromium.org/chromium-os/chromiumos-design-docs/security-overview). Anyone who has successfully run the Tor Browser Bundle on ChromeOS is invited to describe their experiences on the Tor Project wiki. As of this writing, there is no documented way of running Tor Browser Bundle on ChromeOS.

* * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, Matt Pagan, and Andreas Jonsson.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

