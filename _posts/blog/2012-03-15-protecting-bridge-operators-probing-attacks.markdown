---
layout: post
title: "Protecting bridge operators from probing attacks"
permalink: protecting-bridge-operators-probing-attacks
date: 2012-03-15
author: sjmurdoch
category: blog
tags: ["anonymity", "blocking resistance", "bridges", "research", "torouter"]
---

Although Tor was originally designed to enhance privacy, the network is increasingly being used to provide access to websites from countries where Internet connectivity is filtered. To better support this goal, Tor introduced the feature of [bridge nodes](https://www.torproject.org/docs/bridges) – Tor nodes which route traffic but are not published in the list of available Tor nodes. Consequently bridges are commonly not blocked in countries where access to the public Tor nodes are (with the exception of China and Iran).

For bridge nodes to work well, we need lots of them. This is both to make it hard to block them all, and also to provide enough bandwidth capacity for all their users. To help achieve this goal, the Tor Browser Bundle now makes it as easy as clicking a button to turn a normal Tor client into a bridge. The upcoming version of Tor will even set up port forwarding on home routers (through UPnP and NAT-PMP) to make it easier still.

There are, however, potential risks to Tor users if they turn their client into a bridge. These were summarized in a paper by Jon McLachlan and Nicholas Hopper: ["On the risks of serving whenever you surf"](http://www-users.cs.umn.edu/~hopper/surf_and_serve.pdf). I discussed these risks in a [previous blog post](https://blog.torproject.org/blog/risks-serving-whenever-you-surf), along with ways to mitigate them. In this blog post I'll cover some initiatives the Tor project is working on (or considering), which could further reduce the risks.

The attack than McLachlan and Hopper propose involves finding a list of bridges, and then probing them over time. If the bridge responds at all, then we know that the bridge operator could be surfing the web though Tor. So, if the attacker suspects that a blogger is posting through Tor and the blogger's Tor client is also a bridge, then only the bridges which are running at the time a blog post was written could belong to the blogger. There are likely to be quite a few such bridges, but if the attack is repeated, the set of potential bridge IP addresses will be narrowed down.

What is more, the paper also proposes measuring how quickly each bridge responds, which might tell the attacker something about how heavily the bridge operator is using their Tor client. If the attacker probes the rest of the Tor network, and sees a node with performance patterns similar to the bridge being probed, then it is likely that there is a connection going through that node and that bridge. In some circumstances this attack could be used to track connections all the way through the Tor network, and back to a client who is also acting as a bridge.

One way of reducing the risk of these attacks succeeding is to run the bridge on a device which is always on. In this case, just because a bridge is running doesn't mean the operator is using Tor. Therefore less information is leaked to a potential attacker. As laptops become more prevalent, keeping a bridge on 24/7 can be inconvenient so the Tor Project is working on two bits of hardware (known as [Torouters](https://trac.torproject.org/projects/tor/wiki/doc/Torouter)) which can be left running a bridge even if the user's computer is off. If someone probes the bridge now, they can't learn much about whether the operator is using Tor as a client, and so it leaks less information about what the user is doing.

Having an always-on bridge helps resist profiling based on when a client is on. However, evaluating the risk of profiling based on bridge performance is more complex. The reason this attack works is that when a node is congested, increasing traffic on one connection (say, due to the bridge operator using Tor) decreases the traffic on another (say, the attacker probing the bridge). If you run a Tor client on your PC, and a Tor bridge on a separate device, this reduces the opportunity for congestion on one leading to congestion on the other. However, there is still the possibility for congestion on the network connection which the bridge and device share, and maybe you do want to use the bridge device as a client too. So the Torouter helps, but doesn't fix the problem.

To fully decouple bridges from clients, they need to run on different hardware **and networks** . Here the [Tor Cloud](https://cloud.torproject.org/) project is ideal – bridges run on Amazon's (or another cloud provider's) infrastructure so congestion on the bridge can't affect the Tor client running on your PC, or it's network.

But maybe you do want to use your bridge as a client for whatever reason. Recall that the first step of the attack proposed by McLachlan and Hopper is to find the bridges' IP addresses. This is becoming increasingly difficult as more bridges are being set up. Also, there is work in progress to make it harder to scan networks for bridges. Originally this was intended to make it harder to find and block bridges, but it applies equally well to preventing probing. These schemes (e.g. [BridgeSPA](http://www.cypherpunks.ca/~iang/pubs/bridgespa-wpes.pdf) by Smits et. al.) mean that just because you have a bridge's IP address, it doesn't mean that you can route traffic through it (to measure performance) or even check if the bridge is running. To do either, you need to have a secret which is distributed only to authorized users of the bridge.

There is still more work to be done in protecting bridge operators, but the projects discussed above (and in the [previous blog post](https://blog.torproject.org/blog/risks-serving-whenever-you-surf)) certainly improve the situation. Work continues both in academia and at the Tor Project to better understand the problem and develop further fixes.

