---
layout: post
title: "10 years of collecting Tor directory data"
permalink: 10-years-collecting-tor-directory-data
date: 2014-05-15 02:30:57
author: karsten
category: blog
status: closed
tags: ["directory authority archives", "metrics"]
---

Today is the 10th anniversary of collecting Tor directory data!

As the [2004 Tor design paper](https://svn.torproject.org/svn/projects/design-paper/tor-design.pdf) says, "As of mid-May 2004, the Tor network consists of 32 nodes (24 in the US, 8 in Europe), and more are joining each week as the code matures."

In fact, we still have the original relay lists from back then. The [first archived Tor directory](https://people.torproject.org/~karsten/directory-2004-05-15-07-31-04) dates back to May 15, 2004. It starts with the following lines which are almost human-readable:

     signed-directory published 2004-05-15 07:30:57 recommended-software 0.0.6.1,0.0.7pre1-cvs running-routers moria1 moria2 tor26 incognito jap dizum   cassandra metacolo poblano ned TheoryOrg Tonga   peertech hopey tequila triphop moria4 anize rot52   randomtrash 

  
As of today, May 15, 2014, there are about 4,600 relays in the Tor network and another 3,300 bridges. In these 10 years, we have collected a total of 212 GiB of bz2-compressed tarballs containing Tor directory data. That's more than 600 GiB of uncompressed data. And of course, the full archive is publicly [available for download](https://metrics.torproject.org/data.html).

![](https://people.torproject.org/~karsten/tor-directory-data.png)

Here's a small selection of what people do with this fine archive:

-   The metrics portal shows graphs of [network growth over time](https://metrics.torproject.org/network.html) and [estimates of users derived from directory activity](https://metrics.torproject.org/users.html).
-   The [ExoneraTor service](https://exonerator.torproject.org/) allows people to look up whether a given IP address was part of the Tor network in the past.
-   The websites [Atlas](https://atlas.torproject.org/), [Globe](https://globe.torproject.org/), and [Compass](https://compass.torproject.org/) let users explore how specific relays or bridges contribute to the Tor network.
-   The [Shadow Simulator](https://shadow.github.io/) uses archived Tor directory data to generate network topologies that match the real Tor network as close as possible.
-   The [Tor Path Simulator](https://torps.github.io/) uses Tor directory archive data to simulate the effect of changes to Tor's path selection algorithm.

If people want to use the Tor directory archive for their [research](https://research.torproject.org/) or for building new applications, or want to help out with the projects listed above, don't hesitate to contact us!

Happy 10th birthday, Tor directory archive!
