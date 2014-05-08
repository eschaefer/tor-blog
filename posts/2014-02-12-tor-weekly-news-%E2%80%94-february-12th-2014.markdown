---
layout: post
title: "Tor Weekly News — February 12th, 2014"
permalink: tor-weekly-news-%E2%80%94-february-12th-2014
date: 02/12/2014
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the sixth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tails 0.22.1 is out

The Tails team cut its 36th release on February 4th. Their Debian-based live operating system continues to provide anonymity by ensuring that all outgoing connections are routed through Tor, and privacy by ensuring that no traces are left without the user’s knowledge.

[Tails 0.22.1](https://tails.boum.org/news/version_0.22.1/) contains [security fixes](https://tails.boum.org/security/Numerous_security_holes_in_0.22/) to Firefox, NSS, and Pidgin. It also brings an updated Linux kernel and several fixes for regressions and small issues.

While advertised as a minor version, the new incremental upgrades are a major usability improvement. Previously, upgrading Tails basically meant installing Tails again by downloading the image and putting it on a DVD or a USB stick. Users who store persistent data in their Tails instance then had to use this new medium to upgrade the stick with their data. A tedious process, to say the least. Now, with incremental upgrades, Tails users with USB sticks will be prompted to perform a few clicks, wait, and reboot to get their system up-to-date.

One usability change might surprise long time Tails users: the browser now has to be manually opened when Tor has successfully reached the network.

As always, be sure to [upgrade](https://tails.boum.org/doc/first_steps/upgrade/)! Users of Tails 0.22 on USB sticks can do so easily by running the _Tails Upgrader_ application in the _Tails_ menu.

# Tor Browser Bundle 3.5.2 is released

The Tor Browser team delivers a [new Tor Browser Bundle](https://blog.torproject.org/blog/tor-browser-352-released). Version 3.5.2 brings Tor users [important security fixes from Firefox](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.3) and contains fixes to the “new identity” feature, window size rounding, and the welcome screen with right-to-left language, among others.

The curious can take a peek at the [changelog](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/a1bab4013e:/Bundle-Data/Docs/ChangeLog.txt) for more details. Every Tor user is encouraged to upgrade as soon possible. Jump to the [download page](https://www.torproject.org/download/download-easy.html)!

# Call to bridge operators to deploy ScrambleSuit

In the beginning there was Tor. When censors started filtering every known relay address, [bridges](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/125-bridges.txt) were invented as a way to access the Tor network through unlisted relays. Deep packet inspection systems then started to filter Tor based on its traffic signature, so [pluggable transports](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/pt-spec.txt) and obfucation protocols were designed in order to prevent bridge detection.

Currently, obfuscation is achieved through “obfs2” and “obfs3”. obfs2 is flawed; it’s detectable by deep packet inspection and is being phased out. obfs3 is unfortunately still vulnerable to active probing attacks. As obfs3 bridges are open to anyone, an attacker who uses a traffic classifier and finds an unclassified connection can figure out if it’s Tor simply by trying to connect through the same destination.

[ScrambleSuit](http://www.cs.kau.se/philwint/scramblesuit/) comes to the rescue. On top of making the traffic harder to recognize by timing or volume characteristics, ScrambleSuit requires a shared secret between the bridge and the client. A censor looking at the connection won’t have this secret, and therefore be unable to connect to the bridge and confirm that it’s Tor.

obfsproxy 0.2.6 was [released last week](https://gitweb.torproject.org/pluggable-transports/obfsproxy.git/commit/a3b43d475c4172) and adds ScrambleSuit to the set of available pluggable transports. Bridge operators are now [called](https://lists.torproject.org/pipermail/tor-relays/2014-February/003886.html) to update their software and configuration. At least Tor 0.2.5.1-alpha is required. The latest version of obfsproxy can be installed from [source](https://gitweb.torproject.org/pluggable-transports/obfsproxy.git), [pip](https://pypi.python.org/pypi/obfsproxy) and [Debian unstable](https://lists.torproject.org/pipermail/tor-relays/2014-February/003894.html).

There must be a critical mass of bridges before ScrambleSuit is made available to the Tor users who need it, so please help!

# More status reports for January 2014

The wave of regular monthly reports from Tor project members for the month of January continued. [Kevin P Dyer](https://lists.torproject.org/pipermail/tor-reports/2014-February/000446.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-February/000447.html), [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2014-February/000448.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2014-February/000449.html), [Jacob Appelbaum](https://lists.torproject.org/pipermail/tor-reports/2014-February/000450.html), [Arturo Filastò](https://lists.torproject.org/pipermail/tor-reports/2014-February/000451.html), [Isis Lovecruft](https://lists.torproject.org/pipermail/tor-reports/2014-February/000452.html) and [Nicolas Vigier](https://lists.torproject.org/pipermail/tor-reports/2014-February/000453.html) all released their reports this week.

Roger Dingledine has also sent the [report](https://lists.torproject.org/pipermail/tor-reports/2014-February/000454.html) to SponsorF.

# Miscellaneous news

Most Tor developers will gather next week in Reykjavík, Iceland for the [2014 winter meeting](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014WinterDevMeeting). Expect a drop in activity on the usual communication channels while everyone is busy with face-to-face conversations. See [upcoming events](https://blog.torproject.org/events/tors-winter-2014-developers-meeting-reykjavik-iceland) for activities open to the larger Tor community.

David Fifield is [looking for testers](https://lists.torproject.org/pipermail/tor-qa/2014-February/000324.html) for experimental 3.5.2 browser bundles with tor-fw-helper. “tor-fw-helper is a tool that uses UPnP or NAT-PMP to forward a port automatically” — something that [flashproxy](https://crypto.stanford.edu/flashproxy/) requires. David is “interested in finding out how likely it is to work”.

David Goulet gave us an [update on the development of Torsocks 2.x](https://lists.torproject.org/pipermail/tor-dev/2014-February/006172.html). He hopes to perform a “full on release” after the Tor developers meeting.

”The Trying Trusted Tor Traceroutes project is coming closer to the next data review (03/2014)” [wrote](https://lists.torproject.org/pipermail/tor-relays/2014-February/003865.html) Sebastian Urbach. If you are a relay operator, please help find out how Tor performs against network-level attackers. The team now has a [scoreboard](http://datarepo.cs.illinois.edu/relay_scoreboard.html) with feedback for the participants.

One relay started to act funny regarding its advertised bandwidth. Roger Dingledine quickly [reported his worries](https://lists.torproject.org/pipermail/tor-talk/2014-February/032094.html) to the tor-talk mailing list. A couple of hours later Hyoung-Kee Choi [accounted](https://lists.torproject.org/pipermail/tor-talk/2014-February/032096.html) that one of the students from his research group had made a mistake while experimenting on the Tor bandwidth scanner. Directory authorities are now restricting its usage in the consensus.

On February 11th, the Tor Project participated on [The Day We Fight Back](https://thedaywefightback.org/), a global day of mobilization against NSA mass surveillance.

# Tor help desk roundup

Tor supporters are often curious about the legal risks involved in running a Tor relay. The Tor Project is not aware of any country where running Tor is a punishable offense. Running a bridge relay or a non-exit relay is the best way to grow the Tor network without being exposed to additional legal scrutiny. The decision to run an exit relay should be made only after carefully reviewing the [best practices](https://blog.torproject.org/running-exit-node). Unlike non-exit and bridge operators, exit relay operators need to be prepared to respond to abuse complaints.

Users continue to express interest in a 64-bit Tor Browser Bundle for Windows. Work to provide this new variant is [on-going](https://bugs.torproject.org/10026).

# News from Tor StackExchange

strugee is running a Fast, Running and Valid relay and wonders [when the relay will get the V2Dir flag](https://tor.stackexchange.com/q/1485/88). weasel answered that relays should “get the V2Dir flag simply by publishing a DirPort”, but that Tor will not always publish a DirPort: the full list can be found in the [source code](https://gitweb.torproject.org/tor.git/blob/tor-0.2.4.20:/src/or/router.c#l1018).

Ivar noted that the site [How’s my SSL](https://www.howsmyssl.com/) thinks that the SSL configuration of the Tor Browser is bad and wondered [how the situation could be improved](https://tor.stackexchange.com/q/1455/88). Jens Kubieziel explained some settings for about:config and pointed to a [more detailed blog post](http://kubieziel.de/blog/archives/1564-Using-SSL-securely-in-your-browser.html). Sam Whited also pointed out some settings for Firefox and noted that Firefox 27 [improved the rating to “probably good”](https://blog.samwhited.com/2014/01/fixing-tls-in-firefox/) which will help the Tor Browser in the future.

fred set up a relay on a Windows machine where µTorrent is used besides Tor. When Tor is enabled many trackers become unreachable, but come back as soon as the relay is disabled. An [explanation to this behaviour](https://tor.stackexchange.com/q/1243/88) has yet to be found, don’t hesitate to chime in.

* * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, Paul Feitzinger, qbi, Roger Dingledine and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to  
get involved!

