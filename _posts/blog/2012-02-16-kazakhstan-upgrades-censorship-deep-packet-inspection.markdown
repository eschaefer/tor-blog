---
layout: post
title: "Kazakhstan upgrades censorship to deep packet inspection"
permalink: blog/kazakhstan-upgrades-censorship-deep-packet-inspection
date: 2012-02-16
author: phobos
category: blog
tags: ["censorship circumvention", "deep packet inspection", "dpi", "internet censorship", "kazakhstan", "obfsproxy", "tor blocked"]
---

In December 2011 we were aware of Kazakhstan [increasing Internet censorship](http://www.hrw.org/news/2011/12/17/kazakhstan-investigate-violence-oil-rich-western-region) in response to some unrest and protests in Zhanaozen in the west. The censorship was then deployed around the country, in many cases with the [full support of the populace](http://www.washingtontimes.com/news/2011/dec/30/kazakhstan-social-networking-ban-censorship-debate/). The initial invesitgation showed simple IP address blocking coupled with basic dns censorship. Tor continued to work without incident until this week.

JSC KazTransCom, [AS35104](http://bgp.he.net/AS35104#_asinfo), has deployed or begun testing deep packet inspection (dpi) of all Internet traffic. They specifically target SSL-based protocols for blocking. This includes Tor, IPsec, and PPTP-based technologies, as well as some SSL-based VPNs. Business and private users of these technologies are equally affected.

An example of the censorship, as recorded by volunteers in country, can be found in this [network flow diagram](https://media.torproject.org/misc/2012-02-14-kazakhstan-dpi-blocking-of-tor.txt). Kazakhstan is identifying and blocking the SSL client key exchange during the setup of an SSL connection. [This graph](https://metrics.torproject.org/users.html?graph=direct-users&start=2011-11-18&end=2012-02-16&country=kz&events=on&dpi=72#direct-users) shows the effects of this deployment of censorship based on dpi.

Luckily, due to our [recent experience with Iran](https://blog.torproject.org/blog/obfsproxy-next-step-censorship-arms-race) we have an answer for people: [use obfsproxy](https://www.torproject.org/projects/obfsproxy.html.en). Obfsproxy continues to work in Kazakhstan, as well as Iran. In fact, it works in any country where dpi is used to censor citizens' access to the Internet.

Thank you to the volunteers for spending their Valentine's Day collecting and analyzing data.

