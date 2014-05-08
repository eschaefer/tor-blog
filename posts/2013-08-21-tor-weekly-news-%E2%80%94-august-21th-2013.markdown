---
layout: post
title: "Tor Weekly News — August, 21th 2013"
permalink: tor-weekly-news-%E2%80%94-august-21th-2013
date: 08/21/2013
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the eighth issue of Tor Weekly News, the weekly newsletter that covers what is happening in the great Tor community.

# Future of pluggable transports integration

While David Fifield was busy updating the [Pluggable Transports Bundle](https://www.torproject.org/docs/pluggable-transports.html.en) to match the “classic” bundle version 0.2.4.16-beta-1, several discussions took place on how to better integrate pluggable transports in the future.

bastik opened [#9444](https://bugs.torproject.org/9444), pointing out that “currently TBB with Pluggable Transports are build separately, thus lagging behind”. Having two separate bundles is also a long standing usability issue, as often [users have tried to add “obfs” bridges to their normal TBB](https://bugs.torproject.org/9156).

Mike Perry is fully aware of the issue and stated in the discussion that his “long term goal is to try to cram all of the pluggable transports into The One True Bundle.”

This will require modifications to the new “Tor Launcher” component of the TBB 3.x series in order to allow users to select the bridges and pluggable transports they wish to use. Compromises might be needed on how users should input bridges. BridgeDB [recently stopped](https://gitweb.torproject.org/user/isis/bridgedb.git/commit/792cfd9) having the “bridge” keyword in front of the addresses it replies with as Vidalia would not understand it. Mike Perry was thinking in exactly the opposite direction: “take bridge lines directly from bridgedb […] verifying only that they start with ‘bridge’”. Maybe the transition could be easier if [Florian Stinglmayr’s patch to Vidalia](https://github.com/n0la/vidalia/tree/master-bug/6724) was merged so that current bundles would [ignore the “bridge” keyword](https://bugs.torproject.org/6724) when entering bridges.

In any case, Mike wants to solve these issues “before we release as beta/stable, to minimize user confusion.”

Another tricky part of the “One True Bundle” solution is the bundle size, making it harder to [circumvent download restrictions through email](https://www.torproject.org/projects/gettor.html). But, as Mike said, “even if they don’t, we’ll probably have to find some other solution anyway for gettor, because the intersection of gettor users and PT users is probably high.”

# Extended ORPort land in tor 0.2.5

After more than a year and a half in the making, the [Extended ORPort mechanism](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/196-transport-control-ports.txt) has been [merged by Nick Mathewson into the tor master branch](https://gitweb.torproject.org/tor.git/commit/74262f15). This will allow pluggable transport proxies to exchange arbitrary operational information and metadata with tor clients and bridges.

Such plumbing was needed in order to make some pluggable transports easier to use or to allow Tor to gather more data about the state of the transports used.

obfsproxy has [supported this new communication channel](https://gitweb.torproject.org/pluggable-transports/obfsproxy.git/blob/HEAD:/obfsproxy/network/extended_orport.py) for a little while and was only waiting for tor to catch up. George Kadianakis thus [asked obfsbridge operators to upgrade their tor to git master](https://lists.torproject.org/pipermail/tor-relays/2013-August/002477.html) to enable client statistics.

Once they do, their bridges will send statistics on users per transport to the bridge authority, and they will be [published on metrics.torproject.org](https://metrics.torproject.org/users.html?graph=userstats-bridge-transport&transport=obfs3#userstats-bridge-transport). This helps track deployment of pluggable transports in the future.

# A new implementation for the web side of check.torproject.org

Arlo Breault wrote a [new implementation for the web component of check.torproject.org](https://github.com/arlolra/check/) in the Go programming language, in response to [Roger Dingledine’s appeal](https://lists.torproject.org/pipermail/tor-talk/2013-August/029306.html): “Check could really use some love. Any volunteers please?”.

There is already a ticket to [replace the check.torproject.org servers](https://bugs.torproject.org/9529) with Arlo’s Go version. Andrew Lewman stated again that “As for check.tpo website, it shouldn’t exist at all”, as it is an architectural issue to “have the entire tor browser userbase hit a single website to learn ’Tor or not’”. Until all clients are changed to stop using check, deploying a new code base would only make sense if it was at least able to handle “500 requests per second on really busy times”. More benchmarks are probably needed with Arlo’s implementation.

On another front, tup, the [initial author of TorDNSEL](https://gitweb.torproject.org/tordnsel.git/commit/99d490), has resurfaced to [offer to update the code](https://bugs.torproject.org/9204#comment:14) to work with newer Haskell environments after many years of silence!

# Tor exit crowdfunding

Moritz Bartl from [torservers.net](https://www.torservers.net/) posted an [update on their ongoing crowdfunding campaign](https://lists.torproject.org/pipermail/tor-talk/2013-August/029431.html) to support Tor exit bandwidth. The fund just went over €3000, and there are still a few days left!

For more information, and ways to contribute, please [visit the Indiegogo page](http://www.indiegogo.com/projects/tor-anti-censorship-and-anonymity-infrastructure/)

# A Flattr-like incentive for Tor relays?

While torservers.net is presently collecting euros, George Kadianakis asked for comments from the Tor community about “a practical crowdfunded Flattr-like incentive scheme for Tor relays”, dubbed [Flattor](https://lists.torproject.org/pipermail/tor-talk/2013-August/029419.html).

George’s proposal is meant to solve “one of the problems of scaling Tor to tens of millions of users”, that “Tor’s bandwidth capacity is finite”. He observes that “lately the bandwidth coming out of Tor-friendly organizations (like torservers.net, universities, etc.) seems to increase” and is worried that “Tor might end up looking like the Bitcoin network — where a number of organizations (mining pools) drive the network.”

What George would like to see is incentives for contributing to the network. After studying schemes proposed in the past, all deemed “hard to implement and deploy”, George proposes a simple approach: users can opt to spend a fixed amount of bitcoins to support the Tor network, and their donation will be divided according to the bandwidth of each relay. Obviously, relay operators who wish to receive such contributions would need to publish a bitcoin address, probably in the “contact” field.

There might be some concerns with such scheme, or any monetary incentives scheme, as George summarized: “If relay operators start getting money for their bandwidth, we might end up with relay operators that are just in for the money. It might then be easier for a three-letter org to persuade those relay operators to snoop on their users (by giving them double the money they are currently getting).”

Moritz Bartl [commented](https://lists.torproject.org/pipermail/tor-talk/2013-August/029421.html) that the idea was already quite close to torservers.net current plan, to the extent that donations were distributed “across all participating organizations based on […] advertised bandwidth and a country-specific factor.” Moritz also pointed out that similar discussions had already happened in the past when a [sponsor wished to fund faster exit relays](https://blog.torproject.org/blog/turning-funding-more-exit-relays).

George concluded his mail by saying that he is “not even sure if such an incentive scheme is a good idea, but posting bad ideas to mailing lists is what the Internet is for, right?”

Feel free to join the discussion, or hack wildly.

# Miscellaneous news

The new release of Orbot 12.0.3 comes with a shiny new icon and graphics, bugfixes, and Tor 0.2.4.16-rc. You can download the update [via Google Play](https://play.google.com/store/apps/details?id=org.torproject.android) or straight [from Guardian Project’s website](https://guardianproject.info/releases/orbot-latest.apk).

Andrew Lewman has published the [financial reports of the Tor Project for the year 2012](https://blog.torproject.org/blog/transparency-openness-and-our-2012-financial-docs).

Arturo has sent his [report for July 2013](https://lists.torproject.org/pipermail/tor-reports/2013-August/000313.html).

Runa Sandvik [reported on her trip to Black Hat & DEF CON](https://lists.torproject.org/pipermail/tor-reports/2013-August/000312.html). She managed to fill “the Penn & Teller theater (~1500 people)” for a [talk](https://www.defcon.org/html/defcon-21/dc-21-speakers.html#Sandvik) about “the safety of the Tor network which focused on network diversity, relay operators, and misbehaving relays.” The former Tor GSoC student Brandon Wiley also gave an [update](https://www.defcon.org/html/defcon-21/dc-21-speakers.html#Wiley) on [Dust](https://github.com/blanu/Dust/) — “an Internet protocol designed to resist a number of attacks currently in active use to censor Internet communication.”

Karsten Loesing has [made progress](https://trac.torproject.org/projects/tor/ticket/9166#comment:23) on “experimenting with a client and private bridge connected over uTP”. The connection can be established, but strange timing issues remain to be solved.

George Kadianakis has sent two new proposals to [improve hidden service identity key security](https://lists.torproject.org/pipermail/tor-dev/2013-August/005279.html) and [prevent address enumeration](https://lists.torproject.org/pipermail/tor-dev/2013-August/005280.html). TWN will cover these proposals in detail once the draft deployment strategy is published. Feel free to help refine the proposals in the meantime!

# Help Desk Roundup

Users experience confusion when trying to update the Tor Browser Bundle. Users are not always aware that the Tor Browser Bundle does not have an autoupdate function. Some users will download the latest release from the Tor Project website, then ask “Ok, what do I do now?”. We recommend closing the browser, then deleting one’s current Tor Browser folder before unpacking the new download.

One person asked for help while using the Pirate Browser. Torrent-sharing website The Pirate Bay released the Pirate Browser this week as a fork of the Tor Browser Bundle. The Pirate Browser is not endorsed or recommended by the Tor Project. It is unclear what the advantages are compared to using the Tor Browser Bundle and no source code is available.

* * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, malaparte, mttp, Karsten Loesing, and harmony.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing-list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

