---
layout: post
title: "Tor Weekly News — September 3rd, 2014"
permalink: tor-weekly-news--september-3rd-2014
date: 2014-09-03 07:00:00
author: harmony
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the thirty-fifth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Tor Browser 3.6.5 and 4.0-alpha-2 are out
=========================================

The Tor Browser team put out two new releases of the privacy-preserving web browser. Among the major changes, version 3.6.5 upgrades Firefox to 24.8.0esr, and includes an improved prompt to help users defend against [HTML5 canvas image fingerprinting](https://lists.torproject.org/pipermail/tor-talk/2014-July/033969.html), following a [patch](https://bugs.torproject.org/12684) by Isis Lovecruft. Version 4.0-alpha-2 additionally includes the code for the forthcoming Tor Browser auto-updater (switched off by default) and [“better hardening for Windows and Linux builds”](https://lists.torproject.org/pipermail/tor-qa/2014-September/000458.html).

As ever, you can download the new releases along with their signature files from the Tor Project’s [distribution directory](https://www.torproject.org/dist/torbrowser/). Please upgrade as soon as you can.

Tails 1.1.1 is out
==================

The Tails team [released](https://tails.boum.org/news/version_1.1.1/) version 1.1.1 of the Debian- and Tor-based live operating system. As well as upgrading key components like Tor, Iceweasel, and Linux, this release disables I2P by default when Tails is booted, in response to the [vulnerability recently disclosed by Exodus Intelligence](https://tails.boum.org/security/Security_hole_in_I2P_0.9.13/). Like Truecrypt, “i2p” must now be specified as a parameter on booting by users who wish to use it.

A number of other security fixes and routine improvements make this an important update for all Tails users. See the full changelog in the team’s announcement, then update from a running copy of Tails 1.1 if you have one, or head to the [download page](https://tails.boum.org/download/) if you don’t.

Helping Internet services accept anonymous users
================================================

Without a large and diverse network, run by thousands of dedicated volunteers, Tor would be nowhere near as useful or popular as it currently is. Although the current situation might at times seem fragile, there are still many places where it is feasible to host Tor exit nodes.

However, Tor would become much less attractive to users if they found themselves unable to reach or interact with their favorite websites while using it, a situation that is unfortunately growing more common as site administrators and engineers react negatively to instances of abusive Tor traffic by banning anonymous connections outright. Tor users and developers, as well as members of other online communities (such as [Wikimedia](https://meta.wikimedia.org/wiki/Grants:IdeaLab/Partnership_between_Wikimedia_community_and_Tor_community)), have tried to address the issue before, but real progress has yet to be made.

Roger Dingledine wrote a [“call to arms”](https://blog.torproject.org/blog/call-arms-helping-internet-services-accept-anonymous-users) explaining the problem in detail and exploring possible paths to a solution: “Step one is to enumerate the set of websites and other Internet services that handle Tor connections differently from normal connections […]. Step two is to sort the problem websites based on how amenable they would be to our help”.

Since the problem involves humans as much as it does machines, anyone working on it will have to be both “technical” but also ”good at activism”. If you fit that description, OTF has expressed interest in funding work on this issue through their [Information Controls Fellowship Program](https://www.opentechfund.org/labs/fellowships). Please read Roger’s blog post in full for more details.

Monthly status reports for August 2014
======================================

The wave of regular monthly reports from Tor project members for the month of August has begun. [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-August/000626.html) released his report first, followed by reports from [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2014-August/000627.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-September/000628.html), [Noel Torres](https://lists.torproject.org/pipermail/tor-reports/2014-September/000629.html), [Kevin P Dyer](https://lists.torproject.org/pipermail/tor-reports/2014-September/000630.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-September/000633.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2014-September/000635.html), [Arthur D. Edelstein](https://lists.torproject.org/pipermail/tor-reports/2014-September/000636.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2014-September/000637.html), [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2014-September/000638.html), [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2014-September/000639.html), [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2014-September/000640.html), and [Michael Schloh von Bennewitz](https://lists.torproject.org/pipermail/tor-reports/2014-September/000641.html).

Lunar also reported on behalf of the [help desk](https://lists.torproject.org/pipermail/tor-reports/2014-September/000634.html), and Mike Perry did the same for the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2014-September/000642.html).

Miscellaneous news
==================

Yawning Angel [released](https://lists.torproject.org/pipermail/tor-dev/2014-August/007420.html) a new set of experimental Tor Browser builds containing the proposed obfs4 pluggable transport, along with a changelog; “questions, comments, feedback” are welcome on the email thread or the [bug ticket](https://bugs.torproject.org/12130) tracking the deployment of obfs4.

Arturo Filastò [announced](https://lists.torproject.org/pipermail/tor-dev/2014-September/007450.html) the release of version 1.1.0 of oonibackend, the tool “[used by ooniprobe](https://pypi.python.org/pypi/oonibackend) to discover the addresses of test helpers (via the bouncer) to submit reports to (via the collector) and to perform some measurements that require a backend system to talk to (via test helpers)”.

meejah [posted](https://lists.torproject.org/pipermail/tor-dev/2014-August/007426.html) a list of tasks to be completed in order to bring Tor Weather to a deployable state, following the recent rewrite effort and the Google Summer of Code project by Sreenatha Bhatlapenumarthi.

Israel Leiva submitted a [summary](https://lists.torproject.org/pipermail/tor-dev/2014-August/007427.html) of work completed as part of the “Revamp GetTor” Google Summer of Code project: “The plan for now is to keep doing tests and deploy it asap (hopefully during September).”

Mike Perry [posted](https://lists.torproject.org/pipermail/tor-dev/2014-August/007417.html) an [updated version](https://gitweb.torproject.org/user/mikeperry/torspec.git/blob/refs/heads/multihop-padding-primitives:/proposals/ideas/xxx-multihop-padding-primitives.txt) of the proposal for website fingerprinting countermeasures which he co-authored with Marc Juarez as part of the latter’s Google Summer of Code project.

Lunar gave a [talk](http://meetings-archive.debian.net/pub/debian-meetings/2014/debconf14/webm/Reproducible_Builds_for_Debian_a_year_later.webm) at this year’s DebConf on the effort to build Debian packages deterministically, which is inspired in large part by [Tor Browser’s use of the same technology](https://blog.torproject.org/blog/deterministic-builds-part-one-cyberwar-and-global-compromise). [Major progress](http://lists.alioth.debian.org/pipermail/reproducible-builds/Week-of-Mon-20140901/000198.html) was achieved during the conference.

David Fifield submitted a [breakdown](https://lists.torproject.org/pipermail/tor-dev/2014-August/007429.html) of the costs incurred by the infrastructure that supports the [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek) pluggable transport since its introduction. The total to date from both the Google App Engine and Amazon AWS front domains? \$6.56.

Thanks to [P D](https://lists.torproject.org/pipermail/tor-mirrors/2014-August/000653.html) and [Daniel Pajonzeck](https://lists.torproject.org/pipermail/tor-mirrors/2014-August/000673.html) for running mirrors of the Tor Project website and software!

Also on the subject of mirrors, Roger Dingledine [alerted](https://lists.torproject.org/pipermail/tor-mirrors/2014-September/000675.html) the tor-mirrors mailing list to the fact that the Tor Project website (specifically the distribution directory) will shortly be increasing in size to eight or nine gigabytes, as a result of the soon-to-be-implemented [Tor Browser updater](https://bugs.torproject.org/4234). Mirror operators will need to ensure that they can provide enough disk space to accommodate the change.

whonixqubes [announced](https://lists.torproject.org/pipermail/tor-talk/2014-August/034562.html) the release of an integrated version of the Whonix and Qubes operating systems: “I look forward to helping make Qubes + Whonix integration even tighter and more seamless throughout the future.”

Tor help desk roundup
=====================

The help desk has been asked if Tor can make a website visit appear to come from China. Tor connections appear to originate from the country where the exit relay in use is located; since Tor is blocked in China, there are zero exit relays in China. A visualization of the different country-locations of exit relays can be found on Tor’s [metrics page](https://metrics.torproject.org/bubbles.html#country-exits-only).

News from Tor StackExchange
===========================

Anony Mouse wanted to know why Facebook shows the location of the user’s last login over Tor as [Baghdad or Dhaka](https://tor.stackexchange.com/q/3364/88), instead of the real location of the exit relay. qbi posted a [screenshot](https://twitter.com/qbi/status/506550322308055040) showing this issue. According to Facebook, this information is based on an approximation, but this approximation locates all Tor exit relays either in Baghdad or in Dhaka.

user3500 [wants to contribute to Tor](https://tor.stackexchange.com/q/3961/88) and asks how this can be done as an inexperienced developer. Jens Kubieziel replied with several possibilities, including reading the volunteer page and Tor Weekly News: in particular, the section containing easy development tasks might be a good start. Roya pointed out that any contribution is better than no contribution, and encouraged user3500 to just get started. Umut Seven recommended writing unit tests.

Kras wants to use FoxyProxy in connection with Tor Browser Bundle and [asks if it is safe to do so](https://tor.stackexchange.com/q/3239/88). At the moment, there is only an answer saying “yes”, without any explanation. What is your experience? Is it safe for a user to install and use FoxyProxy?

* * * * *

This issue of Tor Weekly News has been assembled by harmony, Matt Pagan, Lunar, qbi, and Arlo Breault.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
