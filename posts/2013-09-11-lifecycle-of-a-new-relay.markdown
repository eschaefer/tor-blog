---
layout: post
title: "The lifecycle of a new relay"
permalink: lifecycle-of-a-new-relay
date: 09/11/2013
author: arma
category: blog
tags: ["anonymity", "entry guards", "research"]
---

Many people set up new fast relays and then wonder why their bandwidth is not fully loaded instantly. In this post I'll walk you through the lifecycle of a new fast [non-exit](https://www.torproject.org/docs/faq#ExitPolicies) relay, since Tor's bandwidth estimation and load balancing has gotten much more complicated in recent years. I should emphasize that the descriptions here are in part anecdotal — at the end of the post I ask some research questions that will help us make better sense of what's going on.

I hope this summary will be useful for relay operators. It also provides background for understanding some of the anonymity analysis research papers that people have been asking me about lately. In an upcoming blog post, I'll explain why we need to raise the guard rotation period (and what that means) to improve Tor's anonymity. [Edit: [here is that blog post](https://blog.torproject.org/blog/improving-tors-anonymity-changing-guard-parameters)]

A new relay, assuming it is reliable and has plenty of bandwidth, goes through four phases: the unmeasured phase (days 0-3) where it gets roughly no use, the remote-measurement phase (days 3-8) where load starts to increase, the ramp-up guard phase (days 8-68) where load counterintuitively drops and then rises higher, and the steady-state guard phase (days 68+).

[  
 ![The phases of a new relay](https://people.torproject.org/~arma/lifecycle-blog.png)](https://people.torproject.org/~arma/lifecycle-blog.png)

**Phase one: unmeasured (days 0-3).**

When your relay first starts, it does a bandwidth self-test: it builds four circuits into the Tor network and back to itself, and then sends 125KB over each circuit. This step bootstraps Tor's passive bandwidth measurement system, which estimates your bandwidth as the largest burst you've done over a 10 second period. So if all goes well, your first self-measurement is 4\*125K/10 = 50KB/s. Your relay publishes this number in your relay descriptor.

The [directory authorities](https://www.torproject.org/docs/faq#KeyManagement) list your relay in the network consensus, and clients get good performance (and balance load across the network) by choosing relays proportional to the bandwidth number listed in the consensus.

Originally, the directory authorities would just use whatever bandwidth estimate you claimed in your relay descriptor. As you can imagine, that approach made it [cheap](http://freehaven.net/anonbib/#bauer:wpes2007) for even a small adversary to attract a lot of traffic by simply lying. In 2009, Mike Perry deployed the ["bandwidth authority"](https://blog.torproject.org/blog/torflow-node-capacity-integrity-and-reliability-measurements-hotpets) scripts, where a group of fast computers around the Internet (called bwauths) do active measurements of each relay, and the directory authorities [adjust the consensus bandwidth up or down](https://gitweb.torproject.org/torflow.git/blob/HEAD:/NetworkScanners/BwAuthority/README.BwAuthorities) depending on how the relay compares to other relays that advertise similar speeds. (Technically, we call the consensus number a "weight" rather than a bandwidth, since it's all about how your relay's number compares to the other numbers, and once we start adjusting them they aren't really bandwidths anymore.)

The bwauth approach isn't ungameable, but it's a lot better than the old design. Earlier this year we plugged another vulnerability by capping your consensus weight to 20KB until a threshold of bwauths have an opinion about your relay — otherwise there was a [several-day window](https://trac.torproject.org/projects/tor/ticket/2286) where we would use your claimed value because we didn't have anything better to use.

So that's phase one: your new relay gets basically no use for the first few days of its life because of the low 20KB cap, while it waits for a threshold of bwauths to measure it.

**Phase two: remote measurement (days 3-8).**

Remember how I said the bwauths adjust your consensus weight based on how you compare to similarly-sized relays? At the beginning of this phase your relay hasn't seen much traffic, so your peers are the other relays who haven't seen (or can't handle) much traffic. Over time though, a few clients will build circuits through your relay and push some traffic, and the passive bandwidth measurement will provide a new larger estimate. Now the bwauths will compare you to your new (faster) peers, giving you a larger consensus weight, thus driving more clients to use you, in turn raising your bandwidth estimate, and so on.

Tor clients generally make three-hop circuits (that is, paths that go through three relays). The first position in the path, called the guard relay, is special because it helps protect against a certain anonymity-breaking attack. Here's the attack: if you keep picking new paths at random, and the adversary runs a few relays, then over time the chance drops to zero that \*every single path you've made\* is safe from the adversary. The [defense](http://freehaven.net/anonbib/#hs-attack06) is to choose a small number of relays (called guards) and always use one of them for your first hop — either you chose wrong, and one of your guards is run by the adversary and you lose on many of your paths; or you chose right and all of your paths are safe. Read the [Guard FAQ](https://www.torproject.org/docs/faq#EntryGuards) for more details.

Only [stable and reliable](https://gitweb.torproject.org/torspec.git/blob/HEAD:/dir-spec.txt#l1768) relays can be used as guards, so no clients are willing to use your brand new relay as their first hop. And since in this story you chose to set up a non-exit relay (so you won't be the one actually making connections to external services like websites), no clients will use it as their third hop either. That means all of your relay's traffic is coming from being the second hop in circuits.

So that's phase two: once the bwauths have measured you and the directory authorities lift the 20KB cap, you'll attract more and more traffic, but it will still be limited because you'll only ever be a middle hop.

**Phase three: Ramping up as a guard relay (days 8-68).**

This is the point where I should introduce consensus flags. Directory authorities assign the [Guard flag](https://gitweb.torproject.org/torspec.git/blob/HEAD:/dir-spec.txt#l1685) to relays based on three characteristics: "bandwidth" (they need to have a large enough consensus weight), "weighted fractional uptime" (they need to be working most of the time), and "time known" (to make attacks more expensive, we don't want to give the Guard flag to relays that haven't been around a while first). This last characteristic is most relevant here: on today's Tor network, you're first eligible for the Guard flag on day eight.

Clients will only be willing to pick you for their first hop if you have the "Guard" flag. But here's the catch: once you get the Guard flag, all the rest of the clients back off from using you for their middle hops, because when they see the Guard flag, they assume that you have plenty of load already from clients using you as their first hop. Now, that assumption will become true in the steady-state (that is, once enough clients have chosen you as their guard node), but counterintuitively, as soon as you get the Guard flag you'll see a dip in traffic.

Why do clients avoid using relays with the Guard flag for their middle hop? Clients look at the scarcity of guard capacity, and the scarcity of exit capacity, and proportionally avoid using relays for positions in the path that aren't scarce. That way we [allocate available resources best](https://gitweb.torproject.org/torspec.git/blob/HEAD:/dir-spec.txt#l2014): relays with the Exit flag are used mostly for exiting when they're scarce, and relays with the Guard flag are used mostly for entering when they're scarce.

It isn't optimal to allow this temporary dip in traffic (since we're not taking advantage of resources that you're trying to contribute), but it's a short period of time overall: clients rotate their guards nodes every 4-8 weeks, so pretty soon some of them will rotate onto your relay.

To be clear, there are two reasons why we have clients rotate their guard relays, and the reasons are two sides of the same coin: first is the above issue where new guards wouldn't see much use (since only new clients, picking their guards for the first time, would use a new guard), and second is that old established guards would accrue an ever-growing load since they'd have the traffic from all the clients that ever picked them as their guard.

One of the reasons for this blog post is to give you background so when I later explain why we need to extend the guard rotation period to many months, you'll understand why we can't just crank up the number without also [changing some other parts of the system](https://trac.torproject.org/projects/tor/ticket/9321) to keep up. Stay tuned for more details there, or if you don't want to wait you can read the [original research questions](https://blog.torproject.org/blog/research-problem-better-guard-rotation-parameters) and the followup research papers by [Elahi et al](http://freehaven.net/anonbib/#wpes12-cogs) and [Johnson et al](http://freehaven.net/anonbib/#ccs2013-usersrouted).

**Phase four: Steady-state guard relay (days 68+).**

Once your relay has been a Guard for the full guard rotation period (up to 8 weeks in Tor 0.1.1.11-alpha through 0.2.4.11-alpha, and up to 12 weeks in Tor 0.2.4.12-alpha and later), it should reach steady-state where the number of clients dropping it from their guard list balances the number of clients adding it to their guard list.

**Research question: what do these phases look like with real-world data?**

All of the above explanations, including the graphs, are just based on anecdotes from relay operators and from ad hoc examination of consensus weights.

Here's a great class project or thesis topic: using our publically available [Tor network metrics data](https://metrics.torproject.org/data.html), track the growth pattern of consensus weights and bandwidth load for new relays. Do they match the phases I've described here? Are the changes inside a given phase linear like in the graphs above, or do they follow some other curve?

Are there trends over time, e.g. it used to take less time to ramp up? How long are the phases in reality — for example, does it really take three days before the bwauths have a measurement for new relays?

How does the scarcity of Guard or Exit capacity influence the curves or trends? For example, when guard capacity is less scarce, we expect the traffic dip at the beginning of phase three to be less pronounced.

How different were things before we added the 20KB cap in the first phase, or before we did remote measurements at all?

Are the phases, trends, or curves different for exit relays than for non-exit relays?

The "steady-state" phase assumes a constant number of Tor users: in situations where many new users appear (like the [botnet invasion in August 2013](https://blog.torproject.org/blog/how-to-handle-millions-new-tor-clients)), current guards will get unbalanced. How quickly and smoothly does the network rebalance as clients shift guards after that?

