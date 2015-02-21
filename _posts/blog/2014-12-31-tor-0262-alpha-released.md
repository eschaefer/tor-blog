---
layout: post
title: "Tor 0.2.6.2-alpha is released"
permalink: tor-0262-alpha-released
date: 2014-12-31 13:28:53
author: nickm
category: blog
comments: open
tags: ["alpha", "tor-release"]
---

Tor 0.2.6.2-alpha is the second alpha release in the 0.2.6.x series. It introduces a major new backend for deciding when to send cells on channels, which should lead down the road to big performance increases. It contains security and statistics features for better work on hidden services, and numerous bugfixes.

This release contains many new unit tests, along with major performance improvements for running testing networks using Chutney. Thanks to a series of patches contributed by "teor", testing networks should now bootstrap in seconds, rather than minutes.

You can download the source from the usual place on the website. Packages should be up in a few days.

**NOTE:** This is an alpha release. Please expect bugs.

Changes in version 0.2.6.2-alpha - 2014-12-31
---------------------------------------------

-   Major features (relay, infrastructure):
    -   Complete revision of the code that relays use to decide which cell to send next. Formerly, we selected the best circuit to write on each channel, but we didn't select among channels in any sophisticated way. Now, we choose the best circuits globally from among those whose channels are ready to deliver traffic.

        This patch implements a new inter-cmux comparison API, a global high/low watermark mechanism and a global scheduler loop for transmission prioritization across all channels as well as among circuits on one channel. This schedule is currently tuned to (tolerantly) avoid making changes in network performance, but it should form the basis for major circuit performance increases in the future. Code by Andrea; tuning by Rob Jansen; implements ticket 9262.

-   Major features (hidden services):
    -   Make HS port scanning more difficult by immediately closing the circuit when a user attempts to connect to a nonexistent port. Closes ticket 13667.
    -   Add a HiddenServiceStatistics option that allows Tor relays to gather and publish statistics about the overall size and volume of hidden service usage. Specifically, when this option is turned on, an HSDir will publish an approximate number of hidden services that have published descriptors to it the past 24 hours. Also, if a relay has acted as a hidden service rendezvous point, it will publish the approximate amount of rendezvous cells it has relayed the past 24 hours. The statistics themselves are obfuscated so that the exact values cannot be derived. For more details see proposal 238, "Better hidden service stats from Tor relays". This feature is currently disabled by default. Implements feature 13192.

  [**read more »**](https://blog.torproject.org/blog/tor-0262-alpha-released)
