---
layout: post
title: "Tor Weekly News — February 4th, 2014"
permalink: blog/tor-weekly-news-%E2%80%94-february-4th-2014
date: 2014-02-05
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the fifth issue of Tor Weekly News in 2014, the weekly newsletter that covers what is happening in the Tor community.

# News from the browser team front

Mike Perry has a [detailed report](https://lists.torproject.org/pipermail/tor-reports/2014-February/000438.html) about what the growing Tor Browser team has been up to. Among the good news, new fingerprinting defenses are getting close to be merged for “screen resolution, default character sets, site permissions, and local service enumeration”. Some other changes that will reduce the attack surface include “disabling addon update requests for addons that should not update, a potential fix for a disk leak in the browser’s video cache, […], and a potential fix to prevent the Flash plugin from being loaded into the browser at all until the user actually requests to use it.”

Most censored users currently have to use a separate browser bundle dubbed “pluggable transports bundle”. This has proven quite inconvenient for both users and those trying to support them. Mike reports progress on “unifying the pluggable transport bundles with the official bundles, so that both censored and uncensored users can use the same bundles. […] The progress is sufficient that we are very likely to be able to deploy a 3.6-beta1 release in February to test these unified bundles.”

Another important topic is how the privacy fixes in the Tor Browser can benefit a wider userbase. The team has “continued the merge process with Mozilla, and have worked to ensure that every patch of ours is on their radar […]. Two patches, one for an API we require to manage the Tor subprocess, and another to give us a filter to remove potentially dangerous drag-and-drop events to the desktop have already been merged. Next steps will include filing more bugs, continual contact with their development team, and touching up patches as needed.”

There are even more things to smile about in the report. Read it in full for the whole picture.

# Key revocation in next generation hidden services

It looks like every [public-key infrastructure](https://en.wikipedia.org/wiki/Public-key_infrastructure) struggles with how to handle key revocation. Hidden services are no different. The current design completely ignored preventing a stolen key from being reused by an attacker.

With the on-going effort to create a [new protocol for hidden services](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/224-rend-spec-ng.txt), now seems to be a good time for George Kadianakis to [raise this issue](https://lists.torproject.org/pipermail/tor-dev/2014-January/006146.html). In the past there was little control for the hidden services operators over their secret key. The new design enables offline management operations which include key revocation.

As George puts it, currently well-known solutions “are always messy and don’t work really well (look at SSL’s [OCSP](https://en.wikipedia.org/wiki/Online_Certificate_Status_Protocol) and [CRLs](https://en.wikipedia.org/wiki/Certificate_revocation_list)).” So how can “the legitimate Hidden Service can inform a client that its keys got compromised”?

In his email, George describes two solutions, one relying on the directory authorities, the other on hidden service directories. Both have drawbacks, so perhaps further research is necessary.

In the same thread, Nick Hopper [suggested](https://lists.torproject.org/pipermail/tor-dev/2014-January/006149.html) a scheme that uses multiple hidden service directories to cross-certify their revocation lists. This gives more confidence to the user, since the adversary now has to compromise multiple hidden service directories.

Please join the discussion if you have ideas to share!

# Help needed to remove DNS leaks from Mumble

[Mumble](http://mumble.sourceforge.net/) is a “low-latency, high quality voice chat software primarily intended for use while gaming”.

It’s proven to be a reliable solution for voice chat among multiple parties over Tor. Matt and Colin have worked on a documentation on how to [setup both the client and the server side](https://trac.torproject.org/projects/tor/wiki/doc/TorifyHOWTO/Mumble) for Tor users.
But the client is currently safely usable only on Linux system with torsocks and on Tails. On other operating systems, the Mumble client will unfortunately [leak the address of the server to the local DNS resolver](https://github.com/mumble-voip/mumble/issues/1033).

The changes that need to be made to the Mumble code are less trivial than one would think. Matt describe the issue in more details in his [call for help](https://lists.torproject.org/pipermail/tor-dev/2014-January/006158.html). Have a look if you are up to some C++/Qt hacking.

# Monthly status reports for January 2014

The wave of regular monthly reports from Tor project members for the month of January has begun. [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-January/000435.html) released his report first, followed by reports from [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2014-January/000436.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-February/000437.html), the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2014-February/000438.html) from Mike Perry, [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2014-February/000439.html), the [help desk](https://lists.torproject.org/pipermail/tor-reports/2014-February/000440.html), [Matt](https://lists.torproject.org/pipermail/tor-reports/2014-February/000441.html). [Lunar](https://lists.torproject.org/pipermail/tor-reports/2014-February/000442.html), [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-February/000443.html), and [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2014-February/000445.html).

# Miscellaneous news

Nick Mathewson [came up](https://lists.torproject.org/pipermail/tor-dev/2014-January/006157.html) with [a Python script](https://github.com/nmathewson/mmdb-convert) to convert the new MaxMind GeoIP2 binary database to the format used by Tor for its geolocation database.

Thanks to [John Ricketts from Quintex Alliance Consulting](https://lists.torproject.org/pipermail/tor-mirrors/2014-February/000464.html) for providing another mirror for the Tor Project’s website and software.

Abhiram Chintangal and Oliver Baumann are [reporting](https://lists.torproject.org/pipermail/tor-dev/2014-January/006142.html) progress on their [rewrite](https://github.com/baumanno/tor-weather-rewrite) of the Tor Weather service.

Andreas Jonsson gave [an update](https://lists.torproject.org/pipermail/tor-talk/2014-January/031959.html) on how Mozilla is moving to a [multi-process model for Firefox](https://bugzilla.mozilla.org/show_bug.cgi?id=925570) and how this should positively affect the possibility of sandboxing the Tor Browser in the future.

As [planned](https://lists.torproject.org/pipermail/tor-dev/2014-January/006061.html), to help “developers to analyze the directory protocol and for researchers to understand what information is available to clients to make path selection decisions”, Karsten Loesing [has made](https://lists.torproject.org/pipermail/tor-dev/2014-January/006141.html) microdescriptor archives available on the metrics website.

Christian has [deployed](https://lists.torproject.org/pipermail/tor-talk/2014-February/032012.html) a [test platform](https://globe-node.herokuapp.com/) for the JavaScript-less version of Globe, a tool to retrieve information about the Tor network and its relays.

In an answer to Shadowman’s questions about pluggable transports, George Kadianakis wrote a detailed reply on [how Tor manages pluggable transports](https://lists.torproject.org/pipermail/tor-talk/2014-January/031984.html), both on the server side an on the client side.

Arthur D. Edelstein has [advertised a GreaseMonkey script](https://lists.torproject.org/pipermail/tor-talk/2014-February/032010.html) to enable Tor Browser to access YouTube videos without having JavaScript enabled. Please be aware of the [security risks that GreaseMonkey might introduce](https://lists.torproject.org/pipermail/tor-talk/2014-January/031623.html) before using such a solution.

Andrew Lewman reports on his [trip to Washington DC](https://lists.torproject.org/pipermail/tor-reports/2014-January/000434.html) where he met Spitfire Strategies to learn about “Tor’s brand, media presence, and ideas for the future”. For a short excerpt: “It’s interesting to get critiques on all our past media appearances; what was good and what could be better. Overall, the team there are doing a great job.”

Lunar [accounted](https://lists.torproject.org/pipermail/tor-reports/2014-February/000444.html) for Tor’s presence at FOSDEM, one of the largest free software event in Europe. The project had a [small booth](https://twitter.com/anthraxx42/status/429600652399247361) shared with Mozilla and there was even a [relay operator meetup](https://twitter.com/FrennVunDerEnn/status/429636610603233280).

Yan Zhu has [released](https://lists.eff.org/pipermail/https-everywhere/2014-February/001964.html) the first version of HTTPS Everywhere for Firefox Mobile. A good news for users of [the upcoming Orfox](https://github.com/guardianproject/Orfox).

# Tor help desk roundup

Users often want to know if Tor can make them appear to be coming from a particular country. Although doing so can reduce one’s anonymity, it is [documented on our FAQ page](https://www.torproject.org/docs/faq#ChooseEntryExit).

Orbot users have noticed that installing Orbot to their SD storage can cause Orbot to stop functioning correctly. Installing Orbot to the internal storage has resolved issues for a few users.

# News from Tor StackExchange

Rhin is [looking for hidden services hosting services](https://tor.stackexchange.com/q/1402/88). Jens pointed them to ahmia.fi but it looks like no there are no gratis hidden services hosters currently available.

Vijay kudal wanted to know how to [change the current circuit within shell scripts](https://tor.stackexchange.com/q/1438/1041). Jens Kubieziel gave an [answer using expect and hexdump](https://tor.stackexchange.com/a/1453/88).

Roya saw [check.torproject.org replying contradictory information](https://tor.stackexchange.com/q/1439/88) with Atlas about the exit node being used. It seems to be a [bug in check](https://bugs.torproject.org/10499#comment:4) occuring when multiple nodes are using the same IP address.

* * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, qbi, George Kadianakis, Colin, Sandeep, Paul Feitzinger and Karsten Loesing.

TWN is a community newsletter. It can’t rest upon a single pair of shoulders at all times, especially when those shoulders stand behind a booth for two days straight. So if you want to continue reading TWN, we really need your help! Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews) and say “hi” on the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team).

