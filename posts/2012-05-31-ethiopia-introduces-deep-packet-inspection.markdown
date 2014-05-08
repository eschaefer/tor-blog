---
layout: post
title: "Ethiopia Introduces Deep Packet Inspection"
permalink: ethiopia-introduces-deep-packet-inspection
date: 05/31/2012
author: Runa
category: blog
tags: ["censorship circumvention", "deep packet inspection", "dpi", "ethiopia", "internet censorship", "tor blocked"]
---

The Ethiopian Telecommunication Corporation, which happens to be the sole telecommunication service provider in Ethiopia, has deployed or begun testing Deep Packet Inspection (DPI) of all Internet traffic. We have previously analyzed the same kind of censorship in [China](https://blog.torproject.org/blog/knock-knock-knockin-bridges-doors), [Iran](https://blog.torproject.org/blog/iran-partially-blocks-encrypted-network-traffic), and [Kazakhstan](https://blog.torproject.org/blog/kazakhstan-upgrades-censorship-deep-packet-inspection).

Reports show that Tor stopped working a week ago -- even with bridges configured. Websites such as [https://gmail.com/](https://gmail.com/), [https://facebook.com/](https://facebook.com/), [https://twitter.com/](https://twitter.com/), and even [https://torproject.org/](https://torproject.org/) continue to work. The graphs below show the effects of this deployment of censorship based on Deep Packet Inspection:

![](https://media.torproject.org/image/blog-images/direct-users-off-2012-03-02-off-72-2012-05-31-et.png)

![](https://media.torproject.org/image/blog-images/bridge-users-2012-03-02-72-2012-05-31-et.png)

An analysis of data collected by a volunteer shows that they are doing some sort of TLS fingerprinting. The TLS server hello, which is sent by the Tor bridge after the TLS client hello, never reaches the client. We don't know exactly what they are fingerprinting on, but our guess is that it is either the client hello or the server hello. An illustration can be found in this [network flow diagram](https://media.torproject.org/image/blog-images/2012-05-31-ethiopia-dpi-blocking-of-tor.png).

Thanks to Philipp Winter and George Kadianakis for helping me analyze the data. If you have more information about the censorship in Ethiopia, please email [help@rt.torproject.org](mailto:help@rt.torproject.org).

