---
layout: post
title: "Moving Tor to a datagram transport"
permalink: moving-tor-datagram-transport
date: 2011-11-07
author: sjmurdoch
category: blog
tags: ["datagram", "performance improvements", "tls"]
---

Tor currently transports data over encrypted TLS tunnels between nodes, in turn carried by TCP. This has worked reasonably well, but recent research has shown that it might not be the best option, particularly for performance.

For example, when a packet gets dropped or corrupted on a link between two Tor nodes, TCP will cause the packet to be retransmitted eventually. However, in the meantime, all circuits passing through this pair of nodes will be stalled, not only the circuit corresponding to the packet which was dropped.

Also, Tor uses two levels of congestion control; TCP for hop-by-hop links, and a custom scheme for circuits. This might not be the right approach -- maybe these schemes aren't the right ones to use or maybe there should only be one level of congestion control.

There have been a variety of solutions proposed to fix one or both of these problems, Most end up sending data as datagrams in UDP packets, and Tor is responsible for managing congestion and recovering from packet loss, and so can (hopefully) do so in a more intelligent way. However, there are many options for what architecture to use, what building blocks to build these schemes from, and how to tweak the many parameters that result.

To help clarify the various options, I've written a summary of both Tor's current network stack architecture and various proposals for how it can be improved. The document discusses various tradeoffs between the approaches, including performance, security, and engineering difficulties in deploying the solution. It ends with some provisional conclusions about which options are most promising.

The document, “ [Comparison of Tor Datagram Designs](http://www.cl.cam.ac.uk/~sjm217/papers/tor11datagramcomparison.pdf)”, is now available (with source in [git](https://gitweb.torproject.org/sjm217/torspec.git/tree/datagram_comparison:/proposals/ideas/xxx-datagram-comparison)), and I would welcome comments. Over the next few months I'll be working on building and evaluating prototypes for these schemes, and I will be incorporating feedback from the Tor community into the process.

