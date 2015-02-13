---
layout: post
title: "Tor Weekly News — March 19th, 2014"
permalink: tor-weekly-news--march-19th-2014
date: 2014-03-19 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the eleventh issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Accessing the Tor network from China
====================================

In a new blog post [How to read our China usage graphs](https://blog.torproject.org/blog/how-to-read-our-china-usage-graphs), Roger Dingledine looks at the current situation of how Tor is able to circumvent censorship on Chinese Internet accesses. Indeed, if one only looks at the [current bridge users graph](https://metrics.torproject.org/users.html?graph=userstats-bridge-country&start=2011-10-18&end=2014-01-16&country=cn#userstats-bridge-country), one might believe that Tor is not a solution for users in China.

“The correct interpretation of the graph is ‘obfs3 bridges have not been deployed enough to keep up with the demand in China’. So it isn’t that Tor is blocked — it’s that we haven’t done much of a deployment for obfs3 bridges or ScrambleSuit bridges, which are the latest steps in the arms race” writes Roger.

The upcoming version — [currently in QA phase](https://lists.torproject.org/pipermail/tor-qa/2014-March/000364.html) — of the Tor Browser will include support for the [pluggable transports](https://www.torproject.org/docs/pluggable-transports.html) [obfs3](https://gitweb.torproject.org/pluggable-transports/obfsproxy.git/blob/refs/heads/master:/doc/obfs3/obfs3-protocol-spec.txt), [FTE](https://fteproxy.org/) and [Flashproxy](https://crypto.stanford.edu/flashproxy/). Having these transports ready to be used in a couple of clicks should help Chinese users.

The “obfs3” protocol is still vulnerable to active probing attacks. The deployment of its replacement, [ScrambleSuit](http://www.cs.kau.se/philwint/scramblesuit/), is on-going. As Roger highlighted, “we need to get more addresses”. [Several ways have been thoughts in the past](https://blog.torproject.org/blog/strategies-getting-more-bridge-addresses), but until there is more cooperation from ISP and network operators, your can make a difference by [running a bridge](https://lists.torproject.org/pipermail/tor-relays/2014-February/003886.html) if you can!

On another front, work is currently on-going on the [bridge distributor](https://gitweb.torproject.org/bridgedb.git) to improve how censored users can get a hand on bridge addresses. Yawning Angel also [just released](https://lists.torproject.org/pipermail/tor-dev/2014-March/006476.html) the first version of [obfsclient](https://github.com/Yawning/obfsclient) which should help making ScrambleSuit available on Android devices. All in all, the Tor community can hope to welcome back more users from China in a near future.

Circumventing censorship through “too-big-too-block” websites
=============================================================

Late January, David Fifield [introduced](https://lists.torproject.org/pipermail/tor-dev/2014-January/006159.html) a new pluggable transport called [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek). It can be described as “a transport that uses HTTP for carrying bytes and TLS for obfuscation. Traffic is relayed through a third-party server (Google App Engine). It uses a trick to talk to the third party so that it looks like it is talking to an unblocked server.” The approach is close to the [GoAgent](https://trac.torproject.org/projects/tor/wiki/doc/GoAgent) proxy that has a certain popularity in China.

With the current version, using Google App Engine, the transport requires no additional configuration. But David also mentioned that [a PHP script](https://bugs.torproject.org/10984) could also be a good candidate to relay the traffic. Combined to [ScrambleSuit](http://www.cs.kau.se/philwint/scramblesuit/), it could allow “a real web site with real pages and everything” to be used as a bridge if a user can provide the shared secret.

David has made available [experimental versions](https://lists.torproject.org/pipermail/tor-qa/2014-February/000340.html) of the Tor Browser for anyone to try. The [source code](https://gitweb.torproject.org/pluggable-transports/meek.git) has recently [moved](https://lists.torproject.org/pipermail/tor-dev/2014-March/006506.html) to the Tor Project’s infrastructure, and is ready for more eyes and fingers to play with it.

Switching to a single guard node?
=================================

Last October, Roger Dingledine called for research on [improving Tor’s anonymity by changing guard parameters ](https://blog.torproject.org/blog/improving-tors-anonymity-changing-guard-parameters). One of these parameters is the number of guard nodes used simultaneously by a Tor client.

Following up on the [paper written by Tariq Elahi et al.](http://freehaven.net/~arma/cogs-wpes.pdf), Roger’s blog post, and recent discussions during the winter dev. meeting, George Kadianakis made a detailed [analysis of the implications of switching to a single guard node ](https://lists.torproject.org/pipermail/tor-dev/2014-March/006458.html). He studied the performance implications of switching to a single guard, the performance implications of raising the minimum guard bandwidth for both clients and the overall network, and how the change would affect the overall anonymity and fingerprintability of Tor users.

Jumping to conclusions: “It seems that the performance implications of switching to 1 guard are not terrible. […] A guard bandwidth threshold of 2MB/s […] seems like it would considerably improve client performance without screwing terribly with the security or the total performance of the network. The fingerprinting problem will be improved in some cases, but still remains unsolved for many of the users […] A proper solution might involve [guard node buckets](https://bugs.torproject.org/9273#comment:4)”.

For a better understanding, be sure to look at George’s work which includes graphs and proper explanations.

Miscellaneous news
==================

George Kadianakis [announced](https://lists.torproject.org/pipermail/tor-relays/2014-March/004074.html) obfsproxy version 0.2.7. The new release fixes [an important bug](https://bugs.torproject.org/11100) “where scramblesuit would basically reject clients if they try to connect a second time after a short amount of time has passed.” Bridge operators are strongly advised to upgrade from [source](https://gitweb.torproject.org/pluggable-transports/obfsproxy.git/commit/6cdbc64), [pip](https://pypi.python.org/pypi/obfsproxy/0.2.7), or the upcoming Debian packages.

The submission deadline for this year’s [Google Summer of Code](https://blog.torproject.org/blog/tor-google-summer-code-2014) is the 21st: this Friday. Several students already showed up on the tor-dev mailing list, but as Damian Johnson [says](https://lists.torproject.org/pipermail/tor-dev/2014-March/006498.html): “If you’re procrastinating until the last minute then please don’t!”

Tails [logo contest](https://tails.boum.org/news/) is happily on-going. Several submissions have already been received and can be seen on the [relevant blueprint](https://tails.boum.org/blueprint/logo/).

Kelley Misata and Karen Reilly [attended the South by Southwest (SXSW) Interactive festival](https://lists.torproject.org/pipermail/tor-reports/2014-March/000485.html) in Austin, Texas.

Relay and bridge operators might be interested in Ramo’s [first release](https://lists.torproject.org/pipermail/tor-relays/2014-March/004062.html) of [a Tor plugin for Nagios](https://github.com/goodvikings/tor_nagios). It can currently check for a page fetch through the SOCKS proxy port, the hibernation state, the current bandwidth, ORPort reachability, DirPort reachability, and the bytes remaining until hibernation.

Nicolas Vigier sent his [monthly report for February](https://lists.torproject.org/pipermail/tor-reports/2014-March/000486.html).

Tails [won the 2014 Endpoint Security prize](https://twitter.com/accessnow/status/441043400708857856) from Access. The prize [recognizes](https://www.accessnow.org/prize) Tails “unique positive impact on the endpoint security of at-risk users in need”. Congrats!

The Format-Transforming Encryption project at Portland State University [received](http://www.oregonlive.com/silicon-forest/index.ssf/2014/03/psu_professor_wins_surprise_10.html) an unexpected 100,000 USD grant from Eric Schmidt.

Tor help desk roundup
=====================

The help desk has seen an increase in Russian language support requests amidst news that the Russian Federation began censoring a number of websites. Unfortunately, the help desk is not able to provide support in Russian for now. Changes in the number of Tor users by country can be observed on the project’s [metrics page](https://metrics.torproject.org/users.html).

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
