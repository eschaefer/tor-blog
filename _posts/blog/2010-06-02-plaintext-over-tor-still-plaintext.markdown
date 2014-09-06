---
layout: post
title: "Plaintext over Tor is still plaintext"
permalink: blog/plaintext-over-tor-still-plaintext
date: 2010-06-02
author: phobos
category: blog
tags: ["exit relays", "plaintext communications", "tor", "wikileaks"]
---

Recently, a few articles have been published regarding Tor, [Wikileaks](http://wikileaks.org/), and snooping data coming out of the Tor network. I write to remind our users, and people in search of privacy enhancing technology, that good software is just one part of the solution. Education is just as important. This is why there is a [warning on the Tor download page](//www.torproject.org/download/download.html.en#warning) about what Tor does and does not do. We also have a [FAQ entry about this topic](https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/TorFAQ#CanexitnodeseavesdroponcommunicationsIsntthatbad). Any plaintext communication over the Internet is open to intercept. This is true if the transport mechanism is email, http, tor, or carrier pigeons. Tor does not magically encrypt the Internet from end to end. Tor does wrap your traffic in encrypted layers as it transports it through the Tor network. See [this diagram](https://www.torproject.org/images/htw3.png) for a visual explanation.

Tor provides anonymity and privacy by hiding where your Internet traffic is going and where it came from, but users must protect the security of their traffic by using encryption. Once you exit the last relay, you are back on the open Internet. Some web email providers, banks, and other sites use encryption by default when you log in, something you can check by looking for "https://" at the beginning of a URL. For more information, check out [Ethan Zuckerman's comments](http://ryansholin.com/2010/05/31/wikileaks-and-tor-moral-use-of-an-amoral-system/#comment-1769) on this topic.

For reference, these articles are unclear and blur concepts about Tor and Wikileaks. An article about Julian Assange of Wikileaks in [The New Yorker](http://www.newyorker.com/reporting/2010/06/07/100607fa_fact_khatchadourian) is the source of the confusion. [Ryan Sholin deliberates](http://ryansholin.com/2010/05/31/wikileaks-and-tor-moral-use-of-an-amoral-system/) on one paragraph from the New Yorker story. [Ethan Zuckerman](http://ethanzuckerman.com/) responded to Ryan's thoughts about Tor [here](http://ryansholin.com/2010/05/31/wikileaks-and-tor-moral-use-of-an-amoral-system/#comment-17691). We thanked EthanZ for the accurate response in an [Identi.ca dent](http://identi.ca/notice/34289748). It seems [Slashdot](http://yro.slashdot.org/story/10/06/01/2334237/Wikileaks-Was-Launched-With-Intercepts-From-Tor) and [Wired Threat Level](http://www.wired.com/threatlevel/2010/06/wikileaks-documents/) have picked up on just that one statement in the article by the New Yorker.

We hear from the [Wikileaks folks](http://www.theregister.co.uk/2010/06/02/wikileaks_tor_snooping_denial/) that [the premise](http://twitter.com/wikileaks/status/15220072701) behind these news articles is actually false -- they didn't bootstrap Wikileaks by monitoring the Tor network. But that's not the point. The point is that users who want to be safe need to be encrypting their traffic, whether they're using Tor or not.

