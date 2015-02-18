---
layout: post
title: "Tor Weekly News — January 14th, 2015"
permalink: tor-weekly-news-—-january-14th-2015
date: 2015-01-14 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the second issue in 2015 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

What to do if meek gets blocked
===============================

Regular readers of Tor Weekly News will be familiar with [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek), the pluggable transport developed by David Fifield. Where most existing transports work by connecting clients to “bridge” relays that are difficult for the adversary to discover (or identify as relays), meek makes all of a client’s Tor traffic appear as though it is destined for a domain that is “too big to block” — in other words, web platforms so popular that a censor cannot prevent access to them without disrupting lots of unrelated Internet activity in its sphere of control — when in fact the traffic is sent to meek servers running on those platforms, which in turn relay it into the regular Tor network. Google, Amazon, and Microsoft are some of the services whose domain names currently work as disguises for meek.

Unfortunately, that doesn’t mean meek is unblockable. As David [wrote](https://lists.torproject.org/pipermail/tor-talk/2015-January/036410.html) to the tor-talk mailing list, “that’s the wrong way to think about the problem”. “It is designed to be difficult and expensive to block […] but suppose a censor makes that call, and blocks Google/Amazon/whatever. What then?”

Two easy solutions are selecting a different backend (meek-amazon instead of meek-google, for example) or using a different DNS server: “The most common way to block a domain name is by DNS poisoning; i.e., the IP address behind the name is accessible, but the local DNS server gives you a false address. Try a public DNS server such as 8.8.8.8. But if that works, be aware that it’s probably only a temporary fix, as censors have historically figured out the alternate-DNS trick pretty fast.”

“What you really want to do”, David suggested, “if the easy things don’t work, is choose a different front domain.” Please see David’s message for a fuller explanation of the difference between the backend and the “front domain”, and a guide to configuring new domains — as well as one to setting up your own meek web app, if all else fails.

Miscellaneous news
==================

sycamoreone [announced](https://lists.torproject.org/pipermail/tor-talk/2015-January/036425.html) orc, a Go library that implements parts of Tor’s control protocol. “I do have some ideas for a higher-level interface, but no fixed plan yet. The next step will probably be to add net/http-like handlerFuncs to handle (asynchronous) replies from the onion router.”

taxakis [linked](https://lists.torproject.org/pipermail/tor-talk/2015-January/036420.html) to “[Post-Quantum Secure Onion Routing](http://eprint.iacr.org/2015/008)” by Satrajit Ghosh and Aniket Kate, a new paper proposing a successor to the currently-used ntor handshake protocol that would be “resilient against quantum attacks, but also at the same time allow OR nodes to use the current DH public keys, and consequently require no modification to the current Tor public key infrastructure.” Nick Mathewson [wondered](https://lists.torproject.org/pipermail/tor-talk/2015-January/036429.html) whether “anybody around here has the cryptographic background to comment on the PQ part of their scheme?”, and compared it to Yawning Angel’s [experimental “basket” protocol](https://lists.torproject.org/pipermail/tor-dev/2014-December/007977.html).

Nick also sent out a draft of [proposal 240](https://lists.torproject.org/pipermail/tor-dev/2015-January/008115.html), describing “a simple way for directory authorities to perform signing key revocation”.

Daniel Forster [asked](https://lists.torproject.org/pipermail/tor-dev/2015-January/008099.html) for advice on proposed research into splitting traffic over multiple entry guards in combination with traffic padding: “Is the approach heading in a not so great direction w.r.t. the Tor Project’s ‘only one entry node’ decision?”

Karsten Loesing submitted his [status report for December](https://lists.torproject.org/pipermail/tor-reports/2015-January/000744.html), and George Kadianakis sent out the [report for SponsorR](https://lists.torproject.org/pipermail/tor-reports/2015-January/000745.html).

“After CCC I have a list of people that I have given raspberry pi’s with ooniprobe, and I would like to start coordinating with them via a mailing list”, wrote [Arturo Filastò](https://bugs.torproject.org/14140), and the result is the [ooni-operators mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/ooni-operators). If you regularly run ooniprobe, or want to start, be sure to sign up!

Aleksejs Popovs shared with the ooni-dev mailing list [the results](https://lists.torproject.org/pipermail/ooni-dev/2015-January/000220.html) of an OONI investigation into Latvian internet censorship, conducted using ooniprobe.

Dan O’Huiginn started a [conversation](https://lists.torproject.org/pipermail/ooni-dev/2015-January/000208.html) about how to ensure users are informed of the possible consequences of running OONI tests.

Thanks to [John Knoll](https://lists.torproject.org/pipermail/tor-mirrors/2015-January/000828.html) and [Monsieur Tino](https://lists.torproject.org/pipermail/tor-mirrors/2015-January/000835.html) for running mirrors of the Tor Project’s website and software archive!

“How do we prevent a website mirror admin from tampering with the served files?”, [wondered](https://lists.torproject.org/pipermail/tor-mirrors/2015-January/000844.html) Frédéric Cornu. Christian Krbusek [clarified](https://lists.torproject.org/pipermail/tor-mirrors/2015-January/000845.html) that “in fact, you can’t prevent that, but you are also mirroring the signature files. So anybody downloading from any mirror — even the original host — should verify the downloads”. Andrew Lewman [added](https://lists.torproject.org/pipermail/tor-mirrors/2015-January/000848.html) that “the binaries are signed by well-known keys of tor packagers and developers. The mirror update script randomly selects a binary and verifies it each time it runs. If the binaries don't match, the mirror is removed from the public list.”

* * * * *

This issue of Tor Weekly News has been assembled by Harmony.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
