---
layout: post
title: "Media coverage of 'Covert channel vulnerabilities in anonymity systems'"
permalink: media-coverage-%2526quot%3Bcovert-channel-vulnerabilities-anonymity-systems%2526quot%3B
date: 2008-02-04
author: sjmurdoch
category: blog
tags: ["attacks", "covert channels", "media coverage", "tor"]
---

Over the past few days there has been some coverage of my [PhD thesis](http://www.lightbluetouchpaper.org/2007/12/10/covert-channel-vulnerabilities-in-anonymity-systems/), and its relationship to Tor, on blogs and online news sites. It seems like this wave started with a [column](http://mcpmag.com/columns/article.asp?editorialsid=2470) by Russ Cooper, which triggered articles in [PC World](http://www.pcworld.com/article/id,142094-pg,1/article.html) and [Dark Reading](http://www.darkreading.com/document.asp?doc_id=144606&WT.svl=news2_3). The media attention came as a bit of a surprise to me, since nobody asked to interview me over this. I'd encourage other journalists writing about Tor to contact someone from the project as we're happy to help give some context.

My thesis is a fairly diverse collection of work, but the articles emphasize the impact of the attacks I discuss on users of anonymity networks like Tor. Actually, my thesis doesn't aim to show that Tor is insecure; the reason I selected Tor as a test case was that it's one of the few (and by far the largest) low-latency system that aims to stand up to observation. Other, simpler, systems have comparatively well understood weaknesses, and so there is less value in researching them.

Quantifying the security of anonymity systems is a difficult question and still being actively worked on. Comparing different systems is even harder since they make different assumptions on the capabilities of attackers (the “threat model”). The mere chance of attacks doesn't indicate that a system is insecure, since they might make assumptions about the environment that are not met, or are insufficiently reliable for the scenario being considered.

The actual goal of my thesis was try to better understand the strengths and weaknesses of systems like Tor, but more importantly to also to suggest a more general methodology for discovering, and resolving flaws. I proposed that the work from the well-established field of [covert channels](http://en.wikipedia.org/wiki/Covert_channel) could be usefully applied, and used examples, including Tor, to justify this.

There remains much work to be done before it's possible to be sure how secure anonymity systems are, but hopefully this framework will be a useful one in moving forward. Since in September 2007 I joined the Tor project, I hope I'll also help in other ways too.

