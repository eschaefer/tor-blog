---
layout: post
title: "Tor Weekly News — October 9th, 2013"
permalink: blog/tor-weekly-news-%E2%80%94-october-9th-2013
date: 2013-10-09
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the fifteenth issue of Tor Weekly News, the [weekly newsletter](https://lists.torprojet.org/cgi-bin/mailman/listinfo/tor-news) that covers what's happening in the world of Tor — [“king of high-secure, low-latency anonymity”](http://www.theguardian.com/world/interactive/2013/oct/04/tor-high-secure-internet-anonymity).

# New tranche of NSA/GCHQ Tor documents released

After a cameo appearance in [previous leaked intelligence documents](https://blog.torproject.org/blog/tor-nsa-gchq-and-quick-ant-speculation), Tor found itself at the center of attention in the latest installment of the ongoing Snowden disclosures after a series of stories were published in the Guardian and the Washington Post that detailed alleged attempts by NSA, GCHQ, and their allies to defeat or circumvent the protection that Tor offers its users. A number of source materials, redacted by the newspapers, were published to accompany the articles.

The [documents in question](http://media.encrypted.cc/files/nsa) offer, alongside characteristically [entertaining illustrations](https://twitter.com/EFF/status/386291345301581825), an overview of the Tor network from the point of view of the intelligence agencies, as well as a summary of attacks against Tor users and the network as a whole that they have considered or carried out.

Despite the understandable concern provoked among users by these disclosures, Tor developers themselves were encouraged by the often relatively basic or out-of-date nature of the attacks described. In response to one journalist's request for comment, Roger Dingledine [wrote](https://blog.torproject.org/blog/yes-we-know-about-guardian-article#comment-35793) that “we still have a lot of work to do to make Tor both safe and usable, but we don't have any new work based on these slides”.

Have a look at the documents yourself, and feel free to raise any questions with the community on the mailing lists or IRC channels.

# tor 0.2.5.1-alpha is out

Roger Dingledine [announced](https://lists.torproject.org/pipermail/tor-talk/2013-October/030269.html) the first alpha release in the tor 0.2.5.x series, which among many other improvements introduces experimental support for syscall sandboxing on Linux, as well as statistics reporting for pluggable transports usage on compatible bridges.

Roger warned that “this is the first alpha release in a new series, so expect there to be bugs. Users who would rather test out a more stable branch should stay with 0.2.4.x for now.” 0.2.5.1-alpha will not immediately appear on the main download pages, in order to avoid having too many versions listed at once. Please feel free to test the [new release](https://www.torproject.org/dist/), and report any bugs you find!

# How did Tor achieve reproducible builds?

At the end of June, Mike Perry [announced](https://blog.torproject.org/blog/tor-browser-bundle-30alpha2-released) the first release of the Tor Browser Bundle 3.0 alpha series, featuring release binaries “exactly reproducible from the source code by anyone”. In a subsequent [blog post](https://blog.torproject.org/blog/deterministic-builds-part-one-cyberwar-and-global-compromise) published in August, he explained why it mattered.

Mike has just published the [promised follow-up piece](https://blog.torproject.org/blog/deterministic-builds-part-two-technical-details) describing how this feat was achieved in the new Tor Browser Bundle build process.

He explains how [Gitian](http://gitian.org/howto.html) is used to create a reproducible build environment, the tools used to produce cross-platform binaries for Windows and OS X from a Linux environment, and several issues that prevented the builds from being entirely deterministic. The latter range from timestamps to file ordering differences when looking up a directory, with an added 3 bytes of pure mystery.

There is more work to be done to “prevent the adversary from compromising the (substantially weaker) Ubuntu build and packaging processes” currently used for the toolchain. Mike also wrote about making the build of the compiler and toolchain part of the build process, cross-compilation between multiple architectures, and the work being done by Linux distributions to produce deterministic builds from their packages.

If you are interested in helping, or working on your own software project, there is a lot to be learned by reading the blog post in full.

# Toward a new Tor Instant Messaging Bundle

A first meeting last week kicked-off the “ [Attentive Otter project](https://trac.torproject.org/projects/tor/wiki/org/sponsors/Otter/Attentive)” which aims to come up with a new bundle for instant messaging. The first meeting mainly consisted in trying to enumerate the various options.

In the end, people volunteered to research three different implementation ideas. Thijs Alkemade and Jurre van Bergen explored the [possibilty of using Pidgin/libpurple](https://lists.torproject.org/pipermail/tor-dev/2013-October/005544.html) as the core component. Jurre also prepared an [analysis of xmpp-client](https://lists.torproject.org/pipermail/tor-dev/2013-October/005546.html), together with David Goulet, Nick Mathewson, Arlo Breault, and George Kadianakis. As a third option, Mike Perry took a [closer look at Instantbird/Thunderbird](https://lists.torproject.org/pipermail/tor-dev/2013-October/005555.html) with Sukhbir Singh.

All the options have their pros and cons, and they will probably be discussed on the tor-dev mailing list and at the next “Attentive Otter” meeting.

# More monthly status reports for September 2013

The wave of regular monthly reports from Tor project members continued this week with submissions from [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2013-October/000346.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2013-October/000347.html), [Sathyanarayanan Gunasekaran](https://lists.torproject.org/pipermail/tor-reports/2013-October/000348.html), [Ximin Luo](https://lists.torproject.org/pipermail/tor-reports/2013-October/000349.html), [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2013-October/000350.html), [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2013-October/000351.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2013-October/000352.html), [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2013-October/000353.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2013-October/000354.html), [Jason Tsai](https://lists.torproject.org/pipermail/tor-reports/2013-October/000355.html), the [Tor help desk](https://lists.torproject.org/pipermail/tor-reports/2013-October/000356.html), [Sukhbir Singh](https://lists.torproject.org/pipermail/tor-reports/2013-October/000357.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2013-October/000358.html), [Mike Perry](https://lists.torproject.org/pipermail/tor-reports/2013-October/000359.html), [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2013-October/000360.html), [Aaron G](https://lists.torproject.org/pipermail/tor-reports/2013-October/000361.html), and the [Tails folks](https://lists.torproject.org/pipermail/tor-reports/2013-October/000362.html).

# Tor Help Desk Roundup

A number of users wanted to know if Tor was still safe to use given the recent news that Tor users have been targeted by the NSA. We directed these users to the Tor Project's [official statement on the subject](https://blog.torproject.org/blog/yes-we-know-about-guardian-article).

One of the most popular questions the help desk receives continues to be whether or not Tor is available on iOS devices. Currently there is no officially supported solution, although more than one project has been presented ( [1](https://lists.torproject.org/pipermail/tor-dev/2013-October/005542.html), [2](https://trac.torproject.org/projects/tor/ticket/8933)).

The United Kingdom is now one of the countries where citizens request assistance circumventing a [national firewall](https://lists.torproject.org/pipermail/tor-talk/2013-July/029054.html).

# Miscellaneous news

Thanks to [Grozdan](https://lists.torproject.org/pipermail/tor-mirrors/2013-September/000366.html), [Simon Gattner from Netzkonstrukt Berlin](https://lists.torproject.org/pipermail/tor-mirrors/2013-September/000370.html), [Wollomatic](https://lists.torproject.org/pipermail/tor-mirrors/2013-October/000374.html), and [Haskell](https://lists.torproject.org/pipermail/tor-mirrors/2013-October/000375.html) for setting up new mirrors of the Tor project website.

Arlo Breault sent out a [request for comments](https://lists.torproject.org/pipermail/tor-talk/2013-October/030253.html) on a possible new version of the check.torproject.org page.

Runa Sandvik [announced](https://lists.torproject.org/pipermail/tor-talk/2013-October/030269.html) that the Tor Stack Exchange page has moved from private beta to public beta. If you'd like to help answer Tor-related questions (or ask them), [get involved now](http://tor.stackexchange.com/)!

Philipp Winter sent out a [call for testing](https://lists.torproject.org/pipermail/tor-talk/2013-October/030252.html) (and installation instructions) for the ScrambleSuit pluggable transports protocol.

Not strictly Tor-related, but Mike Perry started an [interesting discussion](https://lists.torproject.org/pipermail/tor-talk/2013-September/030235.html) about the “web of trust” system, as found in OpenPGP. The discussion was also held on the MonkeySphere mailing list, which prompted Daniel Kahn Gilmor to reply with many clarifications regarding the various properties and processes of the current implementation. To sum it up, Ximin Luo [started](https://lists.riseup.net/www/arc/monkeysphere/2013-10/msg00000.html) a [new documentation project](https://github.com/infinity0/idsec/) “to describe and explain security issues relating to identity, in (hopefully) simple and non-implementation-specific language”.

The _listmaster_ role has been [better defined](https://trac.torproject.org/projects/tor/wiki/org/operations/Infrastructure/lists.torproject.org) and is now performed by a team consisting of Andrew Lewman, Damian Johnson, and Karsten Loesing. Thanks to them!

Roger Dingledine released an [official statement](https://blog.torproject.org/blog/tor-and-silk-road-takedown) on the Tor project blog regarding the takedown of the Silk Road hidden service and the arrest of its alleged operator.

Fabio Pietrosanti [asked](https://lists.torproject.org/pipermail/tor-talk/2013-October/030405.html) for reviews of “experimental Tor performance tuning for a Tor2web node.” Feel free to [have a look](https://github.com/globaleaks/Tor2web-3.0/wiki/Performance-tuning) and provide feedback.

Claudiu-Vlad Ursache [announced](https://lists.torproject.org/pipermail/tor-dev/2013-October/005545.html) the initial release of [CPAProxy](https://github.com/ursachec/CPAProxy), “a thin Objective-C wrapper around Tor”. This is the first component of a project to “release a free open-source browser on the App Store that uses this wrapper and Tor to anonymize requests.” Claudiu-Vlad left several questions open, and solicited opinions on the larger goal.

* * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, dope457 and Matt Pagan.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

