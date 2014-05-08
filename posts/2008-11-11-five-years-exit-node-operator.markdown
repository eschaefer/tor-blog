---
layout: post
title: "Five Years as an Exit Node Operator"
permalink: five-years-exit-node-operator
date: 11/11/2008
author: phobos
category: blog
tags: ["exit node", "exit relay", "hugging dmca notices", "operator experiences", "tor is benign"]
---

The official version of ["What to expect"](https://www.torproject.org/faq-abuse.html.en#TypicalAbuses) when running a Tor exit relay is fairly brief. This post will be verbose.

I've been running a node since 2003. I first started off running a node in Xen on a server at a colocation datacenter with an un-metered line. The dual Xeon kept up with the demands fairly well. I ran it with the default exit policy with open irc ports. Things went smoothly for many months until my ISP called. The Abuse Department said my IP was reported in a mass irc bot attack against [DalNet](http://www.dal.net/). I spent some time on the phone explaining Tor, explaining how it's an anonymizing proxy, and how it's used for good in the world. I highlighted that of the megabits of bandwidth it provided 7x24 for many months, this was the first issue. They asked that I block irc ports, and all would be well. I modified the exit policy to block irc ports.

Many more months passed without issue. Apparently, given the lax bandwidth controls, many other customers ran Tor exit nodes as well. The ISP updated their Terms of Service, and notified all of us that running any proxy was now in violation of the ToS. This meant I was at risk of disconnection. I switched to a non-exit configuration. I ran this way for months. I knew full well I was violating the ToS. If I was disconnected, it was my fault. Then the ISP was bought; and the new owners demanded I shut off my Tor node or be disconnected. It was fun while it lasted.

Welcome to 2005. New ISP, same nickname, different server, same non-exit Tor configuration. Tor loved the dual opteron cpus. The difference in cpu load was dramatic. The load before was 40-50% cpu for "NumCPU 2" on the dual Xeons. On the dual Opterons, the load was 5-10%. Same non-exit config. Same version of Tor. Different hardware, newer version of the OS (Redhat 4 as opposed to CentOS 3).

I sustained 15 Mb/s the first day. Woo! Oh wait, they meter bandwidth at the switch, and now I have to pay for it. Ok, BandwidthRate here we come. The new ISP was relatively new. The CEO was on the forums. That's how small and new they were. We chatted, he didn't see a problem with Tor. Great.

I changed the config to the default exit policy with irc blocked. About a month later, the DMCA Notice bots hit. And boy, they hit like hourly. I setup a procmail recipe to pull the company and supposed infringing content out of their emails and stuff them into a response template based on [The Tor DMCA Response](https://www.torproject.org/eff/tor-dmca-response.html) Template. After about 3 weeks of this, I switched back to non-exit mode for a month or so. No one asked me to do this, I just felt nervous; or perhaps it was the chilling effect of the notices. And then I switched back to default minus irc exit configuration.

Months would go by without a complaint. Google would occasionally complain that my IP defaced some Google Groups. Or some random person from a blog that got hit with spam from my IP would complain. Once again, I'd explain Tor, and everything would resolve itself. I wrote [this wiki entry](https://wiki.torproject.org/noreply/TheOnionRouter/TorAbuseTemplates) after noting the common patterns that worked when dealing with abuse complaints.

Recently, the DMCA notices have become popular again. However, this time they're complaining directly to the ISP, not to me. My ISP opens support tickets and copy and pastes the exact email they received. I respond with the same DMCA Response template I did before. So far, they just keep closing the tickets.

In the grand scheme of things, Tor is pretty benign. I fluctuate between 2-5 Mb/s depending upon how much transit I've consumed for that billing period. Tor's bandwidth controls are surprisingly accurate. When I configure Tor to consume 1.8TB of transit over 30 days, it'll do it and not a byte more.

In total, I've received around 50 DMCA infringement notices, 20 abuse complaints, and zero visits from the Feds. After 5 years, I must have transferred petabytes of normal Tor traffic. Hopefully, I've helped users in restrictive environments see the unfiltered Internet. Or helped people keep their privacy and anonymity intact while online. Sorry to disappoint you if you were expecting SWAT teams and black helicopters and mad car chases through the streets. Real life is much more boring.

