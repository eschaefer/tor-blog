---
layout: post
title: "The NLnet Foundation funds two projects"
permalink: nlnet-foundation-funds-two-projects
date: 2008-06-07
author: phobos
category: blog
tags: ["directory services", "funding", "hidden services", "low bandwidth clients", "nlnet", "tor protocol"]
---

We're happy to announce the NLnet Foundation is funding two enhancements for the Tor software and network.

The two projects are summarized below:

- [Tor for low-bandwidth clients](http://www.torproject.org/projects/lowbandwidth).

The Tor anonymity system is currently only usable by internet users who have high-bandwith connections. Upon the start of the Tor client, a large file with all Tor server descriptions is being downloaded. An evolution of the Tor protocol is aimed to reduce the initial download size. The new Tor protocol version shall change the way a client receives the information for its Tor circuit setup in a way, that the initial download can be performed over a slow modem line in less then three minutes.

- [Speeding up Hidden Services](http://www.torproject.org/projects/hidserv).

The Tor anonymity system contains an important function that is called Tor Hidden Services, which allows users to set up anonymous information services, like websites, that can only be accessed through the Tor network and are protected against identification of the host that runs the services. Using these function, critical political and human rights information can be published in a way that protects the publisher and users of the service from repression and identification. The most critical limitation of this function is the time it takes until a Hidden Service is registered in the network and the latency of contact establishment when accessed by a user. The aim of this project is to develop the new protocol which will change the way Tor circuits are set up between the user and the Hidden Service as well as the way a Hidden Service is registered in the Tor network.

