---
layout: post
title: "Tor Weekly News — May 28th, 2014"
permalink: tor-weekly-news--may-28th-2014
date: 2014-05-28 07:00:00
author: harmony
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the twenty-first issue of Tor Weekly News in 2014, the weekly newsletter that covers what is happening in the Tor community.

OnionShare and tor’s ControlPort
================================

Micah Lee published [OnionShare](https://github.com/micahflee/onionshare), a program that “makes it simple to share a file securely using a password-protected Tor hidden service”. It originally ran only in Tails, but has now been made compatible with other GNU/Linux distros, Windows, and OS X. As part of that process, Micah [wondered](https://lists.torproject.org/pipermail/tor-dev/2014-May/006895.html) about the best way to make the program work with a Tor Browser or system tor process, as “I would really like to not be in the business of distributing Tor myself”. [meejah](https://lists.torproject.org/pipermail/tor-dev/2014-May/006896.html) and [David Stainton](https://lists.torproject.org/pipermail/tor-dev/2014-May/006899.html) responded with relevant details of the [Stem](https://stem.torproject.org/) and [txtorcon](https://github.com/meejah/txtorcon) controller libraries, which allow this kind of operation to take place via tor’s ControlPort.

The “Tor and HTTPS” visualization made translatable
===================================================

Lunar [announced](https://lists.torproject.org/pipermail/tor-talk/2014-May/033001.html) the creation of a [repository](https://people.torproject.org/~lunar/tor-and-https/) for an SVG+Javascript version of the EFF’s interactive [“Tor and HTTPS” visualization](https://www.eff.org/pages/tor-and-https/), which has proven useful in explaining to users the types of data that can be leaked or intercepted, and by whom, when using Tor or HTTPS (or both, or neither). As Lunar wrote, “The good news is that it’s translatable”: copies have so far been published in over twenty languages. The amount of translation required is very small, so if you’d like to contribute in your language then download the [POT file](https://gitweb.torproject.org/user/lunar/tor-and-https.git/blob/HEAD:/tor-and-https.pot) and submit a patch!

A Child’s Garden of Pluggable Transports
========================================

David Fifield [published](https://lists.torproject.org/pipermail/tor-dev/2014-May/006891.html) [“A Child’s Garden of Pluggable Transports”](https://trac.torproject.org/projects/tor/wiki/doc/AChildsGardenOfPluggableTransports), a detailed visualization of different pluggable transport protocols, including “aspects of different transports that I think are hard to intuit, such as what flash proxy rendezvous looks like, and how transports look under the encrypted layer that is visible to a censor”. A few [other transports supported by Tor](https://www.torproject.org/docs/pluggable-transports) are not yet discussed in the guide; “if you know how to run any of those transports, and you know an effective way to visualize it, please add it to the page”, wrote David.

Miscellaneous news
==================

Anthony G. Basile [released](http://opensource.dyc.edu/pipermail/tor-ramdisk/2014-May/000131.html) version 20140520 of [tor-ramdisk](http://opensource.dyc.edu/tor-ramdisk), the micro Linux distribution “whose only purpose is to host a Tor server in an environment that maximizes security and privacy”. The new version upgrades Tor to version 0.2.4.22, which “adds an important block to authority signing keys that were used on authorities vulnerable to the “heartbleed” bug in OpenSSL”, among other fixes; upgrading “is strongly recommended”.

Cure53 [audited the security](https://cure53.de/pentest-report_onion-browser.pdf) of the [Onion Browser](https://mike.tig.as/onionbrowser/), a web browser for iOS platforms tunneling traffic through Tor. From the conclusion: “we believe that the Onion Browser project is on the right track, however there is still a long way ahead for the project to be appropriately ‘ripe’ for usage in actually privacy-relevant and critically important scenarios.” All reported issues should have been fixed in [release 1.5](https://mike.tig.as/onionbrowser/security/#v1_5) on May 14th.

A new pluggable transport, currently named [obfs4](https://github.com/Yawning/obfs4), is being crafted by Yawning Angel: “obfs4 is ScrambleSuit with djb crypto. Instead of obfs3 style UniformDH and CTR-AES256/HMAC-SHA256, obfs4 uses a combination of Curve25519, Elligator2, HMAC-SHA256, XSalsa20/Poly1305 and SipHash-2-4”. The feature set offered by obfs4 is comparable to ScrambleSuit, with minor differences. Yawning is now asking the community for [comments, reviews, and tests](https://lists.torproject.org/pipermail/tor-dev/2014-May/006897.html).

Stem now offers a [control interpreter](https://blog.torproject.org/blog/new-feature-tor-interpreter), “a new method for interacting with Tor’s control interface that combines an interactive python interpreter with raw access similar to telnet”. Damian Johnson wrote a [new tutorial](https://stem.torproject.org/tutorials/down_the_rabbit_hole.html) to give an overview of what can be done with it.

Also on the controller front, Yawning Angel hacked on [or-applet](https://github.com/yawning/or-applet), a Gtk+ system tray applet to monitor Tor circuits.

Arlo Breault is making progress on the Tor Instant Messenger Bundle: a minimalistic [user interface for OTR encryption in Instantbird](https://bugs.torproject.org/11533), one of the key features missing from the finished software, has now been implemented.

Nicolas Vigier has been [working](https://lists.torproject.org/pipermail/tor-dev/2014-May/006911.html) on improving the [Mbox sandboxing environment](https://github.com/tsgates/mbox/) to test the Tor Browser for disk or network leaks.

Israel Leiva [published](https://lists.torproject.org/pipermail/tor-dev/2014-May/006903.html) the initial version of a [design proposal](https://github.com/ileiva/gettor/blob/master/spec/overview.txt) for the “Revamp GetTor” Google Summer of Code project, having concluded that a full rewrite is needed.

Juha Nurmi submitted the [first weekly report](https://lists.torproject.org/pipermail/tor-reports/2014-May/000536.html) for the ahmia.fi GSoC project.

kzhm [sent out](https://lists.torproject.org/pipermail/tor-talk/2014-May/033032.html) instructions for installing obfsproxy on Fedora 20, to go with [those for other Linux distributions](https://www.torproject.org/projects/obfsproxy-instructions.html).

[AddressSanitizer](https://code.google.com/p/address-sanitizer/wiki/AddressSanitizer) (ASan) is a powerful memory error detector: software built with such technology makes it a lot harder to exploit programming errors related to memory management. Happily, Georg Koppen has [announced](https://lists.torproject.org/pipermail/tor-qa/2014-May/000414.html) the first test packages of the Tor Browser built with ASan hardening.

Karsten Loesing is planning on [spinning off the directory archive from the metrics portal](https://lists.torproject.org/pipermail/tor-dev/2014-May/006909.html).

Tor help desk roundup
=====================

Multiple Mac OS X users complained that despite seeing the “Congratulations” welcome page, they were unable to reach any website with the Tor Browser. It appears that with a recent update, the Sophos anti-virus solution interferes with the Tor Browser. In order to be able to use the Tor Browser again, one must open Sophos Anti-Virus, then “Preferences”, and in the “Web Protection” panel position all switches to off.

News from Tor StackExchange
===========================

yohann2008 doesn’t want their hidden service to be [indexed by search engines](https://tor.stackexchange.com/q/2130/88). puser suggested using a [robots.txt file](https://en.wikipedia.org/wiki/Robots_exclusion_standard), as on a normal webpage. Jens Kubieziel later received confirmation on the IRC channel of [ahmia.fi](https://ahmia.fi/) that this search engine does indeed respect the robots.txt; however, it is unknown whether others do.

Herbalist saw the [following line in their log file](https://tor.stackexchange.com/q/1866/88) and wonders what it could mean: “Rejecting INTRODUCE1 on non-OR or non-edge circuit 7503”. If you can unravel this mystery, please submit your answer to the question.

Easy development tasks to get involved with
===========================================

The metrics website displays graphs on [bridge users by pluggable transport](https://metrics.torproject.org/users.html#userstats-bridge-transport), but we’d like to have another graph with [total pluggable transport usage](https://bugs.torproject.org/11799). Karsten Loesing outlined the steps for adding such a graph, which require some knowledge of R and ggplot2. If you enjoy writing R and want to add this new graph to the metrics website, give it a try and post your results on the ticket.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, qbi, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
