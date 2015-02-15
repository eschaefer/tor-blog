---
layout: post
title: "Tor Weekly News — September 24th, 2014"
permalink: tor-weekly-news-—-september-24th-2014
date: 2014-09-24 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the thirty-eighth issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

The EFF concludes its 2014 Tor Challenge
========================================

As Tor Weekly News [reported](https://lists.torproject.org/pipermail/tor-news/2014-June/000049.html) in June, over the last few months the Electronic Frontier Foundation has been holding its second Tor Challenge to improve the strength and diversity of the Tor network by inspiring people to run Tor relays. The 2014 Challenge is now over, and Rainey Reitman of the EFF posted [some thoughts](https://www.eff.org/deeplinks/2014/09/tor-challenge-inspires-1635-tor-relays) on the campaign and its outcome.

1635 Tor relays (including 326 exit relays) were started up or had their capacity increased as part of the 2014 Tor Challenge, compared to 549 at the end of the last campaign in 2011. As Rainey wrote, this number “far exceeded our hopes”; the success can be attributed to a coordinated promotional effort by the EFF, the Free Software Foundation, the Freedom of the Press Foundation, and the Tor Project, as well as to “the 1,000 individuals who cared enough to help contribute bandwidth to the Tor network.” Thanks to everyone who participated!

It’s important to remember, though, that new relays only benefit Tor users as long as they stay running. Advice and support from experienced relay operators can always be found on the \#tor IRC channel or the [tor-relays mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-relays); if you missed out on the Tor Challenge this year but still want to contribute to a stronger, more stable Tor network, take a look at the [Tor website](https://www.torproject.org/docs/tor-doc-relay) for advice on how to get started.

Guardiness and Tor’s directory authorities
==========================================

When a Tor relay is first assigned the Guard flag by the directory authorities (or “dirauths”) it sees a dip in the amount of traffic passing through it, because Guard capacity is a scarce resource on the Tor network and, as Roger Dingledine explained [last year](https://blog.torproject.org/blog/lifecycle-of-a-new-relay), “all the rest of the clients back off from using you for their middle hops, because when they see the Guard flag, they assume that you have plenty of load already from clients using you as their first hop”, an assumption which is only correct after clients have had enough opportunity to select the new guard. With the recent move to single entry guards, an even longer period of time may pass before a young guard can be selected as a first hop by old clients.

“Guardiness”, or GuardFraction, is a [proposed measurement](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/236-single-guard-node.txt#l101) to let dirauths, and therefore clients, work out how much of a relay’s capacity is being used for first hops by clients, and how much for second and third hops, by finding the fraction of recent consensuses in which the relay has been given the Guard flag; the “dead period” following the assignment of the flag can then be avoided. George Kadianakis [published](https://lists.torproject.org/pipermail/tor-dev/2014-September/007489.html) an analysis of ways in which dirauths’ votes could be extended to include this guardiness measurement, taking into account the time and effort required to parse large numbers of Tor consensuses very quickly. The initial proposal was to ask dirauths to run a script each hour that would extract the data required for parsing into “summary files”: Sebastian Hahn [asked](https://lists.torproject.org/pipermail/tor-dev/2014-September/007526.html) how this measure might fail in different situations, and Peter Palfrader [suggested](https://lists.torproject.org/pipermail/tor-dev/2014-September/007490.html) that loading every consensus into a database for later querying might be more efficient.

“This feature is by far the trickiest part of prop236 (guard node security) and I wanted to inform all dirauths of our plan and ask for feedback on the deployment procedure”, wrote George. If you have any comments to add to the discussion so far, please send them to the [tor-dev mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-dev).

Miscellaneous news
==================

The Tails team wants to make sure that all the Debian packages on which Tails relies are “in good shape” before Jessie, the next Debian release, is frozen on 5th November. To that end, the team called for testing both of the [software itself](https://mailman.boum.org/pipermail/tails-testers/2014-September/000071.html) and its [translations](https://mailman.boum.org/pipermail/tails-l10n/2014-September/001553.html) — if you’d like to help, find full instructions and links to the “barely-working” experimental disk images in the announcements.

[meek](https://trac.torproject.org/projects/tor/wiki/doc/meek), the pluggable transport that routes Tor traffic through platforms which are “too big to block”, now works with Microsoft Azure in addition to the already-supported Google App Engine and Amazon Web Services. David Fifield [posted](https://lists.torproject.org/pipermail/tor-dev/2014-September/007525.html) the announcement, which contains instructions for those who want to start using the new front domain.

Sebastian Hahn [announced](https://lists.torproject.org/pipermail/tor-talk/2014-September/034898.html) that gabelmoo, the Tor directory authority which he administers, has moved to a new IP address. “You should not notice any kind of disturbance from this, and everything should continue to work as normal.”

Released in December 2013, the SafePlug is a \$49 router that promises its users “complete security and anonymity” online by sending all of their traffic through Tor. Annie Edmundson from Princeton University released a [summary](https://freedom-to-tinker.com/blog/annee/security-audit-of-safeplug-tor-in-a-box/) of [research presented during FOCI’14](https://www.usenix.org/system/files/conference/foci14/foci14-edmundson.pdf) in which the authors point out several security problems in the implementation of the SafePlug administration interface, and also highlight other structural issues. “The most crucial problem with a torifying proxy is that it uses a bring-your-own-browser system, as opposed to a hardened browser, and therefore is susceptible to browser-based privacy leaks. This is why it’s better to use the Tor Browser Bundle […]”, wrote Annie.

The upcoming Tor Messenger is based on [Instantbird](http://instantbird.com/). One key feature that was identified as missing in the latter is support for [Off-the-Record encryption](https://otr.cypherpunks.ca/). After months of discussions and reviews to determine the right programming interface, Arlo Breault got the necessary core [modifications](https://hg.mozilla.org/comm-central/rev/e2c85d70fda2) [merged](https://hg.mozilla.org/users/florian_queze.net/purple/rev/6550fcf407f0).

Roger Dingledine wrote up a [walkthrough](https://trac.torproject.org/projects/tor/wiki/doc/TorControlPortWalkthrough-HS) of the controller events you might see when accessing Tor hidden services. “In theory the controller events should help you understand how far we got at reaching a hidden service when the connection fails. In practice it’s [a bit overwhelming](https://bugs.torproject.org/13206)”.

In the first message posted to the recently-created [onionoo-announce mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/onionoo-announce), Karsten Loesing [explained](https://lists.torproject.org/pipermail/onionoo-announce/2014/000000.html) a minor improvement that should allow Onionoo clients to determine when they need to be upgraded to a new protocol version.

Leiah, whose design work has featured on many of Tor’s company publications, [posted](https://bugs.torproject.org/13117) a mock-up of a possible new look for the Tor blog.

Patrick Schleizer [announced](https://lists.torproject.org/pipermail/tor-talk/2014-September/034909.html) the release of version 9 of Whonix, the anonymous operating system based on Tor, Debian, and security-by-isolation.

Tor help desk roundup
=====================

The help desk has been asked how to configure a VPN to prevent a website from learning that a user is using Tor. We consider positioning a VPN between one’s exit node and the destination site to be totally unsafe, and not much more anonymous than using a VPN without Tor. By design, Tor [allows the destination site to know](https://www.torproject.org/docs/faq.html.en#HideExits) that a visitor is using Tor. The better solution is to email the website owner and ask them to stop blocking Tor. The longer-term solution is that Tor needs someone willing to coordinate with websites to design [engagement solutions](https://blog.torproject.org/blog/call-arms-helping-internet-services-accept-anonymous-users) that work for Tor users and for big websites.

News from Tor StackExchange
===========================

Jobiwan has a machine on their network which should act as a SOCKS proxy. When Tor Browser is configured to use this proxy, it complains that [Tor is not working in this browser](https://tor.stackexchange.com/q/4173/88). However, Jobiwan is able to visit hidden services with these settings, and wants to know why this message is printed and if it is safe to use Tor Browser this way. Do you know a good answer to this question? If so, please share your thoughts.

Andy Smith asks if [slow relays are useful](https://tor.stackexchange.com/q/4050/88) for the Tor network. Roya suggests that a large number of slow relays is better than a small number of fast relays, at least anonymity-wise, because this helps to grow diversity in the network and makes it harder for an attacker to deanonymize users. On the other hand, user194 and Relay Operator write that a slow relay does not provide much benefit for the network. They recommend spending a few dollars more to rent a fast virtual server.

Easy development tasks to get involved with
===========================================

The tor daemon has a SafeLogging configuration option that removes all potentially sensitive parts of log messages and replaces them with “[scrubbed]”. However, this option does not cover hidden services operated by the tor daemon. Extending this option involves scanning through some code, but Nick says it could be some interesting code; if you’re up to reading and patching some C code and then reading some (hopefully scrubbed) logs, this ticket may be for you. Be sure to post your branch for review on the [ticket](https://bugs.torproject.org/2743).

* * * * *

This issue of Tor Weekly News has been assembled by harmony, Lunar, qbi, Matt Pagan, Karsten Loesing, Arlo Breault, and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the project page [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
