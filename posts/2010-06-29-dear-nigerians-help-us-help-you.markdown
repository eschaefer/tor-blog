---
layout: post
title: "Dear Nigerians, help us help you."
permalink: dear-nigerians-help-us-help-you
date: 06/29/2010
author: phobos
category: blog
tags: ["data gathering", "herdict", "nigeria", "support", "tor blocked", "websites blocked"]
---

You've flooded the blog and tor-assistants with lots of cries for help about Tor, Freegate, Ultrasurf, and a slew of VPNs all being blocked. Sometimes this is through MTN Nigera, sometimes not.

[http://www.herdict.org/web/explore/country/NG](http://www.herdict.org/web/explore/country/NG "http://www.herdict.org/web/explore/country/NG") suggests access is a 50/50 chance for some sites.

[https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/TorFAQ#Iins...](https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/TorFAQ#IinstalledTorandPolipobutitsnotworking "https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/TorFAQ#IinstalledTorandPolipobutitsnotworking"). That FAQ entry is a fine place to start. Telling us Tor doesn't work lets us know there is a problem. Sending in logs from Message Log would be a great start. We need to know what Tor records while trying to connect to the Tor Network.

Someone could further startup Wireshark and record the entire session of Tor starting up and ultimately failing to connect to the Tor Network.

There are lots of ways ISPs in Nigeria can block Tor and your favorite websites. DNS filtering, IP blacklisting, proxy server keyword filtering, govt mandated blackbox firewalls/proxy servers, or just simply blocking the published tor relays list. The worst case is Nigeria white lists the Internet, allowing you to only visit approved sites (and probably man-in-the-middled as well).

All we know right now is that some ISPs in Nigeria seem to be blocking many websites, tools, and Tor. More data is needed to figure out some solutions.

Updates 2010-07-01: Two people have given us some data from [MTN](https://trac.torproject.org/projects/tor/ticket/1645) and [Etisalat](https://trac.torproject.org/projects/tor/ticket/1625) ISPs. It seems these two ISPs have implemented some general "circumvention tool" blocking.

