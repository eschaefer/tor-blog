---
layout: post
title: "Tor Weekly News — December 25th, 2013"
permalink: blog/tor-weekly-news-%E2%80%94-december-25th-2013
date: 2013-12-25
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the 26th issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# The 3.x series of the Tor Browser Bundle is now stable

After more than a year of work, Mike Perry has officially [blessed the 3.5 release of the Tor Browser Bundle as the new stable release](https://blog.torproject.org/blog/tor-browser-bundle-35-released). Improving on the previous stable series, it features a [deterministic build system](https://blog.torproject.org/blog/deterministic-builds-part-two-technical-details) for [distributed trust](https://blog.torproject.org/blog/deterministic-builds-part-one-cyberwar-and-global-compromise), a new [integrated interface to interact with Tor](https://gitweb.torproject.org/tor-launcher.git) and all the [improvements from Tor 0.2.4](https://lists.torproject.org/pipermail/tor-talk/2013-December/031392.html).

Users of the previous 2.x series might be a little disoriented by the user interface changes. David Fifield, Matt Pagan and others have been compiling [the most frequent questions](https://trac.torproject.org/projects/tor/wiki/doc/TorBrowserBundle3FAQ) heard after the switch. Until the integrated browser interface catches up, [new Vidalia bundles are now available](https://people.torproject.org/~erinn/vidalia-standalone-bundles/) for those who need them. Erinn Clark is ironing out the remaining integration issues.

With the discontinuation of Firefox 17 ESR, the new release had to be pushed to users to avoid exposing them to security holes. Firefox 24 ESR, on which the Tor Browser is now based, should be supported by Mozilla for approximately one year. This will leave our browser hackers some time to focus more on user experience improvements, test automation, and better resistance to fingerprinting issues.

Several tutorials, videos, and bits of documentation might now in one way or another be out-of-date in many places. Please help report them or, even better, write up some updated versions.

This release is quite a milestone for the project. Update and enjoy!

# The Tor Project now accepts donation in Bitcoin

As is often pointed out in the press, the majority of the Tor Project’s financial support comes from US government-linked organizations. In the ongoing effort to offer as many possible ways for individuals and organizations to give help to the project, [Bitcoin donations are now being accepted](https://blog.torproject.org/blog/announcement-tor-project-now-accepting-bitcoin-donations).

As Roger Dingledine wrote in a subsequent comment: “We really need to get some funding for core Tor development, and especially for improving Tor’s anonymity, because none of our current funders care enough about the anonymity side of Tor. Outreach and blocking-resistance are great topics, but we can’t let the anonymity part rot.”

Head over to the [donations page](https://www.torproject.org/donate/donate#bitcoin) to learn more about how to chip in with Bitcoins or other currencies.

# Tor 0.2.4.20 is out

The first update to the new stable branch of Tor has been [released](https://lists.torproject.org/pipermail/tor-talk/2013-December/031483.html) on December 23rd. It fixes an issue that would create more preemptive circuits than actually need, and a security issue related to poor random number generation.

The latter affects “users who 1) use OpenSSL 1.0.0 or later, 2) set ‘HardwareAccel 1’ in their torrc file, 3) have ‘Sandy Bridge’ or ‘Ivy Bridge’ Intel processors, and 4) have no state file in their DataDirectory (as would happen on first start). Users who generated relay or hidden service identity keys in such a situation should discard them and generate new ones.”

The source code is already available from [the usual location](https://www.torproject.org/dist/). Update packages and bundles should be ready soon.

# Tor events at the 30th Chaos Communication Congress

The Chaos Computer Club will be holding [its 30th Congress](https://www.ccc.de/en/updates/2013/30c3) in Hamburg between the 27th and the 30th of December, and as usual there are a number of Tor-related talks and events scheduled.

Following their [session on the Tor ecosystem at 29c3](https://media.torproject.org/video/29c3-5306-en-the_tor_software_ecosystem_h264.mp4), Tor Project members Roger Dingledine and Jacob Appelbaum will be giving a talk entitled “ [The Tor Network: We’re living in interesting times](https://events.ccc.de/congress/2013/Fahrplan/events/5423.html)”, in which they discuss the Project’s work over the last few years, with special reference to “major cryptographic upgrades in the Tor network, interesting academic papers in attacking the Tor network, major high profile users breaking news about the network itself, discussions about funding, FBI/NSA exploitation of Tor Browser users, botnet related load on the Tor network, and other important topics”.

Their talk will be followed by a [discussion involving everyone interested in helping Tor](https://events.ccc.de/congress/2013/wiki/Session:How_to_help_Tor%3F) at the NoisySquare assembly. The Tor ecosystem is now made up of more than forty different projects, and there are sure to be ways you can help. Bring your skills and your energy!

Torservers.net will be holding a [meeting of Tor relay operators and organizations](https://events.ccc.de/congress/2013/wiki/Session:Tor_Relay_Operators_Meetup), featuring “quick presentations on recent and future activities around Torservers.net”, to be followed by the official members’ meeting of the German Torservers.net partner organization, Zwiebelfreunde e.V.

#youbroketheinternet will hold a session on the [future of crypto routing backends](https://events.ccc.de/congress/2013/wiki/Session:YBTI_Cryptographic_Routing): “Even the IETF is now considering that Onion Routing should be a fundamental capability of the Internet. How would that look in practice?”

If you are attending the Congress, feel free to come along and participate in these sessions; if not, you should be able to catch up with the talks online.

# Miscellaneous news

Anthony G. Basile [released version 20131216](http://opensource.dyc.edu/pipermail/tor-ramdisk/2013-December/000107.html) of Tor-ramdisk, a “uClibc-based micro Linux distribution whose only purpose is to host a Tor server in an environment that maximizes security and privacy.” This new release is the first to ship the 0.2.4 branch of Tor.

For those who like hazardous experiments, intrigeri sent a [call for testing](https://mailman.boum.org/pipermail/tails-dev/2013-December/004538.html) an experimental Tails image with preliminary UEFI support — users of Apple hardware should be particularly interested. anonym also [announced](https://mailman.boum.org/pipermail/tails-dev/2013-December/004547.html) that test images from the MAC spoofing branch were available.

Nick Mathewson sent his now-monthly [review of the status of Tor’s proposals](https://lists.torproject.org/pipermail/tor-dev/2013-December/005957.html). Karsten Loesing followed-up by commenting on several of those related to the directory protocol. Have a look, you might also be able to move things forward!

Many thanks to [John Sweeney of otivpn.com](https://lists.torproject.org/pipermail/tor-mirrors/2013-December/000403.html), [Jeremy J. Olson of EPRCI](https://lists.torproject.org/pipermail/tor-mirrors/2013-December/000411.html), and [les.net](https://lists.torproject.org/pipermail/tor-mirrors/2013-December/000415.html) for running mirrors of the Tor Project website.

Karsten Loesing has been [experimenting](https://bugs.torproject.org/10460) with replacementsfor the “fast exits” graphs that would convey a better feeling of the network growth. He also deployed a new visualization for the [fraction of connections used uni-/bidirectionally](https://metrics.torproject.org/performance.html#connbidirect).

# Tor help desk roundup

Multiple users have now emailed the help desk regarding a particular type of “ [ransomware](https://en.wikipedia.org/wiki/Ransomware_%28malware%29)” that encrypts the hard drive of Windows computers and won’t give users the decryption key until a payment is made. Victims of this malware have emailed the help desk because the ransomware message includes a link to a tor hidden service site. Malware victims wanted to know how to install the Tor Browser, or thought the Tor Project was the source of the malware.

The Tor Project does not make malware; in the past Tor developers have worked with anti-virus developers to help stop other types of malware. Users affected might find useful information in the [guide assembled by BleepingComputer.com](http://www.bleepingcomputer.com/virus-removal/cryptolocker-ransomware-information). If you have not been affected, the story might be a good reminder to think about your backups.

* * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan and dope457.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

