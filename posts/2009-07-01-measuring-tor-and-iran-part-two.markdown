---
layout: post
title: "Measuring Tor and Iran (Part two)"
permalink: measuring-tor-and-iran-part-two
date: 07/01/2009
author: karsten
category: blog
tags: ["bridges", "iran", "metrics"]
---

Two weeks ago we posted early measurements about the [growth of Tor usage in Iran](https://blog.torproject.org/blog/measuring-tor-and-iran). Since then we have improved our math, and used more data sources. This work is part of our [metrics project](https://blog.torproject.org/blog/performance-measurements-and-blockingresistance-analysis-tor-network), where we're learning about the Tor network to improve its availability and performance while keeping our users safe.

The first graph shows the estimated number of new and returning Tor clients per day coming from China and Iran. So for example, there were around 7800 new and returning Iranian Tor users on June 24. By "returning", we mean Tor clients that were off for at least several days, so they didn't have cached directory information. We added China as a comparison for the Iran numbers: you can see the results of the recent [Green Dam fiasco and attempts to block Google services](http://rconversation.blogs.com/rconversation/2009/06/chinas-censorship-blowback.html). Many more details and math are [here](https://git.torproject.org/checkout/metrics/master/report/dirreq/directory-requests-2009-06-26.pdf).

<center><img height="350" width="500" src="https://blog.torproject.org/files/new-returning-users-2009-06-30.png"></center>

The second graph shows the growth in bridge users coming from Iran and China. [Bridges](https://www.torproject.org/bridges) are like normal relays except that they are not listed in a public directory and therefore they're harder to block. We show "growth compared to June 1" because we don't yet have a good estimate of the absolute number of bridge users. The number is probably an order of magnitude smaller than the number of "regular" Tor users. But still, we can say that bridge usage from Iran has boosted to 950% as compared to June 1. For more information on these numbers see [this report](https://git.torproject.org/checkout/metrics/master/report/bridges/bridges-2009-06-22.pdf).

<center><img height="350" width="500" src="https://blog.torproject.org/files/bridge-usage-2009-06-30.png"></center>

While it is great to see that so many people in Iran find the Tor network useful, we should continue our attempts to make Tor even better. Your contribution could be to [set up a bridge or relay](https://www.torproject.org/docs/tor-doc-relay) as [many others recently did](https://blog.torproject.org/blog/recent-growth-tor-network). You might also consider setting up an exit relay, possibly with the help of [these instructions](https://blog.torproject.org/blog/tips-running-exit-node-minimal-harassment). But middle nodes and bridges are helping as well!

<thead><tr>
<th>Attachment</th>
<th>Size</th> </tr></thead>
<tbody>
<tr class="odd">
<td><a href="https://blog.torproject.org/files/new-returning-users-2009-06-30.png">new-returning-users-2009-06-30.png</a></td>
<td>22 KB</td> </tr>
<tr class="even">
<td><a href="https://blog.torproject.org/files/bridge-usage-2009-06-30.png">bridge-usage-2009-06-30.png</a></td>
<td>21.44 KB</td> </tr>
</tbody>

