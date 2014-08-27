---
layout: post
title: "Tor Weekly News — November 13th, 2013"
permalink: tor-weekly-news-%E2%80%94-november-13th-2013
date: 2013-11-13
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the twentieth issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# First beta release of Tor Browser Bundle 3.0

The [Tor Browser Bundle](https://www.torproject.org/projects/torbrowser.html) is the Tor Project’s flagship product: an easy and straightforward way to browse the web with anonymity and privacy.

With previous Tor Browser Bundles, users had to interact with two different applications, Vidalia and the browser itself. Vidalia was responsible for handling and configuring the tor daemon, and the browser had no knowledge of the connection status and other details. The result was confusing error messages, and mismatched user expectations.

With the 3.0 series of Tor Browser Bundle, the browser is directly responsible for configuring and handling the tor daemon. Users only see one single application. It’s clearer that only the browser will go through the Tor network. Starting and stopping the browser will take care of starting and stopping tor — no extra steps are required.

Mike Perry, Kathleen Brade, Mark Smith, Georg Koppen, among others, are working hard to perfect many other usability and technical improvements that are part of Tor Browser Bundle 3.0 which has now reached the “beta” stage.

The new [3.0beta1 release](https://blog.torproject.org/blog/tor-browser-bundle-30beta1-released) is based on Firefox 17.0.10esr for [security updates](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox17.0.10), and contains several other small improvements and corrections.

Current users of the 3.0 alpha series should update. Others should [give it a try](https://archive.torproject.org/tor-package-archive/torbrowser/3.0b1/)!

# A critique of website traffic fingerprinting attacks

For a new [blog post](https://blog.torproject.org/blog/critique-website-traffic-fingerprinting-attacks), Mike Perry took the time to reflect on fingerprinting attacks on website traffic. These are attacks “where the adversary attempts to recognize the encrypted traffic patterns of specific web pages without using any other information. In the case of Tor, this attack would take place between the user and the Guard node, or at the Guard node itself.”

In the post, Mike lays down three distinct types of adversary that could mount fingerprinting attacks: partial blocking of Tor, identification of visitors of a set of targeted pages, and identification of all web pages visited by a user.

In theory, such attacks could pose devastating threats to Tor users. But in practice, “false positives matter” together with other factors that affect the classification accuracy. Mike gives a comprehensive introduction to these issues before reviewing five research papers published between 2011 and 2013. Each of them are summarized together with their shortcomings.

Mike concludes that “defense work has not been as conclusively studied as these papers have claimed, and that defenses are actually easier than is presently assumed by the current body of literature.” He encourages researchers to re-evaluate existing defenses “such as [HTTPOS](http://freehaven.net/anonbib/cache/LZCLCP_NDSS11.pdf), SPDY and pipeline randomization, [Guard node adaptive padding](https://bugs.torproject.org/7028), and [Traffic Morphing](http://freehaven.net/anonbib/cache/morphing09.pdf)“, and to think about “the development of additional defenses”. Mike ends his post by mentioning that some new defenses can also be dual purpose and help with end-to-end correlation attacks.

# The “bananaphone” pluggable transport

[Pluggable transports](https://www.torproject.org/docs/pluggable-transports.html) is how Tor traffic can be transformed from a  
client to a bridge in order to hide it from Deep Packet Inspection filters.

Improving upon the [initial work of Leif Ryge](https://github.com/leif/bananaphone), David Stainton has been working on the new [“bananaphone” pluggable transport for obfsproxy](https://github.com/david415/obfsproxy/tree/david-bananaphone). The latter implements “reverse hash encoding“, described by Leif Ryge as “a steganographic encoding scheme which transforms a stream of binary data into a stream of tokens (e.g., something resembling natural language text) such that the stream can be decoded by concatenating the hashes of the tokens.”

For a concrete example, that means that using [Project Gutenberg’s Don Quixote](http://www.gutenberg.org/cache/epub/29468/pg29468.txt) as corpus, one can encode “my little poney” into “lock whisper: yellow tremendous, again suddenly breathing. master’s faces; fees, beheld convinced there calm” and back again!

While it’s probably not going to be the most compact pluggable transport, “bananaphone” looks like a promising project.

# Miscellaneous news

Christian Grothoff, Matthias Wachs and Hellekin Wolf are working on getting [special-use domain names for P2P networks reserved](https://lists.torproject.org/pipermail/tor-dev/2013-November/005747.html) according to [RFC 6761](https://tools.ietf.org/html/rfc6761): “the goal is to reserve .onion, .exit, .i2p, .gnu and .zkey (so that they don’t become ordinary commercial TLDs at some point)”.

The Tails team has released their report on [Tails activity during the month of October](https://lists.torproject.org/pipermail/tor-reports/2013-November/000383.html). Things are happening on many fronts, have a look!

Andrea Shepard has been working on new scheduler code for Tor. Its goal is to remove the limitation that “we can only see one channel at a time when making scheduling decisions.” Balancing between circuits without opening new attack vectors is tricky, Andrea is asking for [comments on potential heuristics](https://lists.torproject.org/pipermail/tor-dev/2013-November/005761.html).

Justin Findlay has [recreated some of the website diagrams](https://lists.torproject.org/pipermail/tor-dev/2013-November/005762.html) in the versatile SVG format.

Roger [asked the community](https://lists.torproject.org/pipermail/tor-talk/2013-November/031001.html) to create a “Tor, king of anonymity” graphic for his presentations. Griffin Boyce made a [“queen of anonymity” picture](http://i.imgur.com/PmuFz4n.jpg), Lazlo Westerhof [crowned the onion](http://i.imgur.com/vYZSu6Q.png) and Matt Pagan did the [full Tor logo](http://i.imgur.com/2yIMmcQ.png) .

David Fifield released the new [Pluggable Transports Tor Browser Bundle version 2.4.17-rc-1-pt2](https://blog.torproject.org/blog/pluggable-transports-bundles-2417-rc-1-pt2-firefox-17010esr) based on Tor Browser Bundle 2.4.17-rc-1. The only change from the previous release of the pluggable transport bundle is a [workaround](https://bugs.torproject.org/10030#comment:20) that makes transports resume working on Mac OS X Mavericks.

# Tor help desk round-up

Recently users have been writing the help desk asking for assistance verifying the signature on their Tor Browser Bundle package. These users said they found the [instructions on the official Tor Project page](https://torproject.org/docs/verifying-signatures.html) confusing. One person reported being unsure of how to open a terminal on their computer. Another person did not know how to save the package signature onto the Desktop. Yet another person reported they were able to verify the signature only after discovering that their GnuPG program was named gpg2.exe rather than gpg.exe. A ticket on [improving the signature verification page](https://bugs.torproject.org/10073) has been opened.

One user mentioned wanting to use the Tor Browser Bundle as their default browser but being unable to do so because their online bank required Java. Java is disabled in the Tor Browser Bundle because it can bypass the browser proxy settings and leak the client’s real IP address over the network.

* * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, David Stainton, sqrt2, and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

