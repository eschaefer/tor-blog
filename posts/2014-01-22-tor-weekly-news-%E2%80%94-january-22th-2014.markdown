---
layout: post
title: "Tor Weekly News — January 22th, 2014"
permalink: tor-weekly-news-%E2%80%94-january-22th-2014
date: 01/22/2014
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the third issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Future of the geolocalization database used in Tor software

The first version of Tor to include an IP-to-country database was [0.2.0.27-rc](https://gitweb.torproject.org/tor.git/tree/ee60a8dd), released in 2008. In 2010, the [database switched](https://gitweb.torproject.org/tor.git/commit/befcc84f) from data provided by WebHosting.Info to use the more up-to-date MaxMind’s GeoLite service. All was good, until two years later when MaxMind started to [hide the country of Tor relays](https://bugs.torproject.org/6266), marking them as from the “A1” country, standing for “anonymous proxy”. Karsten Loesing has been tirelessly doing manual database updates ever since.

MaxMind has [launched GeoIP2](http://blog.maxmind.com/2013/07/01/introducing-the-geoip2-beta/) as a successor of its previous service. The very good news, as [spotted by Karsten](https://lists.torproject.org/pipermail/tor-dev/2014-January/006080.html), is that the new format “provide the A1/A2 information in \*addition\* to the correct country codes”.

The question lies on how should this new database be integrated into the different software using geolocalization information: Tor, BridgeDB, the metrics database and the metrics website. The format used by Tor so far has always been a custom format, so writing a converter from MaxMind’s database format is one option. Another option is to integrate the parsing libraries provided by MaxMind into Tor software.

Both approaches have their advantages. In any cases, they can be useful, fun and small projects for someone new to the Tor community. Be sure to have a look at Karsten’s suggestions if you feel like helping.

# Key generation on headless and diskless relays

Following up on his work on [Torride](https://redmine.koumbit.net/projects/torride) — a live Linux distribution meant to run Tor relays — anarcat asked about key generation in low entropy situation. Lunar had [raised](http://opensource.dyc.edu/pipermail/tor-ramdisk/2013-January/000101.html) a similar question for the [Tor-ramdisk distribution](http://opensource.dyc.edu/tor-ramdisk/) a couple of months ago.

“The concern here is what happens when Tor starts up the first time. I believe it creates a public/private key pair for its cryptographic routines. In Torride, this is done right on the start of the operating system, when the entropy of the system is low or inexistent” explained anarcat.

Gerardus Hendricks has made a [quick analysis](https://lists.torproject.org/pipermail/tor-talk/2014-January/031725.html) of Tor source code to determine that key were generated using entropy from `/dev/urandom` — an insecure behavior in low entropy situation.

Nick Mathewson [suggested](https://lists.torproject.org/pipermail/tor-talk/2014-January/031773.html) to change the initialization procedure in order to “try to read a byte from `/dev/random` before it starts Tor, and block until it actually can read that byte.“ This would “ensure that the kernel RNG has (by its own lights) reached full entropy at least once, which guarantees cryptographic quality of the rest of the `/dev/urandom` stream.” More general solutions are now discussed in a [newly created ticket](https://bugs.torproject.org/10676).

# Exposing malicious exit relays

Anyone is free to start a new Tor relay and join the Tor network. Most Tor relay operators are volunteers who dedicate time and money to support online privacy.

Unfortunately, as Philipp Winter and Stefan Lindskog wrote in the introduction of their [new research project](http://www.cs.kau.se/philwint/spoiled_onions/), “there are exceptions: in the past, some exit relays were documented to have [sniffed](http://www.cs.columbia.edu/~mikepo/papers/tordecoys.raid11.pdf) and [tampered with](https://trac.torproject.org/projects/tor/wiki/doc/badRelays) relayed traffic”. The project, dubbed “spoiled onions”, is meant to “monitoring all exit relays for several months in order to expose, document, and thwart malicious or misconfigured relays”.

The [paper](http://www.cs.kau.se/philwint/spoiled_onions/techreport.pdf) gives more details on the [modular scanning software](https://github.com/NullHypothesis/exitmap) that has been developed. It elaborates on how it can detect tampering with the HTTP, HTTPS, SSH, and DNS protocols. The paper also discusses that occasionally it’s the relay’s ISP that is responsible for an attack despite the operator’s good faith.

The authors also describe an extension to the Tor Browser that can help with detecting HTTPS man-in-the-middle attacks: if the browser is unable to verify a certificate, it will automatically retrieve the certificate again using a different Tor exit node. If the certificates do not match, a warning can then be issued informing the user that an attack might be happening and offering to notify the Tor Project. However, the extension is merely a proof of concept and not usable at this point.

Philipp and Stefan’s efforts have already identified 25 bad relays that have subsequently been marked as such by directory authority operators. Even if we wish the number of problematic relays to stay low, let’s hope this will help to identify those who try to abuse Tor users as soon as possible in the future.

# Miscellaneous news

Alex [reported](https://lists.torproject.org/pipermail/tor-relays/2014-January/003620.html) his bad experience with Hetzner when attempting to participate in the [“Trusted Tor Traceroutes” experiment](https://web.engr.illinois.edu/~das17/tor-traceroute_v1.html). Paul Görgen [reported](https://lists.torproject.org/pipermail/tor-relays/2014-January/003625.html) having similar troubles, even with a lower packet per second rate. Relay operators might want to warn their ISP before undertaking the experiment in the future to avoid similar misadventures.

Anupam Das [reported](https://lists.torproject.org/pipermail/tor-relays/2014-January/003686.html) that they have “received a good rate of participation by relay operators to [our measurement project](https://web.engr.illinois.edu/~das17/tor-traceroute_v1.html)”. To measure progress, there is now a [live scoreboard](http://128.174.241.211:443/relay_scoreboard) of all participants.

The [integration of “pluggable transports” in the main Tor Browser Bundle](https://bugs.torproject.org/9444) is moving smoothly. David Fifield published [beta images of his recent work](https://gitweb.torproject.org/user/dcf/tor-browser-bundle.git/shortlog/refs/heads/3.6-beta), and the initial implementation [adding a default set of bridges to Tor Launcher](https://bugs.torproject.org/10418) has been completed.

Following up on last week  [call for help](https://lists.torproject.org/pipermail/tor-dev/2014-January/006039.html) regarding [Tor Weather](https://weather.torproject.org/), Karsten Loesing is [organizing an IRC meeting](https://lists.torproject.org/pipermail/tor-dev/2014-January/006102.html) with interested developers on Wed, Jan 22, 18:00 UTC. The meeting will happen in #tor-dev on OFTC.

As part of the website redesign effort, Marck Al [proposed](https://lists.torproject.org/pipermail/www-team/2014-January/000196.html) an updated visual identity. Lunar also highlighted a [couple of tasks](https://lists.torproject.org/pipermail/www-team/2014-January/000216.html) that could be undertaken to move the website redesign forward.

Tails’ release [calendar](https://tails.boum.org/contribute/calendar/) has been shifted by two weeks because of the [holiday break from Mozilla](https://mailman.boum.org/pipermail/tails-dev/2014-January/004757.html).

Ximin Luo has been discussing with [I2P](http://geti2p.net/) developers on how [Pluggable Transports](https://www.torproject.org/docs/pluggable-transports.html) could be made [easier to use by other projects](https://bugs.torproject.org/10629).

Isis Lovecruft has sent late reports on her activity for [October](https://lists.torproject.org/pipermail/tor-reports/2014-January/000431.html), [November](https://lists.torproject.org/pipermail/tor-reports/2014-January/000432.html) and [December 2013](https://lists.torproject.org/pipermail/tor-reports/2014-January/000433.html).

There are two weeks left to participate in the crowdfunding campaign started by the [Freedom of the Press Foundation](https://pressfreedomfoundation.org/). Among other projects, the money will support core Tor development and Tails 1.0 release.

# Tor help desk roundup

Frequently users email the Tor help desk because they cannot access a particular public-facing website. Often this is because an increasing number of websites have begun blocking connections that appear to come from the Tor network. A partial list of websites that do this can be [found on Tor Project’s wiki](https://trac.torproject.org/projects/tor/wiki/org/doc/ListOfServicesBlockingTor). Feel free to add more sites to the list, and to contact the website’s operators to explain why banning Tor is not the best course of action.

Some users reported websites that do not allow logins when using the Tor Browser. This is not always related to website blocks or blacklists. There is a known bug in the Tor Browser Bundle such that Private Browsing Mode disallows cookies in a way that some sites don’t like. Disabling Private Browsing mode via Torbutton’s Preferences is a workaround and will hopefully be [fixed soon](https://bugs.torproject.org/10569).

* * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, Philipp Winter, Karsten Loesing, Sandeep, and dope457.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

