---
layout: post
title: "Tor design proposals: how we make changes to our protocol"
permalink: blog/tor-design-proposals-how-we-make-changes-to-our-protocol
date: 2015-02-08
author: nickm
category: blog
tags: ["tor weekly news"]
---

(This post is likely to be interesting for folks who want to know how the Tor software is made.)

At the core of the Tor software lies the network protocol that Tor relays and clients use to talk to each other. We try to make sure we have a [good set of specification documents](https://gitweb.torproject.org/torspec.git/tree/) for the protocol at all times, so that other people can write compatible software that interoperates with Tor.

Once upon a time, we used to change these specification documents whenever we changed the software's behavior. That didn't go well. We would have changes in the spec that we had forgotten to make in the software, and tons of inline comments where we argued about whether a particular paragraph was a good idea.

So back in 2007, we introduced a lightweight change-proposal process: to make a change to the Tor protocol, you write up a little design document, and send it to the tor-dev mailing list. Once it meets editorial quality, it can go into the [proposals repository](https://gitweb.torproject.org/torspec.git/tree/proposals). Once it's implemented, it can be merged into the spec.

There are a lot of proposals to look at, though. The current set of open proposals has almost 100,000 words in it! (That's almost half again as long as the Tor specs themselves.)

To help people navigate through this pile of design proposals, I started to write a regular "proposal status" email to explain what all of the open proposals are about. Last year, however, I fell out of the habit. Tonight, I've tried to fall back in: [here's the latest proposal status writeup](https://gitweb.torproject.org/torspec.git/tree/proposals/proposal-status.txt).

Below the cut, my summaries of the still-open proposals that have been added in the past couple of year -- and thanks to all the busy designers who have been working to think of ways to improve Tor! [**read more »**](https://blog.torproject.org/blog/tor-design-proposals-how-we-make-changes-our-protocol)
