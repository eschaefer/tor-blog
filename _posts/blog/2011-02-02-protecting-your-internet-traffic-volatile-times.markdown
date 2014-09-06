---
layout: post
title: "Protecting your Internet traffic in volatile times"
permalink: blog/protecting-your-internet-traffic-volatile-times
date: 2011-02-02
author: phobos
category: blog
tags: ["egypt", "low bandwidth clients", "tor camouflage", "tor on satellite", "volatile internet"]
---

We're glad that the Internet Service Providers in Egypt are announcing their routes to the world and have [rejoined the Internet](http://www.renesys.com/blog/2011/02/egypt-returns-to-the-internet.shtml). We are concerned because it is possible that traffic crossing the Egyptian border is being recorded and possibly saved for future use. [Correctly using Tor](https://www.torproject.org/download/download#warning) to and from Egyptian destinations will keep your traffic anonymous.

Tor separates who you are from where you are going on the Internet. It's up to you, the user, to choose where you share your personal information. Currently, we do not try very hard to hide that you are using Tor. In the past few years, we haven't needed to hide. Tor looks like an SSL connection on the wire. Your local ISP, if they are very clever, could map your current connections from your assigned IP address to the list of public Tor relays. This would only tell them you are using Tor, not where you are going on the Internet. We do offer [bridge relays](https://www.torproject.org/docs/bridges.html.en), which are semi-public relays published in a few selective ways. By using bridges, your ISP is unlikely to figure out you are using Tor. We need thousands more bridges, please [join the Tor network](https://www.torproject.org/docs/tor-doc-relay) to help others.

Many years ago, we theorized this arms race could happen. Recent events have turned theory into reality. We are working on improvements to make it much more difficult to detect Tor usage. These methods include [normalization of our TLS usage](https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/176-revising-handshake.txt) and [tunneling](https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/ideas/xxx-pluggable-transport.txt) Tor through other protocols, such as XMPP, HTTPS, and HTTP.

Thanks to some [funding from Avaaz](https://secure.avaaz.org/en/egypt_blackout/), we've also begun experimenting with ways to make Tor perform better on satellite and mesh networks. We have Tor working well on [mobile phone 3G and 4G connections](https://guardianproject.info/apps/orbot/). Tor over [VSAT](https://secure.wikimedia.org/wikipedia/en/wiki/Very_small_aperture_terminal) and [BGAN](https://secure.wikimedia.org/wikipedia/en/wiki/Broadband_Global_Area_Network) connections does work, however it needs more research into how to better handle the variable latencies and varying available bandwidth on such connections. The improvements that result from this research will benefit those with little to no Internet access, whether due to political unrest, natural disasters, or remote locations, who nonetheless seek to keep their online activities safe.

