---
layout: post
title: "OONI Bridge reachability study and hackfest"
permalink: blog/ooni-bridge-reachability-study-and-hackfest
date: 2014-11-10 06:05:33
author: art
category: blog
comments: closed
tags: ["bridges", "censorship", "circumvention", "events", "ooni", "pluggable transports"]
---

Has a [Tor bridge](https://www.torproject.org/docs/bridges) already been blocked in a given country? Being able to answer that question would allow Tor to provide more efficient circumvention methods to those who need them. OONI, the Open Observatory of Network Interference is now actively collecting data on [bridge reachability](https://lists.torproject.org/pipermail/ooni-dev/2014-October/000184.html). We are also interested in having a better understanding of how reactive censors are in blocking new bridges distributed via [Tor Browser](https://www.torproject.org/projects/torbrowser.html.en) and how effective they are at inhibiting usage of particular [pluggable transport](https://www.torproject.org/docs/pluggable-transports.html.en).

The countries we are focusing on in this survey are China, Iran, Russia and Ukraine. We call these our test vantage points.

From every test vantage point we perform two types of measurements:

-   A [Bridge reachability measurement](https://gitweb.torproject.org/ooni/spec.git/blob/HEAD:/test-specs/ts-011-bridge-reachability.md) that attempts to build a Tor circuit using the bridge in question.
-   A [TCP connect measurement](https://gitweb.torproject.org/ooni/spec.git/blob/HEAD:/test-specs/ts-008-tcpconnect.md) that simply does a TCP connect to the bridge IP and port.

To establish a baseline to eliminate the cases in which the bridge is marked as blocked, while it is in fact just offline, we measure also from a vantage point located in the Netherlands.

So far we have collected about a month worth of data and it is as always publicly [available for download](http://reports.ooni.nu/) by anybody interested in looking at it.

To advance this study at the end of October we did a OONI hackfest in Berlin. Helped by the ubiquitous sticky notes we were able to come up with a plan for those days of work and for continuing the project.

![](https://people.torproject.org/~art/blog/images/ooni-sticky-note-madness.jpg)

The first visualisation we produced is that of the reachability of bridges categorised by country and pluggable transport over time. This simple visualisation already conveys a lot of information and has proven itself a useful tool also in debugging issues with ooniprobe and the tools we use.

[  
 ![](https://people.torproject.org/~art/blog/images/ooni-bridge-reachability-timeline.png)  
](http://reports.ooni.nu/analytics/bridge_reachability/timeline/)

You can visit the actual page by clicking on the picture above.  
 Please note that because the tests are new and experimental you might find inaccuracies or bugs, so don't seriously rely on it for research just yet.

We also developed a [data pipeline](https://github.com/TheTorProject/ooni-pipeline/blob/master/Readme.md#ooni-pipeline<br%20/>%20) that places all of the collected OONI reports into a database. This makes it much easier to search/aggregate and visualise the data of the reports.

To read more about this project check out the [ooni-dev mailing list thread](https://lists.torproject.org/pipermail/ooni-dev/2014-November/000187.html) on this topic.

This project is still in it's very early stages of development, but we would love to hear feedback on it or your cool visualization ideas, as well as any questions regarding Tor bridge reachability (or more in general on Internet censorship) that you would like us to answer!
