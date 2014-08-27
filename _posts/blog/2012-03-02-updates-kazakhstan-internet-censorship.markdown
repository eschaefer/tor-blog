---
layout: post
title: "Updates on Kazakhstan Internet Censorship"
permalink: updates-kazakhstan-internet-censorship
date: 2012-03-02
author: phobos
category: blog
tags: ["deep packet inspection", "dpi", "internet censorship", "kazakhstan", "network data"]
---

Two weeks ago [we announced](https://blog.torproject.org/blog/kazakhstan-upgrades-censorship-deep-packet-inspection) the use of deep packet inspection to censor the Internet in Kazakhstan. Over those two weeks we've continued working on how they are blocking native tor connections. The good news is that our [obfsproxy bundle](https://www.torproject.org/projects/obfsproxy.html.en) continues to work well in country. Thanks to wanoskarnet, ann, and others for their help.

We have some network-level data captures at both ends to help us assess what is occuring. It seems the Kazakhstan firewall finds something unique in the TLS "Server Hello" message as sent by the Tor relay or bridge and therefore blocks subsequent communications. IP address and TCP port are irrelevant to the censorship. Research continues. Anonymized network flows are available here:

.kz client to relay: [https://media.torproject.org/misc/2012-02-28-tor-kz-client-flow.txt](https://media.torproject.org/misc/2012-02-28-tor-kz-client-flow.txt "https://media.torproject.org/misc/2012-02-28-tor-kz-client-flow.txt")

and

the relay view of that same conversation: [https://media.torproject.org/misc/2012-02-28-tor-kz-bridge-relay-flow.tx...](https://media.torproject.org/misc/2012-02-28-tor-kz-bridge-relay-flow.txt "https://media.torproject.org/misc/2012-02-28-tor-kz-bridge-relay-flow.txt")

Here's a graph of what this censorship looks like nationwide. The red dots are probable censorship events.

<center><a href="https://media.torproject.org/image/blog-images/direct-users-off-2011-12-03-on-300-2012-03-02-kz.png"><img src="https://media.torproject.org/image/blog-images/direct-users-off-2011-12-03-on-300-2012-03-02-kz.png" height="200" width="320"></a></center>. The full image is here, [https://media.torproject.org/image/blog-images/direct-users-off-2011-12-...](https://media.torproject.org/image/blog-images/direct-users-off-2011-12-03-on-300-2012-03-02-kz.png "https://media.torproject.org/image/blog-images/direct-users-off-2011-12-03-on-300-2012-03-02-kz.png")
