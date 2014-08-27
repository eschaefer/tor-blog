---
layout: post
title: "Plain Vidalia Bundles to be Discontinued (Don't Panic!)"
permalink: plain-vidalia-bundles-be-discontinued-dont-panic
date: 2011-10-20
author: erinn
category: blog
tags: ["package updates", "tbb", "tor browser bundle", "vidalia bundle"]
---

Over the past few years, Tor has gotten more popular and has had to grow and change to accommodate a highly varied userbase. One aspect of this is getting the software into users' hands and having it immediately do what they want it to, while also not allowing them to inadvertently deanonymize themselves because they missed a configuration step or didn't understand which applications were using Tor and which were not. As a result, we have standardized on the Tor Browser Bundle for all platforms and are currently promoting it as our only fully supported client experience.

Since the Tor Browser Bundle offers the best current protection, we are moving to a client/server model for packages, and consequently the "plain" Vidalia bundles will be discontinued by the **end of the year** and no longer recommended for client usage. We've started rolling out server Vidalia bundles for Windows, which you can test by going to the [download page](https://www.torproject.org/download).

There are currently (and will continue to be) three types of server bundles available:

- Bridge-by-default Vidalia bundle

This configures Tor to act as a bridge by default, so as soon as you install it and run it, you will be helping censored users reach the Tor network. You can read more about bridges [here](https://www.torproject.org/docs/bridges). This bundle still includes Torbutton and Polipo, but those will be removed in the next release (date to be determined).

- Relay-by-default Vidalia bundle

This configures Tor to run as a **non-exit** relay by default. This means you will serve as either a guard or middle node and help grow the size of the Tor network. You can read more about Tor relay configuration [here](https://www.torproject.org/docs/tor-doc-relay).

- Exit-by-default Vidalia bundle

This configures Tor to run as an **exit relay** by default. Exit nodes are special, as they allow traffic to exit from the Tor network to the plain internet, and anyone who has not already looked into the risks associated with running an exit relay should read our [tips for running an exit node with minimal harassment](https://blog.torproject.org/running-exit-node)

We've started creating a [Tor Browser Bundle FAQ](https://trac.torproject.org/projects/tor/wiki/doc/TorFAQ#TorBrowserBundle), but we'd like to hear your concerns so we can provide answers where necessary, documentation for alternative setups, and fix the software where answers are insufficient. We have several months before Tor Browser Bundle is the only option, so please help us make it as good as possible! If you have bugs to file, please don't file them in the blog comments -- use our [bug tracker](https://trac.torproject.org) for that.

