---
layout: post
title: "Tor Weekly News — October 23rd, 2013 "
permalink: tor-weekly-news-%E2%80%94-october-23rd-2013
date: 2013-10-23
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the seventeenth issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tor’s anonymity and guards parameters

In a [lengthly blog post](https://blog.torproject.org/blog/improving-tors-anonymity-changing-guard-parameters), Roger Dingledine looked back on three research papers published in the past year. Some of them have been covered and most of the time misunderstood by the press. A good recap of the research problems, what the findings mean and possible solutions hopefully will help everyone understand better.

[Introduced in 2005](https://blog.torproject.org/blog/top-changes-tor-2004-design-paper-part-2), entry guards were added to recognise that “some circuits are going to be compromised, but it’s better to increase your probability of having no compromised circuits at the expense of also increasing the proportion of your circuits that will be compromised if any of them are.” Roger “originally picked ‘one or two months’ for guard rotation” but the initial parameters called for [more in-depth research](https://blog.torproject.org/blog/research-problem-better-guard-rotation-parameters).

That call was heard by “the [Tor research community](http://freehaven.net/anonbib/), and it’s great that Tor gets such attention. We get this attention because we put so much effort into making it easy  for researchers to analyze Tor.” In his writing Roger highlights the finding of three papers. Two of them published at WPES 2012 and Oakland 2013, and another upcoming at CCS 2013.

These research efforts highlighted several issues in the way Tor handles entry guards. Roger details five complementary fixes: using fewer guards, keeping the same guards for longer, better handling of brief unreachability of a guard, making the network bigger, and smarter assignment of the guard flag to relays. Some will require further research to identify the best solution. There are also other aspects regarding systems which don’t currently record guards such as Tails, how pluggable transports could prevent attackers from recognising Tor users, or enhancing measurements from the bandwidth authorities…

The whole blog post is insightful and is a must read for everyone who wishes to better understand some of Tor’s risk mitigation strategies. It is also full of little and big things where you could make a difference!

# Hidden Service research

George Kadianakis posted a [list of items that need work in the Hidden Service area](https://lists.torproject.org/pipermail/tor-dev/2013-October/005637.html). Despite not being exhaustive, the list contains many items that might help with upgrading the Hidden Service design, be it around security, performance, guard issues or “petname” systems.

Help and comments are welcome!

# Usability issues in existing OTR clients

The consensus after the first round of discussions and research done in the prospect of providing a [new secure instant-messaging Tor bundle](https://trac.torproject.org/projects/tor/wiki/org/sponsors/Otter/Attentive) is to use Mozilla Instantbird at its core. Arlo Breault [sent out a draft plan](https://lists.torproject.org/pipermail/tor-dev/2013-October/005616.html) on how to do so.

Instantbird currently lacks a core feature to turn it into the Tor Messenger: support for the [OTR protocol](https://otr.cypherpunks.ca/) for encrypted chat. Now is thus a good time to gather usability issues in existing OTR clients.

Mike Perry [kicked off the discussion](https://lists.torproject.org/pipermail/tor-dev/2013-October/005636.html) by pointing out several deficiencies regarding problems with multiple clients, key management issues, and other sub-optimal behaviour.

Ian Goldberg — original author of the pervasive OTR plugin for Pidgin — [pointed out](https://lists.torproject.org/pipermail/tor-dev/2013-October/005640.html) that at least one of the behaviour singled out by Mike was “done on purpose. The thing it’s trying to prevent is that Alice and Bob are chatting, and Bob ends OTR just before Alice hits Enter on her message. If Alice’s client went to ‘Not private’ instead of ‘Finished’, Alice’s message would be sent in the clear, which is undesirable. Switching to ‘Finished’ makes Alice have to actively acknowledge that the conversation is no longer secure.”

This tradeoff is a good example of how designing usable and secure user interfaces can be hard. Usability, in itself, is an often overlooked security feature. Now is a good time to contribute your ideas!

# Tor Help Desk Roundup

The Tor Help Desk continues to be bombarded with help requests from users behind university proxies who cannot use ORPort bridges or the Pluggable Transports Browser to circumvent their network’s firewall. Although the cases are not all the same, bridges on port 443 or port 80 do not always suffice to circumvent such proxies.

Ubuntu 13.10 (Saucy Salamander) was released this week. One user reported their Tor Browser Bundle behaving unusually after updating their Ubuntu operating system. This issue was resolved by switching to the Tor Browser Bundle 3. Another user asked when Tor APT repositories would have packages for Saucy Salamander. Since then, packages for the latest version of Ubuntu have been made available from the usual deb.torproject.org.

# Miscellaneous news

Tails has issued a [call for testing](https://tails.boum.org/news/test_0.21-rc1/) of its upcoming 0.21 release. The new version contains two security fixes regarding access to the Tor control port and [persistent settings](https://git-tails.immerda.ch/tails/plain/wiki/src/doc/first_steps/persistence/upgrade.mdwn?h=bugfix/safer-persistence) among [other improvements and package updates](https://git-tails.immerda.ch/tails/plain/debian/changelog?id=0.21-rc1). “Test wildly!” as the Tails team wrote.

Andrew Lewman was invited to speak at [SECURE Poland 2013](http://www.secure.edu.pl/) and sent a [report on his trip](https://lists.torproject.org/pipermail/tor-reports/2013-October/000364.html) to Warsaw.

Tails developers are [looking for Mac and PC hardware with UEFI](https://tails.boum.org/news/Mac_and_PC_UEFI_hardware_needed/). If you have some spare hardware, please consider a donation!

Ximin Luo has been the first to create a [ticket with 5 digits](https://bugs.torproject.org/10000) on Tor tracker. At the current rate, ticket #20000 should happen by the end of 2015… Or will the project’s continued growth make this happen sooner?

Roger Dingledine [reported](https://lists.torproject.org/pipermail/tor-reports/2013-October/000365.html) on his activities for September and October. Arturo Filastò also [reported](https://lists.torproject.org/pipermail/tor-reports/2013-October/000366.html) on his September.

Runa Sandvik [continues her work](https://lists.torproject.org/pipermail/tor-dev/2013-October/005649.html) on the new, more comprehensible Tor User Manual. The first draft [is already out](https://bugs.torproject.org/5811). Please review and contribute.

Aaron published a branch with his work on a [Tor exit scanner based on OONI](https://github.com/TheTorProject/ooni-probe/tree/feature/tor_test_template).

* * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, dope457, George Kadianakis, Philipp Winter and velope.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

