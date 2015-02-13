---
layout: post
title: "Looking for front-end web developers for network status websites Atlas and Globe"
permalink: looking-front-end-web-developers-network-status-websites-atlas-and-globe
date: 2014-07-17 12:13:15
author: karsten
category: blog
status: closed
tags: ["Atlas", "Globe", "network status", "Onionoo", "web development"]
---

Hello front-end web developers!

We are looking for somebody to fork and extend one of the two main Tor network status websites [Atlas](https://atlas.torproject.org/) or [Globe](https://globe.torproject.org/).

Here's some background: both the Atlas and the Globe website use the [Onionoo service](https://onionoo.torproject.org/) as their data back-end and make that data accessible to mere humans. The Onionoo service is maintained by Karsten. Atlas was written by Arturo as proof-of-concept for the Onionoo service and later maintained (but not extended) by Philipp. Globe was forked from Atlas by Christian who improved and maintained it for half a year, but who unfortunately disappeared a couple of weeks ago. That leaves us with no actively maintained network status website, which is bad.

Want to help out?

Here's how: Globe has been criticized for having too much whitespace, which makes it less useful on smaller screens. But we hear that the web technology behind Globe is superior to the one behind Atlas (we're no front-end web experts, so we can't say for sure). A fine next step could be to fork Globe and tidy up its design to work better on smaller screens. And there are plenty of steps after that if you look through the tickets in the Globe and Atlas component of our [bug tracker](https://trac.torproject.org/). Be sure to present your fork on the [tor-dev@ mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-dev) early to get feedback. You can just run it on your own server for now.

The long-term goal would be to have one or more people working on a new network status website to replace Atlas and Globe. We'd like to wait with that step until such a new website is maintained for a couple of weeks or even months though. And even then, we may keep Atlas and Globe running for a couple more months. But eventually, we'd like to shut them down in favor of an actively maintained website.

Let us know if you're interested, and we're happy to provide more details and discuss ideas with you.
