---
layout: post
title: "Tor Weekly News — March 26th, 2014"
permalink: tor-weekly-news-%E2%80%94-march-26th-2014
date: 2014-03-26
author: harmony
category: blog
tags: ["tor weekly news"]
---

Welcome to the twelfth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tor 0.2.5.3-alpha is out

Nick Mathewson cut [a new release](https://lists.torproject.org/pipermail/tor-talk/2014-March/032448.html) of the Tor development branch on March 23rd: “Tor 0.2.5.3-alpha includes all the fixes from 0.2.4.21. It contains two new anti-DoS features for Tor relays, resolves a bug that kept SOCKS5 support for IPv6 from working, fixes several annoying usability issues for bridge users, and removes more old code for unused directory formats.”

This release also marks the first step toward the stabilization of Tor 0.2.5, as from now on “no feature patches not already written will be considered for inclusion”.

The source is available at [the usual location](https://www.torproject.org/dist/), as are updated binary packages.

# Tails 0.23 is out…

…but many Tails users are already running it. Now that incremental upgrades have been turned on by default with the previous release, users of Tails on USB sticks have been able to enjoy the process of a smooth upgrade in three clicks.

As always, [the new release](https://tails.boum.org/news/version_0.23/) fixes several [security holes](https://tails.boum.org/security/Numerous_security_holes_in_0.22.1/). That alone should make anyone switch, but the new version finally brings with it two long-awaited features and many small improvements.

Tails will now do “MAC spoofing” by default. To hide the hardware address used on the local network, Tails will now use a randomized address by default. This will help prevent the tracking of one’s geographical location across networks. For more information about MAC spoofing, why it matters, and when it might be relevant to turn it off, be sure to read the very well-written [documentation](https://tails.boum.org/doc/first_steps/startup_options/mac_spoofing/).

Another important feature is the integrated support for proxies and Tor bridges. This should be of immense help to users of Tails on censored networks. The integration is done using the [Tor Launcher extension](https://gitweb.torproject.org/tor-launcher.git), familiar to everyone who has used recent versions of the Tor Browser.

For examples of smaller features and bugfixes: Tor, obfsproxy, I2P, Pidgin and the web browser have been upgraded, a 64-bit kernel is used on most systems to pave the way for UEFI support, documentation is now accessible from the greeter, and the “New identity” option in the browser is available again.

The next Tails release is scheduled for April 29th and will be 1.0. For this important milestone in 5 years of intense work, the Tails team is still looking for a [logo](https://tails.boum.org/news/logo_contest/).

# New Tor Browser releases

The Tor Browser team put out two new releases based on [Firefox 24.4.0esr](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox24.4). [Version 3.5.3](https://blog.torproject.org/blog/tor-browser-353-released) is meant as a safe upgrade for every Tor Browser user. Among other changes, the new version contains an updated Tor, a fix for a potential freeze, a fix for the Ubuntu keyboard issue and a way to prevent disk leaks when watching videos.

On top of the preceding changes, [version 3.6-beta-1](https://blog.torproject.org/blog/tor-browser-36-beta-1-released) is the culmination of a months-long effort to seamlessly integrate [pluggable transports](https://www.torproject.org/docs/pluggable-transports.html) into the Tor Browser. In the network settings, users can now choose “Connect with provided bridges” and select from [“obfs3”](https://gitweb.torproject.org/pluggable-transports/obfsproxy.git/blob/refs/heads/master:/doc/obfs3/obfs3-protocol-spec.txt), [“fte”](https://fteproxy.org/) or [“flashproxy”](https://crypto.stanford.edu/flashproxy/). Entering custom bridges is also supported and will work for direct, obfs2 and obfs3 bridges.

Other usability changes include wording improvements in the connection wizard, translatable Tor status messages, and the use of disk image (DMG) instead of ZIP archives for Mac OS X.

Please upgrade, in any case, and consider helping iron out the remaining issues in the 3.6 branch.

# Miscellaneous news

Since the 3.5 release, “Tor Browser Bundle is more like a standalone browser and less like a bundle”. This led the Tor Browser team to plan to [“rename it to just ‘Tor Browser’ everywhere”](https://bugs.torproject.org/11193).

Thanks to [Berkay](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000491.html) and to [André Schulz](https://lists.torproject.org/pipermail/tor-mirrors/2014-March/000492.html) for running mirrors of the Tor Project website!

Alex [reported](https://lists.torproject.org/pipermail/tor-talk/2014-March/032441.html) an “important case about Tor relay operators” which came to court in Athens, Greece on March 18th. The defendant, a Tor relay operator, was acquitted after proving that the IP address used for criminal activity was in fact a Tor relay.

Connections to Twitter from inside Turkey were [blocked by the Turkish government](http://arstechnica.com/tech-policy/2014/03/after-dns-change-fails-turkish-government-steps-up-twitter-censorship/) on 20th March, leading to [an increase](https://metrics.torproject.org/users.html?graph=userstats-relay-country&start=2014-01-01&end=2014-03-26&country=tr&events=off#userstats-relay-country) in the number of [Tor users there](http://www.bbc.com/news/technology-26714214).

Jacob Appelbaum presented a keynote titled “Free software for freedom, surveillance and you” at [LibrePlanet 2014](http://libreplanet.org/2014/program/sessions.html). The presentation was done remotely from Berlin using Tor and [GStreamer](https://github.com/ioerror/freenote).

James Valleroy wrote to tor-relays asking the best way to configure the FreedomBox as a Tor bridge. Lance Hathaway explained about pluggable transports and Roger Dingledine mentioned the potential issues of relaying a bridge and a hidden service at the same time.

Aymeric Vitte [wrote](https://lists.torproject.org/pipermail/tor-talk/2014-March/032432.html) to tor-talk to mention an implementation of the Tor protocol in JavaScript. Sadly, the project is not free software yet.

A Tor exit operator recently [held an Ask Me Anything](https://pay.reddit.com/r/IAmA/comments/20243q/iaman_operator_of_eight_tor_relays_including_two) on Reddit, which was quite successful, generating over 800 upvotes, 478 comments, and being read by thousands. The most popular questions were focused on how to improve the use of Tor, the legality of exit nodes, discussions on hidden services, the workings of Tor, and many other topics related to privacy and security.

# Tor help desk roundup

Users sometimes want to know how to transfer their bookmarks from an old Tor Browser to an updated one. Mozilla provide instructions on how to do this on their [website](http://support.mozilla.org/en-US/kb/export-firefox-bookmarks-to-backup-or-transfer).

The new Tor Browser releases were again prevented from working properly by WebRoot Internet Security. The error message is “Couldn’t load XPCOM”. Users need to disable WebRoot, whitelist the appropriate Tor Browser files, and more importantly contact WebRoot support to warn them that their product is breaking the Tor Browser and, to the best of Tor support’s knowledge, Firefox stable releases. Ideally, WebRoot should test new releases before harming Tor users. See [#11268](https://bugs.torproject.org/11268) if you want to help.

# News from Tor StackExchange

uighur1984 wanted to [set up a hidden service for their public-facing website](https://tor.stackexchange.com/q/1783/88) and decided that the HiddenServiceDir should be the same like the DocumentRoot of the website. This led to some problems with access rights. Sam Whited clarified that both directories should be separated: the data in the HiddenServiceDir doesn't contain any actual data from the website, but only the keys and other information from the hidden service.

Gondalse shot a video showing policemen torturing a citizen. The release of the video led to a trial, and Gondalse [fears that someone might try to track the owner of the video down](https://tor.stackexchange.com/q/1790/88). Jens Kubieziel pointed out some OPSEC rules, and showed which problems can lead to deanonymization.

* * *
This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, harmony, qbi, Jesse Victors, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

