---
layout: post
title: "Tor Weekly News — May 7th, 2014"
permalink: blog/tor-weekly-news-%E2%80%94-may-7th-2014
date: 2014-05-07
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the eighteenth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tor Browser 3.6 is released

The long-awaited [Tor Browser 3.6 was finally declared stable](https://blog.torproject.org/blog/tor-browser-36-released) on April 29th. Tor Browser 3.6 is the first version to fully integrate pluggable transports, enabling easier access to the Tor network on censored networks. The browser is based on the latest Firefox ESR 24.5.0 and [includes a new round of security fixes](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.5).

When configuring how to access the Tor network, users can now select one of the included list of [obfs3](https://gitweb.torproject.org/pluggable-transports/obfsproxy.git/blob/refs/heads/master:/doc/obfs3/obfs3-protocol-spec.txt) or [fte](https://fteproxy.org/) bridges. Using Flashproxy is also an option, but [often requires further configuration](https://trac.torproject.org/projects/tor/wiki/FlashProxyHowto) on the local firewall and router. Manually specifying [bridges](https://bridges.torproject.org/) is still an option, now with support for the aforementioned pluggable transports.

Many small usability enhancements have been made: Tor error messages are translated, the wording on several dialog windows has been improved based on user feedback, and Mac users now install the browser from the usual disk image format. Turkish localization has also been enabled.

Read the release announcement for a complete changelog. Be sure to [upgrade](https://www.torproject.org/download/download-easy.html)!

# Tails 1.0 is out

“Version 1.0 is often an important milestone that denotes the maturity of a free software project. The first public version of what would become Tails was released on June 23 2009 […]. That was almost five years ago. Tails 1.0 marks the 36th stable release since then.”

The [release announcement](https://tails.boum.org/news/version_1.0/) could have not said it better. On top of the simple idea of having a system entirely running in memory that guarantees Tor usage for all network connections, Tails has been extended with an USB installer, automatic upgrades, persistence, support for Tor bridges, MAC address spoofing, an extensive and translated documentation and [many more features](https://tails.boum.org/doc/about/features/).

Over Tails 0.23, the new version brings security fixes from Firefox and [Tor](https://trac.torproject.org/projects/tor/ticket/11464), an updated I2P, several enhancements to the Tor configuration interface, and the appearance of the [new Tails logo](https://tails.boum.org/promote/logo/).

More details are in the release announcement. For those who have not made use of the integrated updater, time to [download](https://tails.boum.org/download/) the new version!

# Monthly status reports for April 2014

The wave of regular monthly reports from Tor project members for the month of April has begun. [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2014-April/000511.html) released his report first, followed by reports from [Arthur D. Edelstein](https://lists.torproject.org/pipermail/tor-reports/2014-April/000513.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-May/000514.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2014-May/000515.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2014-May/000516.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-May/000517.html), [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2014-May/000518.html), [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-May/000520.html), [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-May/000521.html), [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2014-May/000523.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2014-May/000524.html), [Kevin Dyer](https://lists.torproject.org/pipermail/tor-reports/2014-May/000525.html), [Isis Lovecruft](https://lists.torproject.org/pipermail/tor-reports/2014-May/000527.html), [Kelley Misata](https://lists.torproject.org/pipermail/tor-reports/2014-May/000528.html), [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2014-May/000529.html), and [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2014-May/000530.html).

Lunar also reported on behalf of the [help desk](https://lists.torproject.org/pipermail/tor-reports/2014-May/000512.html), Mike Perry for the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2014-May/000522.html), and Arturo Filastò for the [OONI team](https://lists.torproject.org/pipermail/tor-reports/2014-May/000526.html).

# Miscellaneous news

The Tails developers [warned](https://lists.torproject.org/pipermail/tor-talk/2014-May/032838.html) that two fake public keys have been found bearing email addresses associated with the project; do not trust these keys, or anything they may have been used to sign. You can check [the real keys](https://tails.boum.org/doc/about/openpgp_keys/) used to sign Tails software on the Tails website.

Erinn Clark [alerted](https://lists.torproject.org/pipermail/tor-dev/2014-May/006809.html) users of the [Trac-based Tor wiki](https://trac.torproject.org/) to the fact that a bug (now fixed) made it possible to register an account with an already-taken username, “overwriting the existing user’s password and thereby taking over the account”. “We recommend users try to login and if you find you are unable to do so, you can reset your password” on the [appropriate Trac page](https://trac.torproject.org/projects/tor/reset_password).

Following up on [previous discussions](https://lists.torproject.org/pipermail/tor-dev/2013-October/005556.html) and a [proposal](https://lists.torproject.org/pipermail/tor-dev/2013-October/005674.html) on the topic of how to make hidden services scale, Christopher Baines went on and implemented a [prototype](https://lists.torproject.org/pipermail/tor-dev/2014-April/006788.html), “for one possible design of how to allow distribution in hidden services”. The code and concrete design is up for feedback.

Daniel Martí [sent out](https://lists.torproject.org/pipermail/tor-dev/2014-May/006792.html) a list of proposed revisions — arrived at in discussion with other developers on IRC — to the now slightly outdated proposal 140, which forms the basis of his upcoming Google Summer of Code project to implement consensus diffs and so reduce the amount of information downloaded hourly by Tor clients. Among the proposals are support for microdescriptor consensus diffs and a time limit to prevent the leak of information about when Tor was last used; “ideas about what might be missing or needing an update are welcome”, wrote Daniel.

Alpha releases of Orbot v14 are [now available](https://lists.torproject.org/pipermail/tor-talk/2014-May/032847.html) for testing. They include support for the obfs3 and ScrambleSuit protocols, thanks to [obfsclient](https://github.com/yawning/obfsclient).

Griffin Boyce solicited feedback on the [first release of Satori](https://lists.torproject.org/pipermail/tor-talk/2014-May/032866.html), an “app for Google Chrome that distributes circumvention software in a difficult-to-block way and makes it easy for users to check if it’s been tampered with in-transit.”

Kelley Misata [announced](https://blog.torproject.org/blog/tor-summer-2014-dev-meeting-hosted-mozilla) on the Tor Blog that this year’s Tor Summer Dev Meeting will be held between June 29th and July 4th at the French offices of Mozilla in Paris.

Also on the blog, Andrew Lewman [announced](https://blog.torproject.org/blog/paypal-account-limits-now-resolved) that the temporary limit on donations to the Tor Project through Paypal has now been lifted.

Nicolas Vigier [announced](https://lists.torproject.org/pipermail/tor-qa/2014-May/000405.html) that the Tor Browser test suite will now be run automatically when a new build is ready. The results will be emailed to the tor-qa mailing list.

Nick Mathewson [suggested](https://lists.torproject.org/pipermail/tor-dev/2014-May/006820.html) that [proposal 236](https://gitweb.torproject.org/torspec.git/blob_plain/refs/heads/master:/proposals/236-single-guard-node.txt), which deals with the proposed transition to single guard nodes for Tor clients, should include the retention of multiple guards for directory requests, since “trusting a single source for the completeness and freshness of your directory info is suboptimal.”

Jacob H. Haven, Mikhail Belous, and Noah Rahman each introduced their Tor-related projects for this year’s Google Summer of Code: [Jacob’s project](https://lists.torproject.org/pipermail/tor-dev/2014-May/006808.html) is titled “A Lightweight Censorship Analyzer for Tor”, and aims to “allow non-technical users to monitor censorship of Tor occurring in their country/network”; Mikhail [will work](https://lists.torproject.org/pipermail/tor-dev/2014-May/006817.html) to implement a multicore version of the tor daemon; and Noah [plans](https://lists.torproject.org/pipermail/tor-dev/2014-May/006821.html) on “refactoring Stegotorus more along DRY lines as well as enhancing and updating various handshaking protocols, and getting it ready to merge in upstream changes from its originators at SRI.”

Thanks to [NetCologne](https://lists.torproject.org/pipermail/tor-mirrors/2014-April/000556.html) and [fr33tux](https://lists.torproject.org/pipermail/tor-mirrors/2014-April/000553.html) for running mirrors of the Tor Project website!

Frederic Jacobs invited [comments](https://lists.torproject.org/pipermail/tor-talk/2014-May/032839.html) on an alternative Tor icon designed by a friend “for fun”.

# Tor help desk roundup

Many users alerted the help desk to a [new bug](https://bugs.torproject.org/11658) in Tor Browser 3.6 that prevents users from setting a proxy. Developers have said this bug is related to the introduction of Pluggable Transport support; a new Tor Browser release addressing this issue is expected this week.

# News from Tor StackExchange

Tom Ritter wonders how the [Exit Probability is calculated](https://tor.stackexchange.com/q/2041/88) and wants to know if all values add up to 100 %. If anyone knows a good answer, please don’t hesitate to add it to the question.

user1698 wants to extend the number of Tor relays in a circuit, and asks if it is possible to [have one with 5 or 6 nodes](https://tor.stackexchange.com/q/2039/88). Tom Ritter suggests that this is only possible when one changes the source code. There is another question which deals with [extending the number of nodes in a circuit](https://tor.stackexchange.com/q/103/88): Steven Murdoch warns the user in his answer that under some circumstances it might be possible to de-anonymize a person who is using this technique. Furthermore alaf discusses the performance, throughput and anonymity of longer circuits.

* * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, qbi and the Tails team.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

