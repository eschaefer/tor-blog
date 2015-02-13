---
layout: post
title: "IPv6 is the future, I hear"
permalink: ipv6-future-i-hear
date: 2011-04-28 10:50:56
author: nickm
category: blog
status: closed
tags: ["development", "ipv6"]
---

A while ago, I wrote up a description of what needs to be done to get Tor to be IPv6-compliant and sent it to the tor-dev mailinglist. I thought it might be neat to share this on the blog too, so that people know what's left to do before we an call Tor fully IPv6-compliant.

Currently, I'm hoping that for 0.2.3.x we can at least get to the point where bridges can handle IPv6-only clients and exits can handle IPv6 addresses. If we get further, that will be even better.

* * * * *

### Overview

This document outlines what we'll have to do to make Tor fully support IPv6. It refers to other proposals, current and as-yet unwritten. It suggests a few incremental steps, each of which on its own should make Tor more useful in the brave new IPv6 future of tomorrow.

### Motivation

Turns out, 4 billion addresses wasn't enough.

### What needs to change

Tor uses the Internet in many ways. There are three main ways that will need to change for IPv6 support, from most urgent to least urgent.

Tor must allow connections from IPv6-only clients. (Currently, routers and bridges do not listen on IPv6 addresses, and can't advertise that they support IPv6 addresses, so clients can't learn that they do.)

Tor must transport IPv6 traffic and IPv6-related DNS traffic. (Currently, Tor only allows BEGIN cells to ask for connections to IPv4 targets or to hostnames, and only allows RESOLVE cells to request A and PTR records.)

Tor must allow nodes to connect to one another over IPv6.

Allowing IPv6-only clients is the most important, since unless we do, these clients will be unable to connect to Tor at all. Next most important is to support IPv6 DNS related dependencies and exiting to IPv6 services. Finally, allowing Tor nodes to support a dual stack of both IPv4 and IPv6 for interconnection seems like a reasonable step towards a fully hybrid v4/v6 Tor network.

One implementation hurdle that will need to get resolved alongside these changes is to convert uint32\_t to tor\_addr\_t in many more places in the Tor code, so we can handle addresses being either IPv4 or IPv6. There are a few cases, e.g. the local router list, where we'll want to think harder about the resource requirements of keeping tens of thousands of larger addresses in memory.

More issues may of course also be discovered as we develop solutions for these issues, some of which may need to take priority.

### Designs that we will need to do

For IPv6-only clients, we'll need to specify that routers can have multiple addresses and ORPorts.

There is an old proposal (118) to try to allow multiple ORPorts per router. It's been accepted; it needs to be checked for correctness, updated to track other changes in more recent Tor versions, and updated to work with the new microdescriptor designs.

Additionally, we'll need to audit the designs for all our codebase for places that might assume that IPs are a scarce resource. For example, clients assume that any two routers occupying an IPv4 /16 network are "too close" topologically to be used in the same circuit, and the bridgedb HTTPS distributor assumes that hopping from one /24 to another takes a little effort for most clients. The directory authorities assume that blacklisting an IP is an okay response to a bad router at that address. These and other places will instead need more appropriate notions of "closeness" and "similarity".

We'll want to consider geographic and political boundaries rather than purely mathematical notions such as the size of network blocks.

We'll need a way to advertise IPv6 bridges, and to use them.

For transporting IPv6-only traffic, we have another accepted design proposal (117). It has some open questions concerning proper behavior with respect to DNS lookups, and also needs to be checked and updated to track current Tor designs.

We do not have a current accepted design proposal for allowing nodes to connect to each other via IPv6. Allowing opportunistic IPv6 traffic between nodes that can communicate with both IPv4 and IPv6 will be relatively simple, as will be bridges that have only an IPv6 address: both of these fall out relatively simply from designing a process for advertising and connecting to IPv6 addresses. The harder problem is in supporting IPv6-only Tor routers. For these, we'll need to consider network topology issues: having nodes that can't connect to all the other nodes will weaken one of our basic assumptions for path generation, so we'll need to make sure to do the analysis enough to tell whether this is safe.

### Ready, fire, aim: An alternative methodology

At least one volunteer is currently working on IPv6 issues in Tor. If his efforts go well, it might be that our first design drafts for some of these open topics arrive concurrently with (or even in the form of!) alpha code to implement them. If so, we need to follow a variant of the design process, extracting design from code to evaluate it (rather than designing then coding). Probably, based on design review, some changes to code would be necessary.
