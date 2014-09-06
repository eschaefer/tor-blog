---
layout: post
title: "Iran partially blocks encrypted network traffic"
permalink: blog/iran-partially-blocks-encrypted-network-traffic
date: 2012-02-10
author: phobos
category: blog
tags: ["deep packet inspection", "dpi", "iranian censorship", "keyword filtering", "positive futures", "ssl blocking"]
---

Over the past two days we've been hearing from, and working with, a number of Iranians having difficulty using Tor from inside Iran. It seems the Iranian government has ramped up censorship in three ways: deep packet inspection (dpi) of SSL traffic, selective blocking of IP Address and TCP port combinations, and some keyword filtering. For instance, they have partially blocked access to Tor's website, torproject.org, via IP address (such as 86.59.30.36) and port 443 (which is the HTTPS port). The third level of blocking is by keywords, such as searching for the word 'tor' via regular, non-encrypted search engine websites.

The blocks on SSL are not complete and not nationwide. Where blocking is in place, initial investigations show they are identifying the beginning of the SSL handshake and simply interrupting the handshake. We continue to research and investigate solutions with the assumption that SSL will eventually be blocked nationwide inside Iran. Our goal is to defeat their dpi signatures and allow tor to work by default.

The Iran Media Program has [posted their thoughts](http://iranmediaresearch.com/en/blog/101/12/02/09/840) on what is happening from a journalist's perspective.

So far, it seems the majority of Tor users are not affected by these blocks. Iran is still the #2 country based on direct usage, [https://metrics.torproject.org/users.html?graph=direct-users&country=ir#...](https://metrics.torproject.org/users.html?graph=direct-users&country=ir#direct-users "https://metrics.torproject.org/users.html?graph=direct-users&country=ir#direct-users"). This number is on the decline, however.

More details to follow as we have them.

**Update** 2011-02-10 18:05 UTC: We are working on making our obfuscating proxy more stable and easier to deploy. If you can compile code, following [these directions](https://lists.torproject.org/pipermail/tor-talk/2012-February/023070.html) will help. We're also working on Amazon EC2 instances of obfsproxy for point and click deployment.

