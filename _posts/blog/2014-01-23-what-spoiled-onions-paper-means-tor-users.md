---
layout: post
title: "What the \"Spoiled Onions\" paper means for Tor users"
permalink: what-spoiled-onions-paper-means-tor-users
date: 2014-01-23 20:00:10
author: phw
category: blog
status: closed
tags: ["exit relays", "https", "mitm", "research", "ssl", "torbrowser"]
---

Together with Stefan, I recently published the paper "[Spoiled Onions: Exposing Malicious Tor Exit Relays](http://www.cs.kau.se/philwint/spoiled_onions/)". The paper only discusses our results and how we obtained them and we don't talk a lot about the implications for Tor users. This blog post should fill that gap.

First, it's important to understand that 25 relays in four months isn't a lot. It is ultimately a very small fraction of the Tor network. Also, it doesn't mean that 25 out of 1,000 relays are malicious or misconfigured (we weren't very clear on that in the paper). We have yet to calculate the churn rate of exit relays which is the rate at which relays join and leave the network. 1,000 is really just the approximate number of exit relays at any given point in time. So the actual number of exit relays we ended up testing in four months is certainly higher than that. As a user, that means that you will not see many malicious relays "in the wild".

Second, Tor clients select relays in their circuits based on the bandwidth they are contributing to the network. Faster relays see more traffic than slower relays which balances the load in the Tor network. Many of the malicious exit relays contributed relatively little bandwidth to the Tor network which makes them quite unlikely to be chosen as relay in a circuit.

Third, even if your traffic is going through a malicious exit relay, it doesn't mean that everything is lost. Many of the attacks we discovered still caused Firefox' infamous "about:certerror" warning page. As a vigilant user, you would notice that something isn't quite right and hopefully leave the site. In addition, TorBrowser ships with [HTTPS-Everywhere](https://www.eff.org/Https-everywhere) which by default attempts to connect to some sites over HTTPS even though you just typed "http://". After all, as we said in the past, "[Plaintext over Tor is still plaintext](https://blog.torproject.org/blog/plaintext-over-tor-still-plaintext)".

Finally, we want to point out that all of these attacks are of course not limited to the Tor network. You face the very same risks when you are connecting to any public WiFi network. One of the fundamental problems is the broken CA system. Do you actually know all the \~50 organisation who you implicitly trust when you start your Firefox, Chrome, or TorBrowser? Making the CA system more secure is a very challenging task for the entire Internet and not just the Tor network.
