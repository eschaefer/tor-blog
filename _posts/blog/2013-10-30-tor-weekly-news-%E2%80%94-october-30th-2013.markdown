---
layout: post
title: "Tor Weekly News — October 30th, 2013"
permalink: blog/tor-weekly-news-%E2%80%94-october-30th-2013
date: 2013-10-30
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the eighteenth issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# A few highlights from this year’s Google Summer of Code

The Google Summer of Code 2013 program is over since the end of September. While Nick, Moritz and Damian [attended the GSoC Mentor Summit](https://lists.torproject.org/pipermail/tor-reports/2013-October/000367.html) at Google’s main campus last week, here are a few highlights from three of the five projects that were carried through the summer.

Robert worked on enhancing Tor’s Path Selection algorithm. [The enhancement](https://bitbucket.org/ra_/tor-rtt) uses active measurements of the Round-Trip-Time of Tor circuits. Rejecting the slowest circuits will improve the average latency of Tor circuits. The results of this work will hopefully be integrated into Tor 0.2.5.x and should then be usable by users. Robert wrote: “Working with the Tor community is very encouraging since there are highly skilled and enthusiastic people around. I am really happy to have made that decision and can definitely recommend doing so to others.”

Johannes Fürmann created a censorship simulation tool that facilitates testing of applications in a simulated network which can be configured and extended to behave like censorship infrastructure in various countries. [EvilGenius](https://github.com/TheTorProject/EvilGenius) can be used to do automated “smoke testing”, i.e. find out if code still works properly if a node in the network manipulates traffic in different ways. Other than that, it can be used to automatically test decentralized network applications. “Overall, working with Tor was a great experience and I hope to be able to work with the Tor community again” said Johannes.

Kostas Jakeliūnas worked on creating a [searchable and scalable Tor Metrics data archive](http://github.com/wfn/torsearch). This required implementing a Tor relay consensus and descriptor search backend that can encompass most of the archival data available (as of now, the currently running backend covers relays from 2008 up until now).

Those curious to browse Tor relay archives — searching for a needle in the very large haystack or just looking around — might enjoy playing with the [current test platform](http://ts.mkj.lt:5555/). It can run powerful queries on the large dataset without query parameter/span restrictions. Many [use cases](https://github.com/wfn/torsearch/blob/master/docs/use_cases_examples.md) are supported — for example, since the newest consensus data is always available, the backend can be used in an ExoneraTor-like fashion.

Together with Karsten Loesing, Kostas hopes to integrate this system with the current [Onionoo](https://www.torproject.org/projects/onionoo.html), hopefully further empowering (and eventually simplifying) the overall Tor Metrics ecosystem.

Kostas described the project as “an interesting and challenging one — a lot of work […] to make it robust and truly scalable.” He also added: “Working with Tor was a great experience: I found the developer community to be welcoming indeed, comprised of many people who are professionals in their field. It should be noted that where there are interesting problems and a clear cause, great people assemble.”

# Collecting data against network level adversaries

“The anonymity of a connection over Tor is vulnerable to an adversary who can observe it in enough places along its route. For example, traffic that crosses the same country as it enters and leaves the Tor network can potentially be deanonymized by an authority in that country who can monitor all network communication.” Karsten Loesing, Anupam Das, and Nikita Borisov began their [call for help to Tor relay operators](https://lists.torproject.org/pipermail/tor-relays/2013-October/003113.html) by stating a problem that has recently attracted some interest by the research community.

The question “which part of the Internet does a Tor relay lie in” is easy enough to answer, but “determining routes with high confidence has been difficult“ so far. The best source of information could come from the relay operators, as Karsten et al. wrote: “To figure out where traffic travels from your relay, we’d like you to run a bunch of ‘traceroutes’ — network measurements that show the paths traffic takes.”

This one-time experiment — for now — is meant to be used by “several researchers, but the leads are Anupam Das, a Ph.D. student at the University of Illinois at Urbana-Champaign, and his advisor Nikita Borisov.”

In order to participate, shell scripts are available which automate most of the process. They have been reviewed with care from several members of the Tor community and are available from [a Git repository](https://bitbucket.org/anupam_das/traceroute-from-tor-relays). Since their initial email, Anupam Das has assembled a [FAQ regarding scope, resource consumption, and other topics](http://web.engr.illinois.edu/~das17/tor-traceroute_v1.html#faq).

Be sure to run the scripts if you can. As Karsten, Anupam, and Nikita concluded, “with your help, we will keep improving to face the new challenges to privacy and freedom online.”

# Tor Help Desk Roundup

Using the Tor Browser Bundle is still proving to be tricky for many Ubuntu users who upgraded from Ubuntu 13.04 to 13.10. The commonly reported error is that users cannot enter text in any of the browser’s text fields, including the URL and search bars. So far this problem appears to be resolved by removing ibus with apt-get before running the Tor Browser. Users who need ibus can try running `export GTK\_IM\_MODULE=xim`, as documented in [Trac ticket #9353](https://bugs.torproject.org/9353).

# Miscellaneous news

David Goulet is asking for a [final round of reviews of his rewrite of torsocks](https://trac.torproject.org/projects/tor/ticket/10007) so it can replace the old implementation. Lunar has [updated the package in Debian experimental](https://lists.torproject.org/pipermail/tor-talk/2013-October/030730.html) to encourage testing. A few portability bugs and a deadlock  has already been ironed out in the process.

The next Tails contributor meeting will be [held on November 6th](https://mailman.boum.org/pipermail/tails-dev/2013-October/003956.html). The present agenda has “firewall exceptions for user-run local services”, “decide what kind of questions go into the FAQ”, among other topics.

Matthew Finkel has sent a [draft proposal](https://lists.torproject.org/pipermail/tor-dev/2013-October/005674.html) with possible solutions for Hidden Services backed by multiple servers. Several comments have been made already, with Nick Mathewson giving a heads-up on the work he has started on merging thoughts and discussions in a [new specification](https://gitweb.torproject.org/user/nickm/torspec.git/blob/refs/heads/rendspec-ng:/rend-spec-ng.txt).

James B. [reported](https://lists.torproject.org/pipermail/tor-talk/2013-October/030800.html) a [tutorial on bsdnow.tv](http://www.bsdnow.tv/tutorials/tor) describing how to setup Tor relays, bridges, exit nodes and hidden services on FreeBSD. Their [last week’s podcast](http://www.bsdnow.tv/episodes/2013_10_23-a_brief_intorduction) called “A Brief Intorduction” features a live demonstration (beginning at 43:52).

The Guardian Project has made a new release of its chat application for Android systems. ChatSecure v12 (previously known has Gibberbot) contains [several new features](https://guardianproject.info/2013/10/24/chatsecure-v12-provides-comprehensive-security-and-a-whole-new-look/) and is fully integrated with Orbot.

* * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, Matt Pagan, Kostas Jakeliūnas, ra, Johannes Fürmann, Karsten Loesing, and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

