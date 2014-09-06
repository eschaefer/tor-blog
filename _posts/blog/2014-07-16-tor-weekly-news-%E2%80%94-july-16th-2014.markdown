---
layout: post
title: "Tor Weekly News — July 16th, 2014"
permalink: blog/tor-weekly-news-%E2%80%94-july-16th-2014
date: 2014-07-16
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the twenty-eighth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Roundup of research on incentives for running Tor relays

As an hors-d’œuvre to the now [on-going the Privacy Enhancing Technology Symposium](https://petsymposium.org/2014/), Rob Jansen wrote [a long blog post covering the last five years of research on incentives for running Tor relays](https://blog.torproject.org/blog/tor-incentives-research-roundup-goldstar-par-braids-lira-tears-and-torcoin).

Rob introduces the topic by describing the current “volunteer resource model” and mentions that “has succeeded so far: Tor now consists of over 5000 relays transferring between 4 and 5 GiB/s in aggregate”. Rob lists several possible reasons why volunteers run relays right now. They are all intrinsic motivations: current operators run relays because they really want to.

Is only relying on volunteers going to limit the growth of the Tor network in the future? There are already [not-for-profit organizations](https://www.torservers.net/) operating relays based on donations, but growing them too much would also be problematic. Another area being explored are extrinsic motivations: making Tor clients faster when someone runs a relay or giving a financial reward — in a currency or another — for the service. Some can legitimately ask if they are [suitable for Tor at all](http://p2pfoundation.net/Intrinsic_vs._Extrinsic_Motivation#Why_Extrinsic_Motivation_Doesn.27t_Work) and Rob raises plenty of legitimate concerns on how they would interact with the current set of volunteers.

The problem keeps interesting researchers, and Rob details no less than six schemes: the oldest are [PAR](http://cs.gmu.edu/~astavrou/research/Par_PET_2008.pdf) and [Gold Star](http://freehaven.net/anonbib/papers/incentives-fc10.pdf) which introduced anonymity problems, [BRAIDS](http://www.robgjansen.com/publications/braids-ccs2010.pdf) where double spending of rewards is prevented without leaking timing information, [LIRA](http://www.robgjansen.com/publications/lira-ndss2013.pdf) which focused on scalability, [TEARS](http://www.robgjansen.com/publications/tears-hotpets2014.pdf) where a publicly auditable e-cash protocol reduce the reliance on trusted parties, and finally, the ( [not ideally named](https://www.torproject.org/docs/trademark-faq#researchpapers))  [TorCoin](http://www.robgjansen.com/publications/torpath-hotpets2014.pdf) which introduces the idea of a crypto-currency based on “proof-of-bandwidth”.

Rob details the novel ideas and drawbacks of each schemes, so be sure to read the original blog post for more details. After this roundup, Rob highlights that “recent research has made great improvements in the area of Tor incentives”. But that’s for the technical side as “it is unclear how to make headway on the social issues”.

“Tor has some choices to make in terms of how to grow the network and how to position the community during that growth process” concludes Rob. So let’s have that conversation.

# Defending against guard discovery attacks with layered rotation time

Guard nodes are a key component of a Tor client’s anonymity. Once an attacker gains knowledge of which guard node is being used by a particular client, putting the guard node under monitoring is likely the last step before finding a client’s IP address.

George Kadianakis has restarted the [discussion](https://lists.torproject.org/pipermail/tor-dev/2014-July/007122.html) on how to [slow down guard discovery of hidden services](https://bugs.torproject.org/9001) by exploring the idea of “keeping our middle nodes more static”. The idea is to slow down the attacks based on repeated circuit destruction by reusing the same “middle nodes for 3-4 days instead of choosing new ones for every circuit”. Introducing this new behavior will slow down the attack, but George asks “are there any serious negative implications?”

The idea is not new, as Paul Syverson [pointed out](https://lists.torproject.org/pipermail/tor-dev/2014-July/007125.html): “Lasse and I suggested and explored the idea of layered guards when we introduced guards”. He adds “there are lots of possibilities here”.

George worries that middle nodes would then “always see your traffic coming through your guard (assuming a single guard per client)”. Ian Goldberg [added](https://lists.torproject.org/pipermail/tor-dev/2014-July/007123.html) “the exit will now know that circuits coming from the same middle are more likely to be the same client”. Restricting the change to only hidden services and not every client means that it will be “easy for an entry guard to learn whether a client has static middle nodes or not”.

As George puts it the [latest message in the thread](https://lists.torproject.org/pipermail/tor-dev/2014-July/007126.html): “As always, more research is needed…” Please help!

# More monthly status reports for June 2014

The wave of regular monthly reports from Tor project members for the month of June continued, with submissions from [Michael Schloh von Bennewitz](https://lists.torproject.org/pipermail/tor-reports/2014-July/000587.html) and [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2014-July/000588.html).

Arturo Filastò reported on behalf of [the OONI team](https://lists.torproject.org/pipermail/tor-reports/2014-July/000586.html), while Roger Dingledine submitted the [SponsorF report](https://lists.torproject.org/pipermail/tor-reports/2014-July/000589.html)

# Miscellaneous news

The various roadmaps that came out of the [2014 summer dev. meeting](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014SummerDevMeeting) have been [transcribed](https://trac.torproject.org/projects/tor/wiki/org/meetings/2014SummerDevMeeting/Roadmaps) in a joint effort by George Kadianakis, Yawning Angel, Karsten Loesing, and an anonymous person. Most items will probably be matched with a ticket soon.

The Tor Project is hiring a [financial controller](https://www.torproject.org/about/jobs-controller.html). This is a part time position, approximately 20 hours per week, at the office in Cambridge, Massachusetts.

The Tails developers announced the creation of two new mailing lists. “ [If you are a designer, UX/UI expert or beginner](https://mailman.boum.org/pipermail/tails-dev/2014-July/006330.html)” interested in the theory and practice of designing user interfaces for Tails, the [tails-ux list](https://mailman.boum.org/listinfo/tails-ux) is for you, while the [tails-project list](https://mailman.boum.org/listinfo/tails-project) is dedicated to “ [the ‘life’ of the project](https://mailman.boum.org/pipermail/tails-dev/2014-July/006329.html)“; however, “technical questions should stay on tails-dev”.

Alan kicked of the aforementioned tails-ux mailing list [announcing progress](https://mailman.boum.org/pipermail/tails-ux/2014-July/000000.html) on Tails initial login screen. The new set of mockups is visible on the corresponding [blueprint](https://tails.boum.org/blueprint/tails-greeter:_revamp_UI/).

More mockups! Nima Fatemi [produced](https://lists.torproject.org/pipermail/tor-dev/2014-July/007115.html) some for a possible browser-based Tor control panel, incorporating features that were lost with the removal of Vidalia from the Tor Browser, such as the world map with Tor circuit visualizations. “How would you perfect [that image](https://people.torproject.org/~nima/ux/about-tor.png)? What’s missing?”, asked Nima, hoping “to inspire people to start hacking on it”.

Meanwhile, Sean Robinson [had been working](https://lists.torproject.org/pipermail/tor-dev/2014-July/007136.html) on a new graphical Tor controller called [Syboa](https://gitorious.org/syboa/syboa). Sean’s “primary motivation for Syboa was to replace TorK, so [it looks](https://gitorious.org/syboa/syboa/source/7082a82:docs/screenshot-basic.png) more like TorK than Vidalia”. Sean announces that he will not have time for further development soon but that he would answer questions.

Juha Nurmi [submitted](https://lists.torproject.org/pipermail/tor-reports/2014-July/000590.html) the weekly status report for the ahmia.fi GSoC project.

Thanks to the [University of Edinburgh’s School of Informatics](https://lists.torproject.org/pipermail/tor-mirrors/2014-July/000623.html), [funcube.fr](https://lists.torproject.org/pipermail/tor-mirrors/2014-July/000624.html), [Stefano Fenoglio](https://lists.torproject.org/pipermail/tor-mirrors/2014-July/000627.html), [IP-Connect](https://lists.torproject.org/pipermail/tor-mirrors/2014-July/000632.html), [Justin Ramos](https://lists.torproject.org/pipermail/tor-mirrors/2014-July/000633.html), [Jacob Henner from Anatomical Networks](https://lists.torproject.org/pipermail/tor-mirrors/2014-July/000634.html), and [Hackabit.nl](https://lists.torproject.org/pipermail/tor-mirrors/2014-July/000638.html) for running mirrors of the Tor Project website!

# Tor help desk roundup

Users often ask about for assistance setting up Tor Cloud instances. Sina Rabbani is taking over the maintenance of Tor Cloud and is working on updating the packages and documentation. Until new documentation on using the up-to-date images and Amazon Web Services interface lands, users not already familiar with AWS may want to use a different virtual server provider to host their bridges.

# Easy development tasks to get involved with

The setup scripts of the Flashproxy and Obfsproxy pluggable transports attempt to download and build the M2Crypto library if they are not already installed. We´d really want to avoid this and have the setup script fail if not all libraries are present for building Flashproxy. The ticket that describes this bug also outlines [a possible workaround that disables all downloads during the setup process](https://bugs.torproject.org/10847#comment:4). If you know a bit about setuptools and want to turn this description into a patch and test it, please give it a try.

* * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, Karsten Loesing, and George Kadianakis.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

