---
layout: post
title: "Tor Weekly News — January 29th, 2014"
permalink: blog/tor-weekly-news-%E2%80%94-january-29th-2014
date: 2014-01-29
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the fourth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tor Browser Bundle 3.5.1 is released

An update to the Tor Browser Bundle [has been released](https://blog.torproject.org/blog/tor-browser-351-released) on January 27th. The new release contains Tor 0.2.4.20 which fixes [a bug creating useless extra circuits](https://bugs.torproject.org/10456). It also fixes a denial of service condition in OpenSSL and removes “addons.mozilla.org” from the NoScript whitelist.

Arabic bundles are back after a short hiatus. Support for screen readers is also enabled again and has been [confirmed working](https://lists.torproject.org/pipermail/tor-talk/2014-January/031575.html).

HTTPS Everywhere has been updated to version 3.4.5. It contains a new rule to secure connections to Stack Exchange and its [Tor corner](https://tor.stackexchange.com/).

Look at the blog post for a more detailed changelog. And now, head over to the [download page](https://www.torproject.org/download/download-easy.html) and upgrade!

# New Tor denial of service attacks and defenses

Rob Jansen, Florian Tschorsch, Aaron Johnson, and Björn Scheuermann have been working on a new paper entitled [The Sniper Attack: Anonymously Deanonymizing and Disabling the Tor Network](https://www-users.cs.umn.edu/~jansen/publications/sniper-ndss2014.pdf). As research papers are sometimes hard to fully understand, Rob Jansen has published a new [blog post](https://blog.torproject.org/blog/new-tor-denial-service-attacks-and-defenses) giving an overview of the attacks, the defenses, what has been modified in Tor so far, and what open questions remain.

“We found a new vulnerability in the design of Tor’s flow control algorithm that can be exploited to remotely crash Tor relays. The attack is an extremely low resource attack in which an adversary’s bandwidth may be traded for a target relay’s memory (RAM) at an amplification rate of one to two orders of magnitude” explains Rob.

The authors have been working with Tor developers on integrating defenses before publishing: “Due to our devastating findings, we also
designed three defenses that mitigate our attacks, one of which provably renders the attack ineffective. Defenses have been implemented and deployed into the Tor software to ensure that the Tor network is no longer vulnerable as of Tor version 0.2.4.18-rc and later.”

Be sure to read the blog post and the paper in full if you want to know more.

# Good times at Real World Crypto 2014

On the second week of January, a bunch of Tor developers attended the [Real World Crypto workshop](https://realworldcrypto.wordpress.com/) in New York City.

The workshop featured a nice blend of industry and academic crypto talks and a fruitful hallway track. Many researchers involved with Tor and privacy technologies were also present.

As far as talks were concerned, Tom Shrimpton presented the [Format-Transforming Encryption (FTE) traffic obfuscation tool](https://fteproxy.org/) which is currently being developed to [work as a Tor pluggable transport](https://bugs.torproject.org/10362). The Tor developers present also worked with Kevin Dyer, one of the paper authors and developers of FTE, towards including FTE in the Pluggable Transport Tor bundles.

On the censorship circumvention front, I2P developers showed interest in using pluggable transports. Work has been done to identify various problems with the current PT spec that need to be fixed so that other projects can [use pluggable transports more smoothly](https://bugs.torproject.org/10629).

Furthermore, there were talks with the developers of [UProxy](https://uproxy.org/) (a censorship circumvention tool made by Google) and helped them understand how pluggable transports work and what they would need to do if they wanted to use them in UProxy. They seemed interested and motivated to work on this.

The Tor developers also worked on the [Next Generation Hidden Services](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/224-rend-spec-ng.txt) project, and sketched out some ways to move forward even though there are some [open research questions](https://lists.torproject.org/pipermail/tor-dev/2014-January/006099.html) with the current design.

Nick Mathewson commented on IRC: “I think the hallway track to main conference utility ratio was higher than usual, since the conference actually sticks practitioners and cryptographers in the same room pretty reliably.” Let’s hope for next year!

# The media and some terminology

BusinessWeek published [The inside story of Tor, the best Internet anonymity tool the government ever built](http://www.businessweek.com/articles/2014-01-23/tor-anonymity-software-vs-dot-the-national-security-agency). Better that what one can usually read about Tor in the press, the piece — courtesy of Dune Lawrence — still sparkled a discussion on the tor-talk mailing list [about terminology](https://lists.torproject.org/pipermail/tor-talk/2014-January/031863.html).

Katya Titov quoted a misleading part of the article: “In addition to facilitating anonymous communication online, Tor is an access point to the ‘dark Web’, vast reaches of the Internet that are intentionally kept hidden and don’t show up in Google or other search engines, […].”

As references to the “dark web”, the “deep web”, or the “dark deep shady Knockturn Alley of the Internet” have been popping up more and more in the media over the past months, Katya wanted to come up with proper definitions of commonly misunderstood terms to reduce misinformation and [FUD](http://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt).

She summarized the result of the discussion in a new [HowBigIsTheDarkWeb](https://trac.torproject.org/projects/tor/wiki/doc/HowBigIsTheDarkWeb) wiki page. Be sure to point it to your fellow journalists!

# Miscellaneous news

To follow up on last week’s Tor Weekly News coverage, Philipp Winter wrote a blog post to explain [what the “Spoiled Onions” paper means for Tor users](https://blog.torproject.org/blog/what-spoiled-onions-paper-means-tor-users).

Thanks to Sukhbir Singh, users with @outlook.com email addresses can now [request bridges and bundles via email](https://bugs.torproject.org/6591#comment:4).

Karsten Loesing [dug some statistics](https://bugs.torproject.org/10699#comment:3) about the Tor Weather service. There are currently 1846 different email addresses subscribed for 2349 Tor relays.

Tor developers will be [present](https://twitter.com/torproject/status/427922491948818432) at the Mozilla booth during FOSDEM’14 . Drop by if you have questions or want to get involved in Tor!

# Tor help desk roundup

Users repeatedly contact Tor help desk about unreachable hidden services. If that happens, please first make sure the system clock is accurate and try to visit the [hidden service for the Tor Project’s website](http://idnxcnkne4qt76tg.onion/) (`idnxcnkne4qt76tg.onion`). If it works, it means that Tor is working as it should and there’s nothing more the Tor Project can do. Hidden services are solely under the responsibility of their operators and they are the only one that can do something when a hidden service goes offline.

# News from Tor StackExchange

Alex Ryan has been experiencing [crashes of his relay running on a Raspberry Pi](https://tor.stackexchange.com/q/1302/88) due to circuit creation storms. He found out that the problem disappeared after upgrading to the new 0.2.4 series of Tor. There are currently no official Raspbian packages, so users will have to build the package manually from source.

User cypherpunks wanted to know [how to report security issues to the Tor Project](https://tor.stackexchange.com/q/1339/88). Until [a proper process is decided](https://bugs.torproject.org/9186), the best way at the moment is to contact Nick Mathewson, Andrea Shepard, or Roger Dingledine privately using their GnuPG keys.

[How many hidden services can be served from a single Tor instance?](https://tor.stackexchange.com/q/1337/88) Syrian Watermelon is looking to know if there is a hard limit and how memory usage will go. The question is still open and has attracted some interest from other users.

* * *

This issue of Tor Weekly News has been assembled by Lunar, George Kadianakis, qbi, Karsten Loesing and dope457.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

