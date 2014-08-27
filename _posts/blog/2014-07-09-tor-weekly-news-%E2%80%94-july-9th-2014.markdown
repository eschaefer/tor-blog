---
layout: post
title: "Tor Weekly News — July 9th, 2014"
permalink: tor-weekly-news-%E2%80%94-july-9th-2014
date: 2014-07-09
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the twenty-seventh issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# On being targeted by the NSA

Das Erste has [published an article](http://daserste.ndr.de/panorama/aktuell/nsa230_page-1.html) and [supporting material](http://daserste.ndr.de/panorama/xkeyscorerules100.txt) showing how the NSA explicitly targets Tor and Tails user through the XKEYSCORE Deep Packet Inspection system. Several other media picked up the news, and it was also discussed in various threads on the tor-talk mailing list ( [1](https://lists.torproject.org/pipermail/tor-talk/2014-June/033473.html), [2](https://lists.torproject.org/pipermail/tor-talk/2014-July/033564.html), [3](https://lists.torproject.org/pipermail/tor-talk/2014-July/033640.html), [4](https://lists.torproject.org/pipermail/tor-talk/2014-July/033642.html), [5](https://lists.torproject.org/pipermail/tor-talk/2014-July/033656.html), [6](https://lists.torproject.org/pipermail/tor-talk/2014-July/033703.html), [7](https://lists.torproject.org/pipermail/tor-talk/2014-July/033749.html)).

The Tor Project’s view has been [reposted](https://blog.torproject.org/blog/being-targeted-nsa) on the blog. To a comment that said “I felt like i am caught in the middle of a two gigantic rocks colliding each other”, Roger Dingledine [replied](https://blog.torproject.org/blog/being-targeted-nsa#comment-64376): “You’re one of the millions of people every day who use Tor. And because of the diversity of users […], just because they know you use Tor doesn’t mean they know _why_ you use Tor, or what you do with it. That’s still way better than letting them watch all of your interactions with all websites on the Internet.”

# More monthly status reports for June 2014

The wave of regular monthly reports from Tor project members for the month of June continued, with submissions from [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2014-July/000576.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2014-July/000577.html), [Noel David Torres Taño](https://lists.torproject.org/pipermail/tor-reports/2014-July/000578.html), [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2014-July/000579.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2014-July/000580.html), [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2014-July/000583.html), and [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-July/000585.html).

Mike Perry reported on behalf of the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2014-July/000584.html).

# Miscellaneous news

An Austrian Tor exit node operator [interpreted](https://network23.org/blackoutaustria/2014/07/01/to-whom-it-may-concern-english-version/) their conviction in a first ruling as judging them “guilty of complicity, because he enabled others to transmit content of an illegal nature through the service”. Moritz Bartl from [Torservers.net](https://www.torservers.net/) [commented](https://lists.torproject.org/pipermail/tor-talk/2014-July/033613.html): “We strongly believe that it can be easily challenged. […] We will definitely try and find some legal expert in Austria and see what we can do to fight this.”

Linus Nordberg is expanding the idea of public, append-only, untrusted log à la [Certificate Transparency](http://www.certificate-transparency.org/) to the Tor consensus. Linus submitted [a new draft proposal](https://lists.torproject.org/pipermail/tor-dev/2014-July/007092.html) to the tor-dev mailing list for reviews.

Miguel Freitas [reported](https://lists.torproject.org/pipermail/tor-talk/2014-July/033580.html) that [twister](http://twister.net.co/) — a fully decentralized P2P microblogging platform — was now able to run over Tor. As Miguel wrote, “running twister on top of Tor was a long time goal, […] the Tor support allows a far more interesting threat model”.

Google Summer of Code students have sent a new round of reports after the mid-term: Israel Leiva on the [GetTor revamp](https://lists.torproject.org/pipermail/tor-dev/2014-July/007074.html), Amogh Pradeep on [Orbot and Orfox improvements](https://lists.torproject.org/pipermail/tor-dev/2014-July/007083.html), Mikhail Belous on the [multicore tor daemon](https://lists.torproject.org/pipermail/tor-dev/2014-July/007086.html), Daniel Martí on [incremental updates to consensus documents](https://lists.torproject.org/pipermail/tor-dev/2014-July/007087.html), Sreenatha Bhatlapenumarthi on the [Tor Weather rewrite](https://lists.torproject.org/pipermail/tor-dev/2014-July/007091.html), Quinn Jarrell on the [pluggable transport combiner](https://lists.torproject.org/pipermail/tor-dev/2014-July/007094.html), Noah Rahman on [Stegotorus enhancements](https://lists.torproject.org/pipermail/tor-dev/2014-July/007095.html), Marc Juarez on [website fingerprinting defenses ](https://lists.torproject.org/pipermail/tor-reports/2014-July/000581.html), development, Juha Nurmi on the ahmia.fi project , and Zack Mullaly on the [HTTPS Everywhere secure ruleset update mechanism](https://lists.eff.org/pipermail/https-everywhere/2014-July/002182.html).

sajolida, tchou and Giorgio Maone from NoScript [drafted a specification](https://mailman.boum.org/pipermail/tails-dev/2014-July/006288.html) for a Firefox extension to download and verify Tails.

# Tor help desk roundup

One way to volunteer for Tor is to run a [mirror](https://www.torproject.org/getinvolved/mirrors.html) of the Tor Project website. [Instructions](https://www.torproject.org/docs/running-a-mirror.html.en) are available for anyone wanting to run a mirror. Mirrors are useful for those who, for one reason or another, cannot access or use the main Tor Project website. Volunteers who have successfully set up a synced a mirror can report their mirror to the [tor-mirrors mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-mirrors) to get it included in the full mirrors list.

# Easy development tasks to get involved with

ooniprobe is a tool for conducting network measurements that are useful for detecting network interference. When ooniprobe starts [it should perform checks to verify that the config file is correct](https://bugs.torproject.org/11983). If that is not the case, it should fail gracefully at startup. The ticket indicates where this check should be added to the [ooniprobe codebase](https://gitweb.torproject.org/ooni-probe.git). If you’d like to do some easy Python hacking, be sure to give this ticket a try.

* * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

