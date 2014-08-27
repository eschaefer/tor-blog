---
layout: post
title: "How to report bad relays"
permalink: how-report-bad-relays
date: 2014-07-29
author: phw
category: blog
tags: ["badexit", "exit relay", "mitm"]
---

We now have a [wiki page](https://trac.torproject.org/projects/tor/wiki/doc/ReportingBadRelays) which explains how bad relays should be reported to the Tor Project. A bad relay can be malicious, misconfigured, or otherwise broken. Once such a relay is reported, a subset of vigilant Tor developers (currently Roger, Peter, Damian, Karsten, and I) first tries to reproduce the issue. If it's reproducible, we attempt to get in touch with the relay operator and work on the issue together. However, if the relay has no contact information or we cannot reach the operator, we will resort to assigning flags (such as BadExit) to the reported relay which instructs clients to no longer use the relay in the future. In severe cases, we are also able to remove the relay descriptor from the network consensus which effectively makes the relay disappear. To get an idea of what bad behavior was documented in the past, have a look at this (no longer maintained) [wiki page](https://trac.torproject.org/projects/tor/wiki/doc/badRelays) or these [research](http://www.cs.columbia.edu/~mikepo/papers/tordecoys.raid11.pdf) [papers](http://www.cs.kau.se/philwint/spoiled_onions/pets2014.pdf).

We regularly scan the network for bad relays using [exitmap](https://gitweb.torproject.org/user/phw/exitmap.git) but there are several other great tools such as [Snakes on a Tor](https://gitweb.torproject.org/torflow.git/blob/HEAD:/NetworkScanners/ExitAuthority/README.ExitScanning), [torscanner](https://code.google.com/p/torscanner/), [tortunnel](http://www.thoughtcrime.org/software/tortunnel/), and [DetecTor](http://detector.io/DetecTor.html). We are also dependent on the wider community to help us spot relays which don't act as they should. So if you think that you stumbled upon a bad relay while using Tor, please report it to us by sending an email to [bad-relays@lists.torproject.org](mailto:bad-relays@lists.torproject.org). To find out which relay is currently being used as your exit relay, please visit our [Check service](https://check.torproject.org). Just tell us the relay's IP address (Check tells you what your IP address appears to be) and the behavior you observed. Then, we can begin to investigate!

