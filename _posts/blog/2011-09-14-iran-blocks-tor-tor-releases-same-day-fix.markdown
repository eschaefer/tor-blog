---
layout: post
title: "Iran blocks Tor; Tor releases same-day fix"
permalink: blog/iran-blocks-tor-tor-releases-same-day-fix
date: 2011-09-14
author: arma
category: blog
tags: ["internet censorship", "iran"]
---

 **The short version: Tor relays and bridges should upgrade to Tor 0.2.2.33 or Tor 0.2.3.4-alpha so users in Iran can reach them again.**

Yesterday morning (in our timezones — that evening, in Iran), Iran added a filter rule to their border routers that recognized Tor traffic and blocked it. Thanks to help from a variety of friends around the world, we quickly discovered how they were blocking it and released a [new version of Tor](http://archives.seul.org/tor/talk/Sep-2011/msg00187.html) that isn't blocked. Fortunately, the fix is on the relay side: that means once enough [relays](https://torproject.org/docs/tor-doc-relay) and [bridges](https://www.torproject.org/docs/bridges) upgrade, the [many tens of thousands of Tor users in Iran](https://metrics.torproject.org/users.html?graph=direct-users&start=2011-06-16&end=2011-09-14&country=ir&dpi=72#direct-users) will resume being able to reach the Tor network, without needing to change their software.

How did the filter work technically? Tor tries to make its traffic look like a web browser talking to an https web server, but if you look carefully enough you can tell some differences. In this case, the characteristic of Tor's SSL handshake they looked at was the expiry time for our SSL session certificates: we rotate the session certificates every two hours, whereas normal SSL certificates you get from a [certificate](https://blog.torproject.org/blog/detecting-certificate-authority-compromises-and-web-browser-collusion) [authority](https://blog.torproject.org/blog/diginotar-debacle-and-what-you-should-do-about-it) typically last a year or more. The fix was to simply write a larger expiration time on the certificates, so our certs have [more plausible](https://www.eff.org/observatory) expiry times.

There are plenty of interesting discussion points from the research angle around how this arms race should be played. We're working on [medium](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/176-revising-handshake.txt) [term](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/179-TLS-cert-and-parameter-normalization.txt) and [longer term](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/180-pluggable-transport.txt) solutions, but in the short term, there are other ways to filter Tor traffic like the one Iran used. Should we fix them all preemptively, meaning the next time they block us it will be through some more complex mechanism that's harder to figure out? Or should we leave things as they are, knowing there will be more blocking events but also knowing that we can solve them easily? Given that their last blocking attempt was in [January 2011](https://blog.torproject.org/blog/update-internet-censorship-iran), I think it's smartest to collect some more data points first.

It's too early to have cool graphs showing a drop in users and then the users coming back a day or so later. I'll plan to add these graphs once things play out more. [Update: [here is the graph as of Sept 16](https://metrics.torproject.org/users.html?graph=direct-users&start=2011-07-01&end=2011-09-18&country=ir&events=on&dpi=72#direct-users)]

