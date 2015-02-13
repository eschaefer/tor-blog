---
layout: post
title: "Tor Weekly News — October 29th, 2014"
permalink: tor-weekly-news--october-29th-2014
date: 2014-10-29 07:00:00
author: harmony
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the forty-third issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Tor 0.2.5.10 is out
===================

The 0.2.5.x branch of the core Tor software hit stable, with the release of 0.2.5.10. As Nick Mathewson [explained](https://lists.torproject.org/pipermail/tor-announce/2014-October/000096.html), there have been no changes since last week’s 0.2.5.9-rc release, and the new features will be familiar to readers of Tor Weekly News over the past year of development, but highlights include “improved denial-of-service resistance for relays, new compiler hardening options, and a system-call sandbox for hardened installations on Linux”, as well as improvements to transparent proxying, building and testing, pluggable transport usability, and much more.

This release means that Tor versions in the 0.2.3.x series, which has “received no patches or attention for some while” and “accumulated many known flaws”, [are now deprecated](https://lists.torproject.org/pipermail/tor-relays/2014-October/005590.html). Relay operators running these versions must upgrade as soon as possible, or risk having their relays rejected from the network in the near future.

Please see Nick’s release announcement for the full changelog, and download your copy of the 0.2.5.10 source code from the [distribution directory](https://dist.torproject.org/) or a prebuilt package from your usual repositories.

Miscellaneous news
==================

Jacob Appelbaum [announced](https://lists.torproject.org/pipermail/tor-talk/2014-October/035326.html) version 0.1.3 of TorBirdy, a torifying extension for the Thunderbird email client. Among other things, this release fixes the recently-reported [“wrote:” bug](https://bugs.torproject.org/13480), disables the automatic downloading of messages from POP3 accounts, and ensures that draft messages for IMAP accounts are stored on the local system rather than sent over the network. However, as Jacob wrote, “it’s still experimental”, so “use at your own risk”. See the release announcement for a full changelog.

Anthony G. Basile [announced](http://opensource.dyc.edu/pipermail/tor-ramdisk/2014-October/000134.html) version 20141022 of tor-ramdisk, the micro Linux distribution whose only purpose is to host a Tor server in an environment that maximizes security and privacy. This release addresses the recent [POODLE attack](https://blog.torproject.org/blog/new-sslv3-attack-found-disable-sslv3-torbrowser) with updates to Tor and OpenSSL, and also upgrades the Linux kernel.

Yawning Angel [called for testing](https://lists.torproject.org/pipermail/tor-dev/2014-October/007670.html) of the revamped tor-fw-helper, a tool that automates the port forwarding required (for example) by the [flash proxy](https://crypto.stanford.edu/flashproxy/) pluggable transport. Please see Yawning’s message for full testing instructions and other important information: “Questions, Comments, Feedback appreciated”.

On the Tor blog, Andrew Lewman [responded](https://blog.torproject.org/blog/tor-misused-criminals) to the abuse of Tor by creators of so-called “ransomware”, or malware that tries to restrict access to users’ files unless a ransom is paid; these extortionists sometimes ask their victims to install Tor software in order to communicate with them over a hidden service, leading users to the mistaken belief that The Tor Project is somehow involved. As Andrew wrote, this software “is unrelated to The Tor Project. We didn’t produce it, and we didn’t ask to be included in the criminal infection of any computer.” Users may find the information provided by the [BBC](https://www.bbc.com/news/technology-28661463) and [Bleeping Computer](http://www.bleepingcomputer.com/virus-removal/cryptolocker-ransomware-information) to be helpful in resolving the problem.

Josh Pitts posted an [analysis](http://www.leviathansecurity.com/blog/the-case-of-the-modified-binaries/) of apparently malicious behavior by a Tor relay that was modifying binary files downloaded over Tor circuits in which it was the exit node. As Roger Dingledine [responded](https://lists.torproject.org/pipermail/tor-talk/2014-October/035340.html), “we’ve now set the BadExit flag on this relay, so others won’t accidentally run across it”.

David Fifield [pointed out](https://lists.torproject.org/pipermail/tor-dev/2014-October/007659.html) “an apparent negative correlation between obfs3 users and vanilla users” in the Tor Metrics portal’s [bridge user graphs](https://metrics.torproject.org/users.html?graph=userstats-bridge-transport&transport=%3COR%3E&transport=obfs3#userstats-bridge-transport) and wondered what might be causing it.

News from Tor StackExchange
===========================

Dodo wants to run several hidden services (HTTP, XMPP, SSH etc.), but use [just one onion address](https://tor.stackexchange.com/q/4437/88). Jobiwan explained that one can forward each port to a different service. Further information can be found at the [configuration page for hidden services](https://www.torproject.org/docs/tor-hidden-service.html.en#three).

Rodney Hester proxies the DirPort of his relay and saw lots of requests to nonexistent URLs, of which the most prominent is the URL [/tor/status/all.z](https://tor.stackexchange.com/q/4452/88), and asks where they are coming from. Do you have an answer? If so, please share it at Tor’s StackExchange site.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, qbi, Roger Dingledine, and Harmony.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
