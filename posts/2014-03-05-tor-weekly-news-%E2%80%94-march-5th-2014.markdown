---
layout: post
title: "Tor Weekly News — March 5th, 2014"
permalink: tor-weekly-news-%E2%80%94-march-5th-2014
date: 03/05/2014
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the ninth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tor 0.2.4.21 is out

Roger Dingledine [announced the release of Tor 0.2.4.21](https://lists.torproject.org/pipermail/tor-talk/2014-March/032242.html), whose major new feature is the forced inclusion of at least one NTor-capable relay in any given three-hop circuit as a defence against adversaries who might be able to break 1024-bit encryption; this feature was first seen in the [latest alpha release](https://lists.torproject.org/pipermail/tor-talk/2014-February/032150.html) (0.2.5.2-alpha) three weeks ago, but is here incorporated into the current stable series.

You can find full details of this release’s other features and bugfixes in Roger’s announcement.

# Tor in Google Summer of Code 2014

As has been the case over the past several years, Tor will once again [be participating](https://www.google-melange.com/gsoc/org2/google/gsoc2014/tor) in Google’s annual Summer of Code program — aspiring software developers have the chance to work on a Tor-related project with financial assistance from Google and expert guidance from a core Tor Project member. Several prospective students have already contacted the community with questions about the program, and Damian Johnson took to the Tor Blog to give a [brief summary of what students can expect from the Summer of Code](https://blog.torproject.org/blog/tor-google-summer-code-2014), and what the Tor Project expects from its students.

In particular, Damian encouraged potential applicants to discuss their ideas with the community on the tor-dev mailing list or IRC channel before submitting an application: “Communication is essential to success in the summer of code, and we’re unlikely to accept students we haven’t heard from before reading their application.”

If you are hoping to contribute to Tor as part of the Summer of Code program, please have a look through Damian’s advice and then, as he says, “come to the list or IRC channel and talk to us!”

# Two ways to help with Tails development

One of the most interesting upcoming additions to the Tails operating system is the ability to thwart attempts at tracking the movements of network-enabled devices by spoofing the MAC address on each boot. As part of the testing process for this new feature, the Tails developers have [released](https://tails.boum.org/news/spoof-mac/) an experimental disk image which turns it on by default, alongside a step-by-step guide to trying it out and reporting any issues encountered. However, as the developers state, “this is a test image. Do not use it for anything other than testing this feature.” If you are willing to take note of this caveat, please feel free to download the test image and let the community know what you find.

Turning to the longer-term development of the project, the team also published a detailed set of guidelines for anyone who wants to help [improve Tails itself by contributing to the development of Debian](https://tails.boum.org/contribute/how/debian/), the operating system on which Tails is based. They include advice on the relationship between the two distributions, tasks in need of attention, and channels for discussing issues with the Tails community; if you are keen on the idea of helping two free-software projects at one stroke, please have a look!

# Monthly status reports for February 2014

The wave of regular monthly reports from Tor project members for the month of February has begun. [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2014-February/000464.html) released his report first, followed by reports from [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-February/000465.html), [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2014-February/000466.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-February/000467.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2014-March/000468.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2014-March/000471.html), [Kelley Misata](https://lists.torproject.org/pipermail/tor-reports/2014-March/000472.html), [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-March/000474.html), [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-March/000475.html), [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2014-March/000476.html), and [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2014-March/000478.html).

Lunar also reported on behalf of [the help desk](https://lists.torproject.org/pipermail/tor-reports/2014-March/000469.html), while Mike Perry did the same on behalf of [the Tor Browser team ](https://lists.torproject.org/pipermail/tor-reports/2014-March/000473.html), and Arturo Filastò for [the OONI team](https://lists.torproject.org/pipermail/tor-reports/2014-March/000477.html).

# Miscellaneous news

Members of the Prosecco research team released a [new attack on the TLS protocol](https://secure-resumption.com/) — dubbed “Triple Handshake” — allowing impersonation of a given client when client authentication is in use together with session resumption and renegotiation. Nick Mathewson published a [detailed analysis of why Tor is not affected](https://lists.torproject.org/pipermail/tor-dev/2014-March/006372.html), and also outlines future changes to make Tor resistant to even more potential TLS issues.

Mike Perry [announced](https://lists.torproject.org/pipermail/tbb-dev/2014-February/000000.html) the start of a weekly Tor Browser developer’s meeting, to be held on `#tor-dev` on `irc.oftc.net`. These meetings are tentatively scheduled for 19:00 UTC on Wednesdays. Details on the format and flow of the meetings can be found on the tor-dev and [tbb-dev](https://lists.torproject.org/cgi-bin/mailman/listinfo/tbb-dev) mailing lists.

Roger Dingledine and Nick Mathewson were among the signatories of an [open letter](https://www.eff.org/deeplinks/2014/02/open-letter-to-tech-companies) published by the EFF which offers ten principles for technology companies to follow in protecting users from illegal surveillance.

Nick Mathewson also [detailed](https://lists.torproject.org/pipermail/tor-dev/2014-February/006341.html) a change in the way that the core Tor development team will use the bugtracker’s “milestone” feature to separate tickets marked for resolution in a given Tor version from those that can be deferred to a later release.

Nick then sent out the [latest in his irregular series of Tor proposal status updates](https://lists.torproject.org/pipermail/tor-dev/2014-February/006342.html), containing summaries of each open proposal, guidance for reviewers, and notes for further work. If you'd like to help Tor’s development by working on one of these proposals, start here!

On the subject of proposals, two new ones were sent to the tor-dev list for review: [proposal 228](https://lists.torproject.org/pipermail/tor-dev/2014-February/006304.html), which offers a way for relays to prove ownership of their onion keys as well as their identity key, and [proposal 229](https://lists.torproject.org/pipermail/tor-dev/2014-February/006340.html) based on Yawning Angel’s unnumbered submission from last week, which concerns improvements to the SOCKS5 protocol for communication between clients, Tor, and pluggable transports.

Nicholas Merrill [wrote](https://mailman.stanford.edu/pipermail/liberationtech/2014-February/013041.html) to the Liberationtech list to announce that xmpp.net now lists [XMPP servers that are reachable over hidden services](https://xmpp.net/reports.php#onions), and that xmpp.net’s server scanner works with these as well.

Patrick Schleizer [announced](https://lists.torproject.org/pipermail/tor-talk/2014-February/032227.html) the release of version 8 of [Whonix](https://www.whonix.org/) — an operating system focused on anonymity, privacy and security based on the Tor anonymity network, Debian and security by isolation. The curious should take a look at the long changelog.

Kelley Misata wrote up an [account](https://lists.torproject.org/pipermail/tor-reports/2014-March/000470.html) of her talk “Journalists — Staying Safe in a Digital World”, which she delivered at the Computer-Assisted Reporting Conference in Baltimore.

Having co-authored [a paper in 2012 on usability issues connected with  
the Tor Browser Bundle](http://petsymposium.org/2012/papers/hotpets12-1-usability.pdf), Greg Norcie [drew attention](https://lists.torproject.org/pipermail/tor-talk/2014-February/032205.html) to a follow-up study named [Why Johnny Can’t Blow the Whistle](http://www.norcie.com/papers/torUSEC.pdf),  which focuses on verifying the conclusions of the earlier tests while exploring a number of other possible usability improvements. The study was, however, carried out before the release of Tor Browser version 3, which improved the bundle’s usability based on earlier suggestions.

Mac OS X users will be thrilled to learn that the next Tor Browser Bundle will be [shipped as a DMG (disk image)](https://people.torproject.org/~mikeperry/images/TBBDMG.png) instead of the [previous unusual .ZIP archive](https://bugs.torproject.org/4261).

David Rajchenbach-Teller from Mozilla [reached out](https://lists.torproject.org/pipermail/tor-talk/2014-February/032204.html) to the Tor Browser developers about their overhaul of the Firefox Session Restore mechanism. This is another milestone in the growing collaboration between the Tor Project and Mozilla.

On the “anonymity is hard” front, David Fifield [reported](https://bugs.torproject.org/10703) a fingerprinting issue on the Tor Browser. Fallback charsets can be used to learn the user locale as they vary from one to another. The next release of the Tor Browser will use “windows-1252” for all locales, as this matches the impersonated “User-Agent” string (Firefox — English version — on Windows) that it already sends in its HTTP headers.

Yawning Angel [called for help](https://lists.torproject.org/pipermail/tor-dev/2014-March/006358.html) in testing and reviewing obfsclient-0.0.1rc2, the second obfsclient release candidate this week: “assuming nothing is broken, this will most likely become v0.0.1, though I may end up disabling Session Ticket handshakes.”

David Fifield [published](https://lists.torproject.org/pipermail/tor-dev/2014-March/006356.html) a guide to patching meek, an HTTP pluggable transport, so that it can be used to send traffic via [Lantern](https://www.getlantern.org/), a censorship circumvention system which “acts as an HTTP proxy and proxies your traffic through trusted friends.”

Fortasse [started a discussion](https://lists.torproject.org/pipermail/tor-talk/2014-February/032220.html) on tor-talk about using HTTPS Everywhere to redirect Tor Browser users to .onion addresses when available. Several people commented regarding the procedure, its security, or how it could turn the Tor Project or the EFF into some kind of registrar.

anonym [has been busy](https://mailman.boum.org/pipermail/tails-dev/2014-February/005023.html) adapting the configuration interface from the Tor Browser — called “Tor Launcher” — to Tails’ needs. Preliminary results can already be seen in the [images built from the experimental branch](http://nightly.tails.boum.org/build_Tails_ISO_experimental/).

Ramo [wrote](https://lists.torproject.org/pipermail/tor-relays/2014-March/004007.html) to announce their [Nagios plugin project](https://github.com/goodvikings/tor_nagios/) to the relay operator community. Lunar pointed out a complementary probe named  
 [check\_tor.py](http://anonscm.debian.org/gitweb/?p=users/lunar/check_tor.git;a=blob;f=README;hb=HEAD).

Virgil Griffith sent a [draft proposal](https://lists.torproject.org/pipermail/tor-dev/2014-February/006344.html) for changes to improve the latency of hidden services when using the “Tor2web” mode. Roger Dingledine [commented](https://lists.torproject.org/pipermail/tor-dev/2014-March/006347.html) that one of the proposed changes actually opened a new research question regarding the actual latency benefits.

David Goulet released the [fourth candidate of his Torsocks rewrite](https://lists.torproject.org/pipermail/tor-dev/2014-March/006371.html). This new version comes after “a big code review from Nick and help from a lot of people contributing and testing”. But more reviews and testing are now welcome!

# Tor help desk roundup

Often users email the help desk when the Tor Browser’s Tor client fails somehow. There are many ways for the Tor Browser to fail in such a way that the Tor log is inaccessible. Since antivirus programs, firewalls, system clock skew, proxied internet connections, and internet censorship have all been known to cause Tor failures, it is not always easy to determine the source of the problem. Thankfully, the Tor Browser team is working on making the logs easier to access in case of failures ( [#10059](https://trac.torproject.org/projects/tor/ticket/10059), [#10603](https://trac.torproject.org/projects/tor/ticket/10603)).

# News from Tor StackExchange

Janice needs to be able to connect from an IP address in a specific city and wanted to know if [Tor can be used to do so](https://tor.stackexchange.com/q/1485/88). Several users suggested that this is not possible with Tor. For city-level IP addresses, it might better to use other services like a proxy or a tunnel, provided one does not require anonymity.

The Tor Browser Bundle sets the default font to Times New Roman 16pt and allows pages to use their own fonts. User joeb likes to change the settings and wondered [how this increases the possibility to fingerprint a user](https://tor.stackexchange.com/q/1619/88). gacar suggested that this will facilitate fingerprinting attacks. Several important sites use [font probing to fingerprint their users](https://www.cosic.esat.kuleuven.be/fpdetective/#results), and changing the default fonts is likely to make a user stand out from the common anonymity set.

Kristopher Ives [wondered](https://tor.stackexchange.com/q/1598/88) if Tor uses some kind of compression. Several users [searched the source code archives for “gzip”](https://gitweb.torproject.org/tor.git?a=search&h=HEAD&st=grep&s=gzip) and found code which deals with directory information. Jens Kubieziel argued that Tor operates on encrypted data and compressing encrypted data usually results in a increase in size, so it makes no sense to compress this data.

Stackexchange uses bounties to award higher reputations to answers. By using this one can attract attention and get better answers or an answer at all. The question about [using DNSSEC and DNScrypt over Tor](https://tor.stackexchange.com/q/1503/88) is probably the first to receive a bounty: an answer to this question would be rewarded with 50 points. However, they have not been earned yet, so if you know an answer, please enlighten the rest of the community.

* * *

This issue of Tor Weekly News has been assembled by harmony, Lunar, qbi, Matt Pagan, Karsten Loesing, Mike Perry, dope457, and Philipp Winter.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

