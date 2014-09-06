---
layout: post
title: "Tor Weekly News — February 26th, 2014"
permalink: blog/tor-weekly-news-%E2%80%94-february-26th-2014
date: 2014-02-26
author: lunar
category: blog
tags: ["tor weekly news"]
---

Velkomin to the eighth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# News from the 2014 Winter Developers’ Meeting in Reykjavík

Since 2010, the Tor Project’s core contributors have tried to meet twice a year to enjoy the pleasure of each other’s company and move projects forward through face-to-face discussions and hacking time. This year, close to forty people attended the [2014 winter dev. meeting](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting), which was held in Reykjavík, Iceland.

The team discussed over forty topics ranging from organizational matters to highly technical design decisions. Among the highlights: many sessions were focused on discussing and producing roadmaps — [a mid-term vision for the Tor Browser](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting/notes/TorBrowserPlan), [a step-by-step plan for the Tor Instant Messaging Bundle](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting/notes/RoadmapTIMB), [detailed ideas for new bridge bundles](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting/notes/BridgeBundles), [ways to solve the research problems around guard nodes](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting/notes/GuardDesign), and [how to plan little-t tor releases](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting/notes/TorReleaseProcess).

The meeting also enabled cross-team communication: pluggable transports developers were able to [discuss integration into the Tor Browser](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting/notes/PTTBB) and the [lifecycle of recommended transports](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting/notes/BridgeProtocolsAndTBB), while the Tor Browser group and the support teams met to see how to [improve communications on both sides](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting/notes/SupportAndTorBrowserTeamsMeeting). One outcome is a plan to [remix existing documentation to create the Tor Browser User Manual](https://bugs.torproject.org/10974).

Two days of intense discussion were followed by hands-on sessions which saw their [fair share of hacking and write-ups](https://trac.torproject.org/projects/tor/timeline?from=Feb+21%2C+2014&daysback=2&authors=&ticket=on&ticket_details=on&changeset=on&wiki=on&update=Update).

Some of the minutes are still missing, but there is already plenty to read. Now that the developers have had to stop contemplating the [Northern Lights](https://en.wikipedia.org/wiki/Aurora_(astronomy)), some [discussions](https://lists.torproject.org/pipermail/tor-dev/2014-February/006288.html) are already continuing on the project’s various mailing lists. Stay tuned!

# Miscellaneous news

Karsten Loesing   [announced](https://lists.torproject.org/pipermail/tor-dev/2014-February/006299.html) an IRC meeting to discuss the next steps for the rewrite of Tor Weather, to be held on the OFTC #tor-dev channel on Wednesday 26th February at 18:00 UTC. “Topics include reporting progress made since the last meeting two weeks ago, making plans for the next week, and possibly turning this project into a GSoC project”.

Nick Mathewson [announced](https://lists.torproject.org/pipermail/tor-dev/2014-February/006282.html) the start of a weekly Tor developer’s meeting, to be held on the OFTC #tor-dev channel, “for working on the program ‘tor’. (This won’t cover all the other programs developed under the Tor umbrella.)” .

The Tails developers [will be holding](https://mailman.boum.org/pipermail/tails-dev/2014-February/004934.html) their next contributors’ meeting on the OFTC #tails-dev channel at 9pm UTC on March 5th; “everyone interested in contributing to Tails is welcome.” .

Andrew Lewman submitted his [monthly status report for January](https://lists.torproject.org/pipermail/tor-reports/2014-February/000462.html), and also wrote up a report of his [involvement in the recent Boston CryptoParty](https://lists.torproject.org/pipermail/tor-reports/2014-February/000463.html).

Alexander Dietrich [published](https://lists.torproject.org/pipermail/tor-relays/2014-February/003942.html) a multi-instance init script for Tor (“basically the current official init script and torservers.net’s “instances” mechanism frankensteined together”, in Alexander’s words) in response to [a recent discussion on tor-relays](https://lists.torproject.org/pipermail/tor-relays/2014-February/003913.html).

Responding to a message from someone interested in writing a DNS-based pluggable transport, George Kadianakis [suggested](https://lists.torproject.org/pipermail/tor-dev/2014-February/006250.html) several ways in which the existing obfsproxy code could be reworked to accommodate this.

George also [recommended](https://lists.torproject.org/pipermail/tor-relays/2014-February/003951.html) that operators of obfs3 or ScrambleSuit bridges install the python-gmpy package on their relays, as it can significantly increase the speed of some cryptographic operations.

Jens Kubieziel [wrote up](https://lists.torproject.org/pipermail/tor-dev/2014-February/006260.html) the results of an attempt to determine whether the recent transition between the TAP and NTor handshake protocols is connected to some users’ reports of hidden service unavailability.

Max Jakob Maass [published](https://lists.torproject.org/pipermail/tor-talk/2014-February/032173.html) the preliminary results of a test in which the RIPE Atlas measurement API was used to retrieve the SSL certificate of torproject.org from as many countries as possible in order to detect attempted attacks or censorship, and wondered whether it might be worth running such a test on a regular basis.

With regard to a coming redesign of the “Volunteers” section on the Tor Project’s website, Moritz Bartl wrote up a list of proposed volunteer categories that was the fruit of a brainstorming session at the Tor developers’ meeting, and [asked for suggestions](https://lists.torproject.org/pipermail/tor-talk/2014-February/032176.html) of “obvious” missing sections, as well as “acceptably-licensed” graphics that could serve as icons for each category .

Nathan Freitas [wrote](https://lists.torproject.org/pipermail/tor-talk/2014-February/032174.html) from the Tor developers’ meeting with a request for help in compiling “ [user stories](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting/notes/UserStories)” on the Tor wiki: that is, stories of the form “a _type of Tor user_ wants to _some feature of a Tor app_ in order to _some reason related to security, privacy, etc_”. If you have any to add, please write them up on the dedicated wiki page!

Yawning Angel [sent out](https://lists.torproject.org/pipermail/tor-dev/2014-February/006300.html) a draft of a proposal to “extend the SOCKS5 protocol when communicating with pluggable transports to allow passing more per-bridge meta-data to the transport and returning more meaningful connection failure response codes back to Tor”.

Josh Ayers [wrote](http://opensource.dyc.edu/pipermail/tor-ramdisk/2014-February/000119.html) to the Tor-ramdisk list suggesting possible ways to ensure that sufficient entropy is available to the kernel by the time tor-ramdisk generates its long-term keys.

# Tor help desk roundup

A common question the help desk receives is how to respond to the Tor Browser Bundle’s download warning message. The message indicates that the Tor Browser Bundle only routes browser traffic through Tor, not traffic from any other application. For example, a PDF file that connects automatically to a URL will not route its traffic through Tor if the file is opened with an external application. An [open bug ticket](https://bugs.torproject.org/7439) for improving this warning message has more information about the issue.

* * *

This issue of Tor Weekly News has been assembled by harmony, Lunar, Matt Pagan, Nicolas Vigier, Roger Dingledine, and George Kadianakis.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

