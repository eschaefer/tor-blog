---
layout: post
title: "Tor Weekly News — January 7th, 2015"
permalink: tor-weekly-news--january-7th-2015
date: 2015-01-07 07:00:00
author: harmony
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the first issue in 2015 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Tor 0.2.6.2-alpha is out
========================

Nick Mathewson [announced](https://blog.torproject.org/blog/tor-0262-alpha-released) the second alpha release in the Tor 0.2.6.x series. As well as including the [cell scheduling changes](https://bugs.torproject.org/9262) and [hidden service statistics collection](https://bugs.torproject.org/13192) reported in recent issues of TWN, this release makes it harder to portscan hidden services by closing circuits if a client tries to connect to a non-existent port. It also contains numerous bugfixes and new unit tests; please see Nick’s announcement for the full changelog. The source code is available as usual from the [distribution directory](https://dist.torproject.org/).

Tor at 31c3
===========

The 31st edition of the [Chaos Communication Congress](https://events.ccc.de/congress/2014/wiki/Main_Page), an annual highlight in the free software and security calendar, took place in Hamburg, and as usual Tor featured in several key talks over the course of the long weekend.

Roger Dingledine and Jacob Appelbaum’s appropriately grand-sounding [“State of the Onion” address](http://media.ccc.de/browse/congress/2014/31c3_-_6251_-_en_-_saal_1_-_201412301400_-_state_of_the_onion_-_jacob_-_arma.html), a round-up of the year’s events in the Tor community, took place once again, with guest contributions from journalist and filmmaker Laura Poitras and OONI developer Arturo Filastò. Topics included the relationship between censorship and surveillance, the misinterpretation of academic research by journalists, new pluggable transports, and much more.

Laura Poitras also joined Julia Angwin, Jack Gillum, and Nadia Heninger for [“Crypto Tales from the Trenches”](http://media.ccc.de/browse/congress/2014/31c3_-_6154_-_en_-_saal_1_-_201412272300_-_crypto_tales_from_the_trenches_-_nadia_heninger_-_julia_angwin_-_laura_poitras_-_jack_gillum.html), in which the journalists described their experiences with security software when doing research and communicating with sources. “I don’t think any of us could do our work without Tor”, said Laura, while Julia described the Tails operating system as “her favorite success story” in this field.

Tor Browser developer Mike Perry joined Seth Schoen to [discuss](http://media.ccc.de/browse/congress/2014/31c3_-_6240_-_en_-_saal_g_-_201412271400_-_reproducible_builds_-_mike_perry_-_seth_schoen_-_hans_steiner.html) the concept of deterministic builds, the implementation of which has been one of the Tor Project’s major successes over the past year. Mike and Seth demonstrated some of the attacks that this system aims to defend against, as well as the work that Tor, F-Droid, and Debian have all been doing to make their processes compatible with the deterministic build process.

Finally, Dr. Gareth Owen of Portsmouth University [presented](http://media.ccc.de/browse/congress/2014/31c3_-_6112_-_en_-_saal_2_-_201412301715_-_tor_hidden_services_and_deanonymisation_-_dr_gareth_owen.html) the results of research into the content and usage of Tor hidden services. The research involved setting up a number of Tor relays, waiting until they gained the “HSDir” flag, then counting the number of times a particular service’s descriptor was requested, as well as manually categorizing the services whose descriptors were learned. Dr. Owen found that while the largest category of onion services by number could be characterized as “drugs”, the majority of the descriptor requests he saw were for services in his “abuse” category. The talk itself discusses some possible limitations of the data gathered, and Tor developers have responded on the Tor blog with [further](https://blog.torproject.org/blog/tor-80-percent-percent-1-2-percent-abusive) [analysis](https://blog.torproject.org/blog/some-thoughts-hidden-services).

Monthly status reports for December 2014
========================================

The wave of regular monthly reports from Tor project members for the month of December has begun. [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2014-December/000727.html) released his report first, followed by reports from [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-December/000728.html), [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2014-December/000729.html), [Juha Nurmi](https://lists.torproject.org/pipermail/tor-reports/2014-December/000730.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-December/000731.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-December/000732.html), [Sukhbir Singh](https://lists.torproject.org/pipermail/tor-reports/2015-January/000733.html), [Leiah Jansen](https://lists.torproject.org/pipermail/tor-reports/2015-January/000734.html), [David Goulet](https://lists.torproject.org/pipermail/tor-reports/2015-January/000735.html), [Michael Schloh von Bennewitz](https://lists.torproject.org/pipermail/tor-reports/2015-January/000736.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2015-January/000738.html), [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2015-January/000740.html), [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2015-January/000742.html), and [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2015-January/000743.html).

Colin C. also sent out the [help desk report](https://lists.torproject.org/pipermail/tor-reports/2015-January/000737.html), while Arturo Filastò reported on behalf of the [OONI team](https://lists.torproject.org/pipermail/tor-reports/2015-January/000739.html) and Mike Perry for the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2015-January/000741.html).

Miscellaneous news
==================

Nick Mathewson and Andrea Shepard drafted a [proposal](https://lists.torproject.org/pipermail/tor-dev/2015-January/008087.html) for including a hash chain in the [consensus](https://metrics.torproject.org/about.html#consensus) produced by Tor [directory authorities](https://metrics.torproject.org/about.html#directory-authority), in order to prevent certain kinds of attack on the directory authorities and their keys.

Nick also [clarified](https://lists.torproject.org/pipermail/tor-talk/2015-January/036379.html) that a recently-discovered Libevent vulnerability has no effect on Tor.

In connection with the current push to collect statistics relating to Tor hidden services in a privacy-preserving manner, Aaron Johnson [noted](https://lists.torproject.org/pipermail/tor-dev/2015-January/008086.html) that there are two further desirable sets of statistics which might pose a risk to anonymity if gathered incorrectly, and discussed possible solutions to the problem.

David Fifield published a [summary](https://lists.torproject.org/pipermail/tor-dev/2015-January/008082.html) of costs incurred by the meek pluggable transport for the month of December 2014.

David also continued his experiments on historical Tor metrics data with [visualizations of a recent Sybil attack](https://lists.torproject.org/pipermail/tor-dev/2015-January/008095.html), and [wondered](https://lists.torproject.org/pipermail/tor-talk/2015-January/036346.html) what might have been responsible for a sudden change in the way that users in Kazakhstan were choosing to connect to the Tor network in October 2014.

Sebastian Urbach [noted](https://lists.torproject.org/pipermail/tor-relays/2015-January/006051.html) a sudden drop in the number of Tor relays acting as hidden service directories, and wondered about the cause. As SiNA Rabbani [clarified](https://lists.torproject.org/pipermail/tor-relays/2015-January/006063.html), the amount of time a relay needs to have been running before it earns the “HSDir” flag was increased by directory authorities, in response to a recent Sybil attack.

The developers of ChatSecure for iOS [announced](https://chatsecure.org/blog/chatsecure-ios-v3-released/) that their recent 3.0 release includes experimental support for connections to XMPP chat servers over Tor, and briefly described how they added the new feature.

* * * * *

This issue of Tor Weekly News has been assembled by Harmony, David Fifield, Catfish, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
