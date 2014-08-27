---
layout: post
title: "Tor Weekly News — February 19th, 2014"
permalink: tor-weekly-news-%E2%80%94-february-19th-2014
date: 2014-02-19
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the seventh issue of Tor Weekly News in 2014, the weekly newsletter that covers what is happening in the [inked](http://redd.it/1y5y49) Tor community.

# Tor 0.2.5.2-alpha is out

Roger Dingledine [announced](https://lists.torproject.org/pipermail/tor-talk/2014-February/032150.html) the second alpha release in the Tor 0.2.5 series. As well as incorporating “all the fixes from 0.2.4.18-rc and 0.2.4.20, like the “poor random number generation” fix and the “building too many circuits” fix”, this release brings with it several new features of its own, among them the forced inclusion of at least one relay capable of the NTor handshake in every three-hop circuit, which should reduce the chance “that we’re building a circuit that’s worth attacking by an adversary who finds breaking 1024-bit crypto doable”, as Roger wrote.

You can read the full changelog in Roger’s announcement, and download the new release from [the Tor Project website](https://www.torproject.org/dist/).

# Tor Browser 3.5.2.1 is released

A [new point release of the Tor Browser Bundle was put out](https://blog.torproject.org/blog/tor-browser-3521-released) on February 15th. A change in how Mozilla tags Firefox releases [broke the localization](https://bugs.torproject.org/10895) of the browser interface. This release restores proper behavior for languages other than English.

Apart from the localization fix and the removal of unneeded libraries from the Windows bundles, no other changes have been made.

# Help draft a proposal for partnership with the Wikimedia Foundation

The relationship between Tor users and the Wikimedia Foundation, which operates Wikipedia and related projects, is currently not as good as it could be: many Tor users feel they should be able to contribute to Wikipedia anonymously, while many Wikipedia editors are wary of dealing with a tool that could enable untraceable or unblockable vandalism of pages and articles.

As a prelude to resolving this conflict, Lane Rasberry has [opened a discussion](https://meta.wikimedia.org/wiki/Grants:IdeaLab/Partnership_between_Wikimedia_community_and_Tor_community) on the Wikimedia Foundation’s IdeaLab, a forum in which ideas can be discussed and debated before being collaboratively developed into full grant proposals. As Lane wrote, “persons using Tor (the anonymity network) should be able to create Wikipedia accounts and contribute to Wikipedia while logged into those accounts. Some technical problems currently disallow this and some social problems prevent the technical problems from being addressed. Anyone with a proposal of what kind of relationship Tor and the Wikimedia movement should have should describe it here.”

If you are interested in helping to resolve this issue, please see the IdeaLab page, and add your comments!

# Only as good as your weakest transport?

Delton Barnes [pointed out](https://lists.torproject.org/pipermail/tor-relays/2014-February/003906.html) that although the ScrambleSuit pluggable transport protocol includes a certain amount of protection against active probing for bridges by censorship systems like the Chinese “Great Firewall”, bridge operators who run more vulnerable protocols like obfs3 alongside ScrambleSuit may be increasing the risk that censors will discover their relay and block connections to it of any kind.

In reply, Philipp Winter [conceded](https://lists.torproject.org/pipermail/tor-relays/2014-February/003907.html) that although the Chinese censorship system currently seems to block bridges by IP:port tuples, rather than by IP address alone, the mere presence of an easily-discoverable pluggable transport protocol (or a public relay) on a given machine makes it more likely that a censor will be motivated to try and defeat protections such as those offered by ScrambleSuit. “So you are right, only running ScrambleSuit gives your bridge more protection than running other protocols at the same time — at the cost of attracting less users, however”, he concluded.

# Miscellaneous news

The Tails team has published [its report for January 2014](https://tails.boum.org/news/report_2014_01/). A lot is happening in the growing community of Tails developers. Have a look!

Qingping Hou sent out the beginnings of a proposal to increase the speed of connections to Tor Hidden Services by using circuits of only five hops, and [asked the community for feedback](https://lists.torproject.org/pipermail/tor-dev/2014-February/006198.html).

Yawning Angel called for help with testing obfsclient, a C++ pluggable transport client, and clarified the [next steps in the development process](https://lists.torproject.org/pipermail/tor-dev/2014-February/006211.html).

David Fifield [made available a second updated set of the experimental Tor Pluggable Transport Bundle with tor-fw-helper](https://lists.torproject.org/pipermail/tor-qa/2014-February/000338.html), which fixes several of the errors encountered in the first version.

Nick Mathewson [called for help with reviewing proposal 227](https://lists.torproject.org/pipermail/tor-dev/2014-February/006230.html), which involves “extending the Tor consensus document to include digests of the latest versions of one or more package files, to allow software using Tor to determine its up-to-dateness, and help users verify that they are getting the correct software”.

Efforts to include the FTE protocol in the Tor Pluggable Transport Bundles have taken a step forward, as Kevin P. Dyer [announced](https://lists.torproject.org/pipermail/tor-dev/2014-February/006223.html) the release of a patch including fteproxy that not only works, but also builds deterministically, in keeping with the Tor Project’s focus on [build security](https://blog.torproject.org/blog/deterministic-builds-part-one-cyberwar-and-global-compromise).

Rusty Bird [announced](https://lists.torproject.org/pipermail/tor-talk/2014-February/032152.html) the release of [corridor](https://github.com/rustybird/corridor), a Tor traffic whitelisting gateway. corridor will turn a Linux system into a router that “allows only connections to Tor relays to pass through (no clearnet leaks!)”. However, unlike transparent proxying solutions, “client computers are themselves responsible for torifying their own traffic.”

One relay operator was looking for an `init.d` script able to start multiple tor instances. Johannes Fürmann [pointed out](https://lists.torproject.org/pipermail/tor-relays/2014-February/003915.html) that one was [available in the torservers.net Git repository](https://github.com/torservers/setup-automation/blob/master/config/initd-tor).

TorBirdy, the Tor-enabling extension for the Thunderbird mail client, currently disables the automated account configuration system for security reasons. [Progress is being made](https://bugs.torproject.org/1083) in changing the behavior to make it fit the expectations of Tor users.

Andrea Shepard submitted seven status reports, covering her activity since July 2013 ( [July](https://lists.torproject.org/pipermail/tor-reports/2014-February/000455.html), [August](https://lists.torproject.org/pipermail/tor-reports/2014-February/000456.html), [September](https://lists.torproject.org/pipermail/tor-reports/2014-February/000457.html), [October](https://lists.torproject.org/pipermail/tor-reports/2014-February/000458.html), [November](https://lists.torproject.org/pipermail/tor-reports/2014-February/000459.html), [December](https://lists.torproject.org/pipermail/tor-reports/2014-February/000460.html), [January](https://lists.torproject.org/pipermail/tor-reports/2014-February/000461.html)).

# Tor help desk roundup

Users often ask for help updating their Tor Browser Bundle. Some users download and try to run their new Tor Browser without first closing their current Tor Browser. This causes an error message, since Tor is already running. The Tor Browser Bundle update is not an upgrade that can be applied while Tor Browser is still running. Users must close their current Tor Browser before running their newly downloaded Tor Browser Bundle.

* * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, and Matt Pagan.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

