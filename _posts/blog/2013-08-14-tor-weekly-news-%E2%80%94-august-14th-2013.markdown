---
layout: post
title: "Tor Weekly News — August, 14th 2013"
permalink: blog/tor-weekly-news-%E2%80%94-august-14th-2013
date: 2013-08-14
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the seventh issue of Tor Weekly News, the weekly newsletter that covers what is happening in the fast-paced Tor community.

# New Tor Browser Bundle releases

Mozilla released [Firefox version 17.0.8esr](https://www.mozilla.org/en-US/firefox/17.0.8/releasenotes/) on August 6th, fixing several release critical bugs. Three days later, the stable, beta and alpha versions of the Tor Browser Bundle were updated, along with Tails
(see below).

The stable 2.3.25-11 and 2.4.15-beta-2 also updates HTTPS Everywhere, PDF.js, NoScript and libpng to their latest version. Both bundles had a localization issue which was fixed in the subsequently [released 2.3.25-12 and 2.4.16-beta-1](https://blog.torproject.org/blog/new-tor-02416-rc-packages-and-updated-stable-tor-browser-bundles).

Before updating your browser to the latest version, please pause and admire the [enhanced download page](https://www.torproject.org/projects/torbrowser.html.en#downloads). Kudos to J.M. Todaro for the [design and patches](https://trac.torproject.org/projects/tor/ticket/2109#comment:7) and Andrew for the final integration.

The pluggable transports bundles have also been [updated to 2.4.15-beta-2-pt1](https://blog.torproject.org/blog/pluggable-transports-bundles-2415-beta-2-pt1-firefox-1708esr). Like previously, they contains flash proxy and obfsproxy configured to run by default. Using flash proxy requires a [few extra steps](https://trac.torproject.org/projects/tor/wiki/FlashProxyHowto), as before.

For more experimental matters, the new 3.0 series has seen the [release of alpha3](https://blog.torproject.org/blog/tor-browser-bundle-30alpha3-released). On top of the previous updates, several other small improvements were made: in the new launcher and build system, in fingerprinting fixes and in a [possible anonymity threat for Windows users](https://bugs.torproject.org/9195) coming from cloud anti-virus solutions. This is another opportunity to play with the new build system that should produce byte-to-byte identical results. Please [have a try](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/README) and report any discrepancies with Mike Perry’s builds.

# Tails 0.20 has been released

The [32nd release of Tails is out](https://tails.boum.org/news/version_0.20/). It fixes several security issues, and all users are [advised to upgrade](https://tails.boum.org/security/Numerous_security_holes_in_0.19/).

Among other small bugfixes, minor improvements and translation updates, this release tightens the security around Pidgin — by removing support for protocols other than IRC and XMPP — and restricting access to the ptrace(2) system call for unprivileged users.

[Download](https://tails.boum.org/download/), burn, and [upgrade](https://tails.boum.org/doc/first_steps/usb_upgrade/)!

# New release candidate for the 0.2.4 tor branch

Roger Dingledine announced the [release of tor 0.2.4.16-rc](https://lists.torproject.org/pipermail/tor-talk/2013-August/029344.html), the latest incarnation of the 0.2.4 series. This release include several major and minor bugfixes.

The most important one is probably a crash that can be triggered remotely via badly formatted INTRODUCE1 cells. Roger advises: “Anybody running a hidden service on the experimental 0.2.4.x branch should upgrade”.

Erinn Clark has updated the [beta version of the Tor Browser Bundle](https://blog.torproject.org/blog/new-tor-02416-rc-packages-and-updated-stable-tor-browser-bundles) for a wider audience of testers.

# About Tor Browser usability

[Last week events](https://blog.torproject.org/blog/tor-weekly-news-%E2%80%94-august-7th-2013) sparked a good amount of discussions on Tor Browser usability. Several discussions on tor-talk and in other places revolved around the idea that “JavaScript should be disabled by default”. scarp wrote a [good summary](https://lists.torproject.org/pipermail/tor-talk/2013-August/029266.html) on why it is not so simple: “I understand that JavaScript was enabled globally in the Tor Browser Bundle for usability reasons as well as to prevent browser fingerprinting. […] If the torproject were to disable it by default, that would not ensure that users are protected in the future by similar methods. Sites can be written in a way that if you do not allow JavaScript they simply won’t work at all. If I was writing an exploit I’d do this to frustrate users so hopefully they enable JavaScript and accept my exploit.“ Roger Dingledine also [improved](https://lists.torproject.org/pipermail/tor-talk/2013-August/029364.html) the [relevant question in Tor FAQ](https://www.torproject.org/docs/faq.html.en#TBBJavaScriptEnabled).

One possible solution to satisfy contradicting requirements would be to
add a “ [security slider](https://bugs.torproject.org/9387)” that would allow users to easily trade off
web compatibility over security. The slider would have three or four different positions that would gradually deactivate more and more features of the browser. One has to understand that the “most secure” should probably disable loading of any pictures. This also impacts the Tor Browser anonymity set but this is probably a trade off that can be afforded given the actual size of the Tor Browser user base.

scarp had also pined another big usability problem related to updating: “This exploit wasn’t new. […] Users running the latest Tor Browser Bundle didn’t have any issues as their browsers had been patched. It is inappropriate for a web browser to not be automatically updated.” Nick Mathewson [recapitulated](https://lists.torproject.org/pipermail/tor-dev/2013-August/005228.html) the [latest plan](https://trac.torproject.org/projects/tor/wiki/org/meetings/2013SummerDevMeeting/BundleUpdatePlan) that was discussed during the last summer dev. meeting to simply build upon Firefox update mechanism. The next step is to do a proper review. Hopefully, given it is “mature and widespread” and has been “proven to update Firefox”, we will not “run screaming for the hills” when looking at the disadvantages.

On a more general level, an [unexpected comment](https://twitter.com/BrendanEich/status/364265592112414720) came from Brendan Eich (Mozilla’s chief technology officer) on Twitter: “Maybe we should just adopt, support, and bundle Tor in Firefox...” David Dahl subsequently opened a [bug report in Mozilla’s tracker](https://bugzilla.mozilla.org/show_bug.cgi?id=901614) to discuss a way forward. Mike Perry [commented on a thread on the liberationtech mailing list](https://mailman.stanford.edu/pipermail/liberationtech/2013-August/010650.html): “In short, I am excited by this news, and I look forward to improving our communication and cooperation with Mozilla
on this front.”

# Tails 2013 summit

The Tails team has sent a [report on their 2013 development summit](https://tails.boum.org/news/summit_2013/) for which “a bunch of people spend a dozen days together in July”.

Read the report in full for all the details. Some highlights: task tracking have been [moved to Redmine](https://labs.riseup.net/code/projects/tails), [tasks fit for new contributors](https://labs.riseup.net/code/projects/tails/issues?query_id=112) has been better identified, progress has been made to [move Tails to the current Debian stable release](https://labs.riseup.net/code/issues/6015), the [roadmap](https://labs.riseup.net/code/projects/tails/roadmap) has been updated.

Communication channels are going to change a little bit “to ease involvement of new contributors, to make more workload sharing possible, and to be able to provide better user support”. As a start a new [user support mailing list](https://tails.boum.org/support/tails-support/) was created. Subscribe if you have questions or want to help fellow Tails users.

A lot of discussions revolved around “the growth of the project: given the growing number of users and our super-short release cycle, it is a challenge to keep the project sustainable and maintainable in the mid/long term.” Give the current project exposure, the report rightfully concludes: “Tails is living decisive times, so we expect the next year to be pretty interesting. You can perhaps make the difference, so do not hesitate [joining the dance](https://tails.boum.org/contribute/)!”.

# Three new proposals

On Monday, Nick Mathewson robbed everyone of his “I’m a little teapot” [performance](https://twitter.com/nickm_tor/status/365527533627777025) by releasing the following three new proposals:

[Proposal 219](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/219-expanded-dns.txt) has been written a year ago by Ondrej Mikle. It is currently at draft stage. Its goal is to make Tor support any DNS query type and also support full DNSSEC resolution. The latter is important as it provides “protection against DNS cache-poisoning attacks” but is made tricky given a routine hostname resolution with DNSSEC “can require dozens of round trips across a circuit”.

In [another draft proposal](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/220-ecc-id-keys.txt), Nick Mathewson describes a plan for a smooth transition from the current 1024-bit RSA keys used for router identity and TLS links to [Ed25519-SHA-512](http://ed25519.cr.yp.to/) keys. Several small details still have to be ironed out. This proposal does not address hidden service keys. They will have to be addressed in another proposal once an [agreement has been reached](https://bugs.torproject.org/8106) regarding the best crypto scheme.

Now that the [ntor onionskin handshake](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/216-ntor-handshake.txt) has been implemented in 0.2.4, we could get better forward secrecy by having clients stop sending CREATE\_FAST cells. Nick Mathewson has issued [proposal 221](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/221-stop-using-create-fast.txt) to detail the reasons and the implications of such change.

All these proposals are now up for discussions on the tor-dev mailing list.

# Miscellaneous news

Jens Kubieziel researched how to [get a GnuPG version for Windows](https://lists.torproject.org/pipermail/tor-talk/2013-August/029256.html) in a secure way, something needed for users that would like to properly verify the Tor Browser Bundle signatures on Windows systems.

George Kadianakis wrote on [how to deploy your very own pluggable transport](https://lists.torproject.org/pipermail/tor-dev/2013-August/005231.html) explaining what to do before, while and after coding a new pluggable transport. Given they were designed to be “pluggable”, “it should be easy to write new [ones]”. So be sure to read these advices and start experimenting!

A new round of GSoC reports arrived to the tor-dev mailing list: Johannes Fürmann about [EvilGenius](https://lists.torproject.org/pipermail/tor-dev/2013-August/005237.html), Cristian-Matei Toader about [Tor capabilities](https://lists.torproject.org/pipermail/tor-dev/2013-August/005238.html), Hareesan about the [Steganography Browser Extension](https://lists.torproject.org/pipermail/tor-dev/2013-August/005243.html), and Kostas Jakeliunas about the [searchable metrics archive](https://lists.torproject.org/pipermail/tor-dev/2013-August/005244.html). All of them seems to be making good progress. Let’s wish them success for the last six weeks!

More reports came from the July 2013 wave: the [Tor Help Desk](https://lists.torproject.org/pipermail/tor-reports/2013-August/000310.html) by Runa Sandvik, and [Moritz Bartl](https://lists.torproject.org/pipermail/tor-reports/2013-August/000311.html).

Andrew Lewman gave a talk during the US National Network to End Domestic
Violence’s (NNEDV) annual technology summit. His [presentation](https://svn.torproject.org/svn/projects/presentations/2013-07-30-NNEDV-Presentation.pdf)
covered “a quick overview of Tor, why I’m here talking about domestic
violence and intimate partner abuse, and what we’re doing to help.”. Be
sure to read [his report](https://blog.torproject.org/blog/nnedv-tech-summit-2013-report) in full.

Thanks to [Paul Templeton from CoffsWiFi](https://lists.torproject.org/pipermail/tor-commits/2013-August/060352.html), and [nsane](https://lists.torproject.org/pipermail/tor-commits/2013-August/060583.html) for running new Tor website mirrors.

Several people are trying to assemble localization teams for Tails: [Miriam Matar for Arabic](https://mailman.boum.org/pipermail/tails-l10n/2013-August/000637.html), [irregulator for Greek](https://mailman.boum.org/pipermail/tails-l10n/2013-August/000646.html), [hemlockii for Turkish](https://mailman.boum.org/pipermail/tails-l10n/2013-August/000652.html). Tails policy regarding [website translations](https://tails.boum.org/contribute/how/translate/) specifies that “a team of translators, not just one person, is necessary”, so please join if you can help!

# Help Desk Roundup

Below is a summary of some frequent questions received at the Tor help desk this past week:

Users are frequently confused by the message they receive from GetTor. Currently the Tor Browser Bundle is too large to send over GetTor, so users instead receive three mirrors with a link to a page with all available translations of the Tor Browser Bundle. Many users email the help desk unsure of what this page means or which package they need.

A number of users asked whether or not they needed to disable JavaScript in the Tor Browser Bundle. While the vulnerability in Firefox does not affect the latest Tor Browser Bundle, disabling JavaScript globally will reduce one’s risk of being affected by future JavaScript exploits. Users were asked to choose for themselves between greater protection inside the browser or a browsing experience with more functionality enabled.

* * *

This issue of Tor Weekly News has been assembled by Lunar, malaparte, mttp, Phoul, Tails developers, David Fifield, Nick Mathewson, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

