---
layout: post
title: "Tor Weekly News — March 12th, 2014"
permalink: blog/tor-weekly-news-%E2%80%94-march-12th-2014
date: 2014-03-12
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the tenth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# New release of tor-ramdisk

On March 9th, Anthony G. Basile [released](http://opensource.dyc.edu/pipermail/tor-ramdisk/2014-March/000127.html) a new version of [tor-ramdisk](http://opensource.dyc.edu/tor-ramdisk). Tor-ramdisk is a “micro Linux distribution whose only purpose is to host a Tor server in an environment that maximizes security and privacy. Security is enhanced by hardening the kernel and binaries, and privacy is enhanced by forcing logging to be off at all levels so that even the Tor operator only has access to minimal information. Finally, since everything runs in ephemeral memory, no information survives a reboot […].”

The new version contains Tor 0.2.4.21 and an updated kernel. The main change is the addition of “haveged, a daemon to help generate entropy on diskless systems, for a more cryptographically sound system”.

# Tails launches a logo contest

Do you want to design a piece of artwork that might be seen by hundreds of thousands of people every day? A drawing that will appear on websites, t-shirts, stickers, and software that protects anonymity and privacy?

Tails is starting a [logo contest](https://tails.boum.org/news/logo_contest/) to “give Tails the visual impact it deserves”. Designers have a precise list of requirements to follow that was drawn from past discussions amongst Tails developers. Participants should submit a version of the logo that incorporates the word “Tails” as well as one without text; there is also a list of suggestions for complementary material that would be welcome.

As the Tails team wants to have the logo ready for its upcoming 1.0 release, designers have until March 31st to send their submission. Be quick!

# More status reports for February 2014

The wave of regular monthly reports from Tor project members for the month of February continued, with [Isis Lovecruft](https://lists.torproject.org/pipermail/tor-reports/2014-March/000479.html), [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2014-March/000480.html), [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2014-March/000482.html), and [Kevin P. Dyer](https://lists.torproject.org/pipermail/tor-reports/2014-March/000483.html) releasing their reports this week.

The Tails developers also [reported on their recent progress](https://tails.boum.org/news/report_2014_02/), and Roger Dingledine sent out the [report for SponsorF](https://lists.torproject.org/pipermail/tor-reports/2014-March/000484.html).

# Miscellaneous news

Tails issued the [call for testing for its 0.23 release](https://tails.boum.org/news/test_0.23-rc1/). At the very least, the long awaited features that are MAC spoofing and bridge integration would benefit from wider testing. Enthusiasts are encouraged to [report their findings](https://mailman.boum.org/pipermail/tails-testers/2014-March/000000.html) on the newly-created [tails-tester mailing list](https://tails.boum.org/news/tails-testers/).

Nick Mathewson called on anyone who wants to make Tor relays 3% to 10% faster to review his patches. Have a look at [#9683](https://bugs.torproject.org/9683) and [#9841](https://bugs.torproject.org/9841) if you want to help out.

Testing of the upcoming Tor Browser Bundle 3.6 with pluggable transports included [has started](https://lists.torproject.org/pipermail/tor-qa/2014-March/000346.html).

Many thanks to [Samuel D. Leslie](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000483.html) and [MacLemon](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000484.html) for running mirrors of the Tor Project website!

Karsten Loesing sent out the [minutes of the March 5<sup>th</sup> Weather rewrite online meeting](https://lists.torproject.org/pipermail/tor-dev/2014-March/006400.html).

Alex [reported](https://lists.torproject.org/pipermail/tor-dev/2014-March/006394.html) on an effort to use [ScrambleSuit](http://www.cs.kau.se/philwint/scramblesuit/) with OpenVPN. Ultimately, Yawning Angel identified [a flaw in OpenVPN implementation of the SOCKS protocol](https://lists.torproject.org/pipermail/tor-dev/2014-March/006427.html) and even wrote [a patch](https://github.com/Yawning/openvpn/commit/7474f1acfc) for it.

Sebastian Urbach [announced](https://lists.torproject.org/pipermail/tor-relays/2014-March/004037.html) that [Trying Trusted Tor Traceroutes](http://web.engr.illinois.edu/~das17/tor-traceroute_v1.html) has “reached 100 completed runs from different ip’s (not to mention the multiple runs).” To all participating relay operators, he added: “Thank you very much for your support, you officially rock!”

Tails [reported on their 2013 bounty program](https://tails.boum.org/news/bounties_2013_report/) which led to several changes useful for Tails in upstream software.

Erinn Clark [discovered](https://lists.torproject.org/pipermail/tor-dev/2014-March/006422.html) another fake OpenPGP key with her name and email address. Watch out! The canonical [list of keys used for Tor signatures](https://www.torproject.org/docs/signing-keys.html) is still available on the Tor Project’s website. Also consider [verifying all signatures](https://github.com/isislovecruft/scripts/blob/master/verify-gitian-builder-signatures) for the [reproducible Tor Browser Bundles](https://blog.torproject.org/blog/deterministic-builds-part-one-cyberwar-and-global-compromise).

# Tor help desk roundup

Users have asked us why “About TorBrowser” in the Tor Browser’s Help menu displays the Firefox Logo instead of the Tor logo. This has been a known issue for some time, and fixing it is not as easy it would seem. Relevant bug tickets here are [#2176](https://bugs.torproject.org/2176), [#5194](https://bugs.torproject.org/5194), [#5698](https://bugs.torproject.org/5698), and [#10888](https://bugs.torproject.org/10888).

# News from Tor StackExchange

The last few weeks have seen [several vulnerabilities in the GnuTLS library and the SSL protocol in general](http://www.gnutls.org/security.html#GNUTLS-SA-2014-2). Ivar [wanted to know if the GnuTLS bug affected Tor somehow](https://tor.stackexchange.com/q/1652/88); as Tor uses OpenSSL instead of GnuTLS, the answer is no.

tor\_user found the option “Socks5Proxy” in the Tor manual, and [wanted to know what OR connections are and if this option allows running a Tor node over a SOCKS proxy](https://tor.stackexchange.com/q/1654/88). Jens Kubieziel explained that OR connections are those between two relays or between a client and a relay. While this config option can be used to proxy outgoing OR connections from a relay, it won’t proxy exit streams, and also the relay still needs to be reachable on its advertised ORPort, so it is simplest to say that no, it can’t be used to run a relay over a SOCKS proxy.

* * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, qbi and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

