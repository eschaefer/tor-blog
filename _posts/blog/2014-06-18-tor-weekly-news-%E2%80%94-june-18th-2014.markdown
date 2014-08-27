---
layout: post
title: "Tor Weekly News — June 18th, 2014"
permalink: tor-weekly-news-%E2%80%94-june-18th-2014
date: 2014-06-18
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the fiftieth issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tails 1.0.1 is out

The Tails developers [announced](https://tails.boum.org/news/version_1.0.1/) the first point release in the Tails 1.0 series, following their [decision](https://mailman.boum.org/pipermail/tails-dev/2014-May/005917.html) to postpone the release of Tails 1.1 (which will be based on Wheezy, the latest stable version of Debian).

This release contains no major new features, but does fix [numerous security issues](https://tails.boum.org/security/Numerous_security_holes_in_1.0/index) present in 1.0, so all Tails users should upgrade as soon as possible.

# Collecting statistics from Tor exits in a privacy-sensitive manner

Optimizing the Tor network to better support the most common use-cases could make a real difference to its perceived usability. Unfortunately, Tor is an anonymity network. Understanding what the most common use-cases are, in a way that does not endanger its users, is far from being a trivial problem.

There have been some cases of [inconsiderate spying on Tor network users](http://www.ifca.ai/pub/fc11/wecsr11/soghoian.pdf) in the past. This is one of the motivations for the Tor Project to provide and research properly anonymized statistics through the [Metrics](https://metrics.torproject.org/) and [CollecTor](https://collector.torproject.org/) portals.

Tariq Elahi, George Danezis, and Ian Goldberg are working on new solutions to tackle the problem of collecting statistics from Tor exits in a privacy-sensitive manner. Tariq [announced](https://lists.torproject.org/pipermail/tor-dev/2014-June/006999.html) the PrivEx system which “preserves the security and privacy properties of anonymous communication networks, even in the face of adversaries that can compromise data collection nodes or coerce operators to reveal cryptographic secrets and keys”.

The introduction of the [detailed tech report](http://cacr.uwaterloo.ca/techreports/2014/cacr2014-08.pdf) gives a general description of the solution: “PrivEx collects aggregated statistics to provide insights about user behaviour trends by recording aggregate usage of the anonymity network. To further reduce the risk of inadvertent disclosures, it collects only information about destinations that appear in a list of known censored websites. The aggregate statistics are themselves collected and collated in a privacy-friendly manner using secure multiparty computation primitives, enhanced and tuned to resist a variety of compulsion attacks and compromises. Finally, the granularity of the statistics is reduced […] to foil correlation attacks.”

PrivEx’s threat model is described in section 3, and matches the current mode of operation of the Tor network, relying on a set of mostly honest collectors while being able to cope with a limited number of malicious nodes. Two variants are described: one “is secure in the honest-but-curious setting but can be disrupted by a misbehaving actor” while “the other is secure in the covert adversary setting in that misbehaving servers can be identified”, but is more computationally expensive.

Tariq mentions that implementations of the two variants of PrivEx described in the tech report have been created and should soon be released to the community. The researchers expect to “start by rolling out our own PrivEx-enabled exits in the Tor network and begin collecting destination visit statistics” around the “June-August timeframe”. Section 6 contains an analysis of the overhead in both CPU and bandwidth of the two PrivEx variants, and the requirements seem reasonable.

Given how much privacy matters to the Tor community and to all network users, the researchers wants “a measure of confidence that collecting data with PrivEx is inherently good and is being done in a responsible and intelligent manner”. They are therefore asking the “community at large” to review the design of the proposal, and its implementation once released.

If no fundamental flaws are discovered in the process, the Tor community might finally be able to enjoy better network statistics in the not-too-distant future.

# Upcoming developments in pluggable transports

In a new [blog post](https://blog.torproject.org/blog/recent-and-upcoming-developments-pluggable-transports), George Kadianakis reported on some recent pluggable transports developments. Some — like the [release of Tor Browser 3.6](https://blog.torproject.org/blog/tor-browser-36-released), the [deprecation of obfs2](https://bugs.torproject.org/10314), the new [meek transport](https://trac.torproject.org/projects/tor/wiki/doc/meek), or the recently-written [“Child’s Garden Of Pluggable Transports” guide](https://trac.torproject.org/projects/tor/wiki/doc/AChildsGardenOfPluggableTransports) should already be known to regular readers of Tor Weekly News.

It was previously [impossible to use pluggable transports at the same time as an HTTP or SOCKS proxy](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/232-pluggable-transports-through-proxy.txt). The [release of Tor Browser 3.6.2](https://blog.torproject.org/blog/tor-browser-362-released)is the first to include work by Yawning Angel which solves this deficiency.

However, ScrambleSuit, released last winter, has not yet been included in Tor Browser. The pluggable transport team is considering skipping its deployment in favor of a new protocol, dubbed [obfs4](https://github.com/Yawning/obfs4), which is “like ScrambleSuit (with regards to features and threat model), but it’s faster and autofixes some of the open issues”.

George also mentions that enabling pluggable transports to work over IPv6 is on the team’s radar. As advanced deep packet inspection (DPI) on IPv6 is less common, it should buy some more time for users on censored networks.

# Miscellaneous news

David Fifield [updated](https://lists.torproject.org/pipermail/tor-talk/2014-June/033229.html) the [experimental Tor Browser builds that include the meek pluggable transport](https://people.torproject.org/~dcf/pt-bundle/3.6.2-meek-1/). The new packages are based on Tor Browser version 3.6.2.

meejah [announced](https://lists.torproject.org/pipermail/tor-dev/2014-June/007006.html) a new release of txtorcon — a Twisted-based asynchronous Tor control protocol implementation. Version 0.10.0 adds support for Twisted’s endpoint strings. meejah explains: “this means that ANY Twisted program that uses endpoints can accept ‘onion:’ strings to bring up a hidden services easily […]. Typically, no code changes to the application should be needed […].”

The Tails team [reported](https://tails.boum.org/news/report_2014_05/) progress on code, documentation, infrastructure, discussions, funding, and outreach matters for May. The report also mentions Tails’ position regarding the discontinuation of TrueCrypt.

Following up on his [earlier promise](https://lists.torproject.org/pipermail/tor-dev/2013-December/005948.html), Karsten Loesing [shut down](https://lists.torproject.org/pipermail/tor-dev/2014-June/007007.html) the Tor Metrics portal’s relay-search service, and in doing so reduced the size of the metrics database from 95 gigabytes to a mere 3. “If the metrics website shows you funny numbers in the next couple of days, please let me know”, wrote Karsten.

Andrew Lewman [reported](https://lists.torproject.org/pipermail/tor-reports/2014-June/000563.html) on his activities for May. Sebastian G. subsequently opened two discussions on the [tor-talk mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-talk): one regarding the challenges of [integrating Tor into millions of products](https://lists.torproject.org/pipermail/tor-talk/2014-June/033254.html) and another on how [US legislation is preventing the Tor Project, Inc. from receiving donations from certain countries](https://lists.torproject.org/pipermail/tor-talk/2014-June/033255.html).

Several GSoC students reported on the progress of their projects: Kostas Jakeliunas on the [BridgeDB Twitter distributor](https://lists.torproject.org/pipermail/tor-dev/2014-June/006988.html), Juha Nurmi for [ahmia.fi](https://lists.torproject.org/pipermail/tor-reports/2014-June/000562.html), and Zack Mullaly on the [HTTPS Everywhere secure ruleset update mechanism](https://lists.eff.org/pipermail/https-everywhere/2014-June/002128.html).

Lukas Erlacher has released [OnionPy 0.1.5](https://lists.torproject.org/pipermail/tor-dev/2014-June/007018.html). “If you are planning to make something in python that uses the tor network status, accessing [Onionoo](https://onionoo.torproject.org/) using OnionPy might be exactly what you need”, Lukas wrote.

The Tails developers [suggested](https://mailman.boum.org/pipermail/tails-l10n/2014-June/001293.html) that Tails translation teams using git, rather than the online Transifex platform, should begin signing their email pull requests with OpenPGP keys, to ensure that the process is not open to exploitation.

Drupal.org, the main website for the development community around the free and open-source web platform Drupal, subscribes to a blacklist that includes Tor exit nodes, making it difficult for Tor users to interact with the site. AohRveTPV [explained the problem](https://lists.torproject.org/pipermail/tor-talk/2014-June/033250.html), and asked for “ideas on how to actually achieve better Drupal.org support for Tor users”.

Chris Double [described](http://bluishcoder.co.nz/2014/06/12/using-tor-with-firefox-os.html) a detailed but experimental method for using Tor with Firefox OS, the mobile operating system from Mozilla. “This is just a proof of concept. Don’t depend on this […] Ideally Tor would be integrated with Firefox OS so that you can start and stop it as a service and maybe whitelist or blacklist sites that should and shouldn’t use Tor. I hope to do some of this over time or hope someone else gets excited enough to work on it too.”

# Tor help desk roundup

The help desk has received some complaints regarding the default window size of the Tor Browser. To prevent window size fingerprinting, the browser window size has been set to a multiple of 100 pixels according to the detected screen resolution. Taskbars in the user workspace making selecting an appropriate window size slightly more complicated though; more details are available on the [bug’s ticket](https://bugs.torproject.org/9268).

# News from Tor StackExchange

bk201 found some random-looking domain names in the logs of some network software. These connection attempts [disappeared when Tor was closed](https://tor.stackexchange.com/q/3324/88), so bk201 wants to know what they are. Lunar explained that they are requests for non-existent domain names. Tor wants to find out if some DNS servers send fake answers. This feature was [added in 2007](https://gitweb.torproject.org/tor.git/blob/HEAD:/ReleaseNotes#l6663).

user1747 often visits web sites which provide their services both within the visible web and as a hidden service (DuckDuckGo might serve as an example). [Does the Tor Browser Bundle (TBB) automatically switch to a hidden service in this case?](https://tor.stackexchange.com/q/3262/88) mirimir explained that there is no connection between DNS and the names of hidden services, so TBB doesn’t know about this hidden service and can’t connect automatically. user2949 pointed to a [plugin](https://github.com/chris-barry/darkweb-everywhere), similar to HTTPS Everywhere, that forwards a request to a hidden service if it is available.

* * *

This issue of Tor Weekly News has been assembled by harmony, Lunar, the Tails developers, Matt Pagan, Karsten Loesing, and qbi.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

