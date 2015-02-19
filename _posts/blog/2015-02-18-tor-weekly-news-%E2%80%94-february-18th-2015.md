---
layout: post
title: "Tor Weekly News — February 18th, 2015"
permalink: blog/tor-weekly-news-—-february-18th-2015
date: 2015-02-18 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the seventh issue in 2015 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Onion services
==============

[Anonymous web services hosted in the Tor network](https://www.torproject.org/docs/hidden-services) have until now been referred to as “hidden services”. Although this name accurately describes one of their properties, it does not convey some of the other benefits that the system provides, like end-to-end encryption without a purchased SSL certificate, or self-authenticating domain names outside of the commercial DNS system. Furthermore, as Aaron Johnson [points out](https://lists.torproject.org/pipermail/tor-dev/2015-February/008256.html), words like “hidden” and “dark” have an unnecessarily negative connotation.

Aaron and other members of the SponsorR team declared themselves in favor of using the word “onion” (as in “[onion routing](https://en.wikipedia.org/wiki/Onion_routing)”) to characterize Tor-protected web services. “Hidden services” could be renamed “onion services”, while websites offered as onion services are “onionsites”; an onion service’s URL is its “onion address”, while the dreaded “Dark Web” becomes simply “onionspace”.

A full list of new and more precise terminology is in Aaron’s message and on the [Tor wiki](https://trac.torproject.org/projects/tor/wiki/org/sponsors/SponsorR/Terminology); please feel free to contribute to the discussion on the tor-dev mailing list with your thoughts.

Miscellaneous news
==================

Nathan Freitas of the Guardian Project [announced](https://lists.mayfirst.org/pipermail/guardian-dev/2015-February/004243.html) the release of version 15-alpha-3 of Orbot. This release includes more work on VPN support, and builds on last week’s early release of the [PLUTO library](https://github.com/guardianproject/pluto) to offer support for [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek), although it is not currently possible to use both at the same time. See Nathan’s announcement for usage instructions and download links.

Yawning Angel [asked for comments](https://lists.torproject.org/pipermail/tor-dev/2015-February/008279.html) on an implementation of a [proposal](https://bugs.torproject.org/6411) to let Tor create “ephemeral” onion services, using key material that is supplied at runtime rather than stored on the disk. See Yawning’s post for a detailed explanation of the concept and a link to the new code; however, trying to run this untested and unreviewed new branch “WILL BROADCAST YOUR SECRETS TO THE NSA’S ORBITAL SPACE STATION”, so don’t do that.

Yawning also [announced](https://lists.torproject.org/pipermail/tor-dev/2015-February/008306.html) version 0.0.4 of obfs4proxy, which “is more useful for the Tor Browser people than anyone else, since it means that the next build can remove the old go.crypto cruft from the build process, and the ScrambleSuit client provider can be switched over to obfs4proxy like obfs2 and obfs3 have been”.

SiNA Rabbani announced that Faravahar, the directory authority which he operates, will be [moving to a new IP address on Friday](https://lists.torproject.org/pipermail/tor-dev/2015-February/008278.html).

Thanks to [cuanto](https://lists.torproject.org/pipermail/tor-mirrors/2015-February/000858.html) for running a mirror of the Tor Project website and software!

Thomas White [published](https://lists.torproject.org/pipermail/tor-talk/2015-February/036886.html) a [guide](https://www.thecthulhu.com/setting-up-a-hidden-service-with-nginx/) to configuring an Nginx webserver as a hidden service: “It isn’t intended to be a hardening guide or an ultra secure way of hosting, but it is for people who want to casually publish some static HTML files or with a little extra configuration to host some applications”.

Collin Anderson and the University of Toronto’s Citizen Lab made a [joint submission](https://citizenlab.org/wp-content/uploads/2015/02/SR-FOE-submission.pdf) to the United Nations Special Rapporteur on the promotion and protection of the right to freedom of opinion and expression, examining the importance of digital security software such as Tor in upholding free expression and the right to privacy.

carlo von lynX [wondered](https://lists.torproject.org/pipermail/tor-talk/2015-February/036911.html) about the truth of the statement that “it would take latencies in the order of hours to fully make communications impossible to shape and correlate”. Roger Dingledine clarified [](https://lists.torproject.org/pipermail/tor-talk/2015-February/036912.html): “It’s actually worse than that — we have no idea. I’d love to have a graph where the x axis is how much additional overhead (latency, bandwidth, whatever) we’re willing to add, and the y axis is how much additional security (anonymity, privacy, whatever) we can get. Currently we have zero data points for this graph.”

* * * * *

This issue of Tor Weekly News has been assembled by Harmony and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
