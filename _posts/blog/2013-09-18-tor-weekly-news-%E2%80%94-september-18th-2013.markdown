---
layout: post
title: "Tor Weekly News — September 18th, 2013"
permalink: tor-weekly-news-%E2%80%94-september-18th-2013
date: 2013-09-18
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the twelfth issue of Tor Weekly News, the weekly newsletter that covers what’s happening in the closely-observed Tor community.

# Official response to QUICK ANT disclosure

Another round of speculation regarding the attitude of state surveillance agencies towards the Tor network was provoked by [a slide](https://people.torproject.org/~andrew/2013-09-10-quick-ant-tor-events-qfd.png) featured in [an edition of the Brazilian current-affairs show “Fantástico”](http://g1.globo.com/fantastico/noticia/2013/09/nsa-documents-show-united-states-spied-brazilian-oil-giant.html), broadcast on September 8th. The slide, leaked as part of the ongoing Snowden disclosures, appeared to show a tab in the [alleged GCHQ](https://twitter.com/ggreenwald/status/378185448293552128) FLYING PIG surveillance interface labelled “Query QUICK ANT — Tor events QFD”. [Users on Reddit](http://www.reddit.com/r/TOR/comments/1m3jum/gchq_tor_events_capture/) and [Twitter](https://twitter.com/jonathanmayer/status/377292928718499841) began to suggest possible attacks on Tor that might be managed through such an interface.

Andrew Lewman posted an [official response](https://blog.torproject.org/blog/tor-nsa-gchq-and-quick-ant-speculation) on the Tor blog in which he reiterated that “it’s not clear what the NSA or GCHQ can or cannot do”, and that well-known theoretical attacks against the Tor network are clearly [described on the project’s FAQ page](https://www.torproject.org/docs/faq.html.en#AttacksOnOnionRouting).

He further added that the tool in question was more likely to involve “some ‘Tor flow detector’ scripts that let them pick Tor flows out of a set of flows they’re looking at” than “anything to do with deanonymizing Tor users, except insofar as they might have traffic flows from both sides of the circuit in their database.”

Finally, he remarked that instead of engaging in speculation based on limited evidence, “we’d rather spend our time developing Tor and conducting research to make a better Tor.”

# Entry guards and linkability

Leif Ryge [pointed out](https://lists.torproject.org/pipermail/tor-dev/2013-September/005423.html) an issue with Tor’s current “entry guards” system, whereby connections entering Tor from different points on the same network could potentially be linked to an individual user based on the three entry nodes selected by that user’s Tor client, which [remain constant for a period of 4-8 weeks](https://blog.torproject.org/blog/lifecycle-of-a-new-relay).

Leif suggested that “assuming this is an accurate assessment, wouldn’t it make sense to maintain separate sets of entry guards for each network that the user connects from?”

Nick Mathewson [replied](https://lists.torproject.org/pipermail/tor-dev/2013-September/005424.html) with an acknowledgement of the problem and a number of reasons why simply generating separate sets of guards might also harm a user’s anonymity: “You would \*not\*, for example, want to maintain a different set of entry guards for every IP that you receive, since if you did, a hostile DHCP server could feed you new IPs until you picked a hostile guard. Similarly, if you are a busy traveler who changes your view of what network you are on hundreds or thousands of times, your chance of picking a hostile guard would rise accordingly.” He also pointed out that “having a record in your state file of every network you have visited is not necessarily the best idea either.”

Nick concluded by mentioning Roger Dingledine’s proposal to lower the number of entry guards selected by a client to one only, “to avoid the property of letting guard choices identify Tor clients”.

# The lifecycle of a new relay: further research needed

In response to some confusion on the part of relay operators over the apparently slow growth in the use of newly-established nodes by clients, Roger Dingledine [posted on the Tor blog](https://blog.torproject.org/blog/lifecycle-of-a-new-relay) a detailed account of how new relays, and the bandwidth they supply, are gradually integrated into the Tor network by directory authorities, bandwidth authorities, and clients themselves. Roger stressed that “the descriptions here are in part anecdotal”.

Roger outlined the four broad phases that define the development of a relay within the network, and finished by offering a number of questions for further research, under a general rubric: “what do these phases look like with real-world data?” If you would like to contribute to the Tor community’s understanding of the interaction between individual relays and the network as a whole, please take a look both at the list of sample questions and at Tor’s publicly-available [archive of metrics data](https://metrics.torproject.org/data.html), and see what you can find!

# Food for thought

<figure></figure>

> Back in the ancient pre-Tor days, at the height of the crypto wars, Ian Goldberg asked me at Financial Crypto in 1998 why we created onion routing. Not entirely facetiously I told him that the fascinating technological problems and the potential to better protect people and their activities was nice, but the real attraction was to create a context where people who were sure they should hate each other were forced to collaborate.

<figcaption style="margin-left: 3em;">— <a href="https://lists.torproject.org/pipermail/tor-talk/2013-September/030097.html">Paul Syverson</a><figcaption><br>
</figcaption></figcaption>

# Tor help desk roundup

The Tor help desk received a request for assistance setting up Thunderbird to work with Tor. Thunderbird can be made to route connections through Tor using the TorBirdy add-on. [Further information](https://trac.torproject.org/projects/tor/wiki/torbirdy#BeforeusingTorBirdy) about using Tor with Thunderbird can be found on the wiki.

Another user wrote to comment on the lack of OpenSUSE support on Tor’s [rpm package page](https://www.torproject.org/docs/rpms.html). There is an [open ticket](https://bugs.torproject.org/4389) concerning this issue, but it hasn’t seen activity for some months. A [new ticket](https://bugs.torproject.org/9718) was opened that addresses this concern more specifically.

# Miscellaneous news

The commitment level for the proposed Tor StackExchange page is hovering at 88%; it needs to reach 100% before it will be accepted into beta. If you think you will be able to contribute by answering questions from current or potential Tor users, [please sign up](http://area51.stackexchange.com/proposals/56447/tor-online-anonymity-privacy-and-security)!

Brian Callahan [alerted](http://lists.nycbug.org/pipermail/tor-bsd/2013-September/000044.html) relay operators running FreeBSD and OpenBSD to the release of ports updated to the new tor 0.2.4.17-rc.

Christian Sturm then [promptly announced](https://lists.torproject.org/pipermail/tor-talk/2013-September/030036.html) the release of updated packages for NetBSD, DragonFly BSD, illumos, Minix, and “other systems potentially using pkgsrc”.

Karsten Loesing [updated tor’s GeoIP database](https://bugs.torproject.org/9714) to the newest version.

Karsten also [published the results](https://trac.torproject.org/projects/tor/ticket/7359#comment:18) of his memory usage test on a version of tor that reports additional statistics, which he conducted using the Shadow network simulator.

Finally, Karsten asked for comments on his [proposal to retire the old method](https://lists.torproject.org/pipermail/tor-dev/2013-September/005443.html) of estimating user numbers on the metrics page over the next few weeks in favor of a more reliable, more efficient system (which has been in beta for some time already), and with it to remove the accumulated data associated with the older method .

Fabio Pietrosanti [announced](https://lists.torproject.org/pipermail/tor-talk/2013-September/030003.html) that the available cipher suites for connections to tor2web.org have been updated to a much stronger set.

Robert [published](https://lists.torproject.org/pipermail/tor-dev/2013-September/005440.html) the results of an investigation into different kinds of round-trip time (RTT) measurement, and their efficiency in building circuits through the Tor network.

George Kadianakis asked for comments on his [early draft](https://lists.torproject.org/pipermail/tor-dev/2013-September/005438.html) of a proposal for different methods of migrating the Hidden Service protocol to a more secure version.

George also [pushed new versions](https://lists.torproject.org/pipermail/tor-dev/2013-September/005441.html) of obfsproxy (0.2.3) and pyptlib (0.0.4).

In the course of a [thread about the size of browser windows posing a fingerprinting threat](https://lists.torproject.org/pipermail/tor-talk/2013-September/030022.html), harmony discovered that users of Ubuntu’s Unity desktop should [disable the “automaximize” behavior](https://bugs.torproject.org/9738), as it can override one of Tor Browser’s anti-fingerprinting measures.

Tom Lowenthal submitted his [monthly status report for August](https://lists.torproject.org/pipermail/tor-reports/2013-September/000339.html).

* * *

This issue of Tor Weekly News has been assembled by harmony, Lunar, dope457, Matt Pagan, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

