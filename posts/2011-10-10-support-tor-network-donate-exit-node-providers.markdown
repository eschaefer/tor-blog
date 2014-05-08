---
layout: post
title: "Support the Tor Network: Donate to Exit Node Providers"
permalink: support-tor-network-donate-exit-node-providers
date: 10/10/2011
author: mikeperry
category: blog
tags: ["anonymity advocacy", "distributed trust", "exits", "performance", "relays"]
---

The Tor network is run by volunteers, and for the most part is entirely independent of the software development effort led by The Tor Project, Inc. While The Tor Project, Inc is a 501(c)3 non-profit that is [happy to take donations](https://www.torproject.org/donate/donate.html.en) to create more and better software, up until recently there was no way for you to fund deployment of more relays to improve network capacity and performance, aside from running those relays yourself.

We're happy to announce that both [Noisebridge](https://www.noisebridge.net/wiki/Tor) and [TorServers.net](https://www.torservers.net) are now able to take donations directly for the purpose of running high capacity Tor exit nodes.

Noisebridge is a US 501(c)3 non-profit, which means that for US citizens, [donations](http://tor.noisebridge.net/) are tax deductible. Torservers.net is a German non-profit organization whose [donations](https://www.torservers.net/donate.html) are tax deductible for German citizens (and [also potentially](http://eur-lex.europa.eu/LexUriServ/LexUriServ.do?uri=CELEX:62007J0318:EN:HTML) for citizens of other EU member states).

What are the pluses and minuses of donating as opposed to running your own relay? Glad you asked!

While it is relatively easy and risk-free to run a middle relay or a bridge, running an exit can be tough. You have to seek out a [friendly ISP](https://trac.torproject.org/projects/tor/wiki/doc/TheOnionRouter/GoodBadISPs), explain Tor to them, and then navigate a [laundry list of Internet bureaucracies](https://blog.torproject.org/blog/tips-running-exit-node-minimal-harassment) to ensure that when abuse happens, the burden of [answering complaints](https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/TorAbuseTemplates) falls upon you and not your ISP.

These barriers are all made easier the larger your budget is. On top of this, like most things, bandwidth is cheaper in bulk. But not just [Costco cheaper](http://www.costco.com/Browse/Product.aspx?prodid=11487214): exponential-growth cheaper, all the way up into the gigabit range (and perhaps beyond, but no one has run a Tor node on anything faster).

At these scales, large exit nodes can pay as little as $1/mo per dedicated megabit/second. Sometimes less. This means that [adding $30/mo](https://www.paypal.com/subscriptions/business=treasurer%40noisebridge.net&item_name=Noisebridge%20Tor%20Node%20Project&cy_code=USD&no_note=1&no_shipping=1&a3=30&p3=1&t3=M&src=1) to the hosting budget of a large exit node can buy almost 40 times more full-duplex dedicated bandwidth than a similarly priced business upgrade to your home ADSL line would buy, and about 50 times more bandwidth than Amazon EC2 instances at the entry-level price of $0.08 per half-duplex gigabyte, not counting CPU costs. ( [Bridge](https://www.torproject.org/docs/bridges) economics in terms of IP address space availability might still favor Amazon EC2, but that is a different discussion).

The downside to donation is that network centralization can lead to a more fragile and a more observable network. If these nodes fail, the network will definitely feel the [performance](https://metrics.torproject.org/performance.html) [loss](https://lists.torproject.org/pipermail/tor-talk/2011-September/021493.html). In terms of observability, fewer nodes also means that fewer points of surveillance are required to deanonymize users (though [some argue](http://archives.seul.org/or/dev/Sep-2008/msg00016.html) that more users will make such surveillance less reliable, no one has yet rigorously quantified that result against actual attacks).

Therefore, if you are able to run a high capacity relay or exit yourself (or have access to cheap/free/ [unused](https://gitweb.torproject.org/tor.git/blob/master:/contrib/linux-tor-prio.sh) bandwidth at your work/school), running your own relay is definitely preferred. If you are part of the Tor community and want to accept donations, we'd love to add you to our [recommended donor list](https://www.torproject.org/docs/faq#RelayDonations). Please join us on the [tor-relays mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-relays) to discuss [node configuration](https://github.com/noisetor/) and [setup](https://www.torservers.net/wiki/guides).

However, if configuring and maintaining a high capacity relay is not for you, donating a portion of the monthly hosting budgets of either of these organizations is an excellent way to support anonymity, privacy, and censorship circumvention for very large numbers of people.

