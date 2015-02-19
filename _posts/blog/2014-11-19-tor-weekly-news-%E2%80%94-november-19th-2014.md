---
layout: post
title: "Tor Weekly News — November 19th, 2014"
permalink: blog/tor-weekly-news-—-november-19th-2014
date: 2014-11-19 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the forty-sixth issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Tor Browser 4.5-alpha-1 is out
==============================

Mike Perry [announced](https://blog.torproject.org/blog/tor-browser-45-alpha-1-released) the first alpha release in the Tor Browser 4.5 series. This version goes some way to restoring one of the features most missed by users following the removal of the now-defunct Vidalia interface from Tor Browser — the ability to quickly visualize the Tor circuit that the current page is using. Clicking on the green Torbutton icon in the Tor Browser window now brings up a small diagram showing the IP addresses of all relays in a circuit, and the states in which they are located; this may help users evaluate the suitability of the circuits their Tor has selected, and also to quickly identify a malicious exit relay if they notice unusual behavior in downloaded pages and files.

Another key user-facing innovation in this release is the “security slider”. Users can now choose from four security settings in Torbutton’s “Preferences” window — “low (default)”, “medium-low”, “medium-high”, and “high” — that allow them to customize their Tor Browser based on their own security and usability needs, while still working to prevent “partitioning” attacks, which try to identify users based on their unusual browser configuration.

For other important additions in this series, please see the full changelog in Mike’s post. If you want to try out this alpha version, you can find it on the Tor Browser [project page](https://www.torproject.org/projects/torbrowser.html#downloads-alpha) or in the [distribution directory](https://www.torproject.org/dist/torbrowser/4.5-alpha-1/); please report any bugs you find!

Tor Browser on 32-bit Macs approaches end-of-life
=================================================

Now that Apple has discontinued support for the last remaining 32-bit Mac systems, Mike Perry [announced](https://blog.torproject.org/blog/end-life-plan-tor-browser-32-bit-macs) that the Tor Browser team will soon stop distributing 32-bit builds of its software. This week’s 4.5-alpha-1, like all future releases in the 4.5 series, is only available in a 64-bit build, and all support for 32-bit systems will end once 4.5 supersedes 4.0.

“32-bit Mac users likely have a month or two to decide what to do”, wrote Mike. “If your actual Mac hardware is 64-bit capable, you can upgrade to either the 64-bit edition of OSX 10.6 (which we will continue to support for a bit longer), or use the app store to upgrade to 10.9 or 10.10. If your hardware is not 64-bit capable and won’t run these newer Mac operating systems, you should still be able to use [Tails](https://tails.boum.org), which contains the Tor Browser.”

As a side effect of this transition, Tor Browser 4.0’s experimental in-browser secure updater will not handle the upgrade to the 64-bit build correctly for any Mac user; the old version must instead be replaced manually with the new one.

Miscellaneous news
==================

[Roger Dingledine](https://blog.torproject.org/blog/traffic-correlation-using-netflows) and [Sambuddho Chakravarty](https://blog.torproject.org/blog/traffic-correlation-using-netflows#comment-78918) responded on the Tor blog to inaccurate reports of a new attack against Tor, based on a recent study co-authored by Sambuddho. “It’s great to see more research on traffic correlation attacks, especially on attacks that don’t need to see the whole flow on each side. But it’s also important to realize that traffic correlation attacks are not a new area”, wrote Roger.

The Tails team set out the December [release schedule](https://mailman.boum.org/pipermail/tails-dev/2014-November/007422.html) for version 1.2.1 of the anonymous live operating system.

Giovanni Pellerano [announced](https://lists.torproject.org/pipermail/tor-talk/2014-November/035742.html) version 3.1.30 of Tor2web, which now supports web access to Tor hidden services over TLS. Access to the Facebook hidden service, the most high-profile instance of an HTTPS-enabled .onion site, is blocked in this version, as Tor2web offers no benefit in cases where there exists an identical service on the regular or “naked” web, and may actually present additional risk of compromise.

Griffin Boyce [requested feedback](https://lists.torproject.org/pipermail/tor-dev/2014-November/007798.html) on a “very rough” version of [Stormy](https://github.com/glamrock/Stormy), the simple hidden service setup wizard. “I’d love to get feedback on places where it breaks and where it could use a major structural change […] the current setup is entirely for development and should not be used as-is.”

Virgil Griffith [started a discussion](https://lists.torproject.org/pipermail/tor-talk/2014-November/035658.html) on the suitability of the name “hidden services” as opposed to other possible terms like “onion service” or “onion site”. Among the many responses, Roger Dingledine [suggested](https://lists.torproject.org/pipermail/tor-talk/2014-November/035660.html) that an alternative name like “onion service” “makes people have to learn what it is rather than guessing (and often guessing wrong)”, while Nathan Freitas [pointed out](https://lists.torproject.org/pipermail/tor-talk/2014-November/035662.html) that as “typical users don’t talk about web services, they talk about web sites or pages”, “onion site” might be a term worth adopting.

Tom Ritter [put forward](https://lists.torproject.org/pipermail/tor-dev/2014-November/007786.html) a number of improvements to the integration of HTTPS certificates and hidden services, following “a spirited debate on IRC”.

The Wikimedia Foundation is the latest high-profile organization to [set up a non-exit Tor relay](https://lists.torproject.org/pipermail/tor-talk/2014-November/035655.html). “It’s just a small contribution to the network. Really — anyone can do it.”

* * * * *

This issue of Tor Weekly News has been assembled by Harmony and Lunar.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the team [mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
