---
layout: post
title: "Tor Weekly News — October 22nd, 2014"
permalink: tor-weekly-news-—-october-22nd-2014
date: 2014-10-22 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the forty-second issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Tor 0.2.5.9-rc is out
=====================

Nick Mathewson [announced](https://lists.torproject.org/pipermail/tor-talk/2014-October/035302.html) what is hopefully the final release candidate in the Tor 0.2.5 series. It contains two enhancements in response to the recent [POODLE attack on OpenSSL](https://blog.torproject.org/blog/new-sslv3-attack-found-disable-sslv3-torbrowser), “even though POODLE does not affect Tor”, as well as a number of other miscellaneous improvements.

Upgrading is especially important for relay operators, as a [remote crash is possible](https://blog.torproject.org/blog/advisory-remote-dos-when-using-tor-recent-openssl-versions-built-no-ssl3-option) when older Tor versions are used with a version of OpenSSL released last week that was built with the “no-ssl3” flag.

As ever, you can download the source code from the [distribution directory](https://www.torproject.org/dist/) and packages should follow shortly.

Tor Browser 4.0 is out
======================

Mike Perry [announced](https://blog.torproject.org/blog/tor-browser-40-released) a major release by the Tor Browser team. Version 4.0 of the secure and anonymous web browser brings several exciting new features to the stable series, including the [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek) censorship-circumvention tool, the secure updater, and a simplified Javascript enabling/disabling process in NoScript, all based on a customized Firefox ESR31. SSLv3 is also disabled, in response to the recent POODLE attack.

This release contains important security fixes, and all users should upgrade as soon as possible. Please note that the new directory structure means users cannot simply extract the new Tor Browser over their existing 3.6.6 directory, and must instead delete the old version entirely. The secure updater still requires manual activation in the “About Tor Browser” menu option, as its security will depend “on the specific CA that issued the [www.torproject.org](http://www.torproject.org "www.torproject.org") HTTPS certificate (Digicert)” until [site-specific certificate pinning](https://bugs.torproject.org/11955) and [signed update files](https://bugs.torproject.org/13379) are implemented. Furthermore, “we still need to improve meek’s performance to match other transports”, wrote Mike, “so adjust your expectations accordingly”.

See Mike’s post for further details and a full changelog, and get your copy of Tor Browser 4.0 from the [distribution directory](https://www.torproject.org/dist/torbrowser/4.0/) or the [download page](https://www.torproject.org/download/download-easy).

Tails 1.2 is out
================

The Tails team put out [version 1.2](https://tails.boum.org/news/version_1.2/) of the anonymizing live operating system. This release replaces the Iceweasel browser with “most of” the regular Tor Browser, and confines several important applications with AppArmor.

I2P will now, like Tor, be started upon network connection if activated with the “i2p” boot parameter, and must be used with the new dedicated I2P Browser. This is also the last Tails release to ship with the now-unmaintained TrueCrypt tool, but the Tails team has already documented the method for [opening TrueCrypt volumes with cryptsetup](https://tails.boum.org/doc/encryption_and_privacy/truecrypt/index#cryptsetup). See the team’s announcement for a full list of changes in the new version.

This is an important security release and all users should upgrade as soon as possible. If you have a running Tails, you should be able to use the incremental updater; if your Tails drive was manually created, or you are a new user, head to the [download page](https://tails.boum.org/download/) for more information.

Miscellaneous news
==================

tagnaq [warned](https://lists.torproject.org/pipermail/tor-talk/2014-October/035285.html) users of [TorBirdy](https://trac.torproject.org/projects/tor/wiki/torbirdy), the torifying extension for the Thunderbird mail client, that a change in Thunderbird 31’s handling of the “reply\_header\_authorwrote” header means that the word “wrote”, translated into the user’s system language, may be inserted before quoted text when replying to emails, leaking the system language to recipients of replies if not removed. Jacob Appelbaum [responded](https://lists.torproject.org/pipermail/tor-talk/2014-October/035305.html) that a new release of TorBirdy addressing this and other issues was imminent.

Arturo Filastò [announced](https://lists.torproject.org/pipermail/ooni-dev/2014-October/000177.html) the release of ooniprobe 1.1.2, containing “two new report entry keys, test\_start\_time and test\_runtime”, and a fix for a bug that “led to ooniresources not working properly”.

evilaliv3 [announced](https://lists.torproject.org/pipermail/tor-dev/2014-October/007641.html) version 3.1.20 of tor2web, an HTTP proxy that enables access to hidden services without a Tor client, for users who do not require strong anonymity. As well as “some networking bugfixing and optimizations”, this release adds a “replace” mode for remotely-fetched blocklists in addition to “merge”, and a feature that allows different hostnames to be mapped to specific hidden services.

Karsten Loesing gave users of Onionoo a “[one-month heads-up](https://lists.torproject.org/pipermail/onionoo-announce/2014/000001.html)” that on or after November 15th, a change to the protocol will let the search parameter “accept base64-encoded fingerprints in addition to hex-encoded fingerprints, nicknames, and IP addresses.” These searches will also return relays whose base64-encoded fingerprints are a partial match for the search string. “If you’re fine with that, feel free to ignore this message and do nothing”, but if not, “you’ll have to filter out those relays locally”.

Following updates to the Tor Project’s website, Sebastian Hahn [drew attention](https://lists.torproject.org/pipermail/tor-mirrors/2014-October/000727.html) to a change in the steps necessary to [run a website mirror](https://www.torproject.org/docs/running-a-mirror). “Please ask if you run into any trouble, and thanks for providing a mirror!”

Inspired by “the Directory Authorities, the crappy experiment leading up to Black Hat, and the promise that one can recreate the Tor network in the event of some catastrophe”, Tom Ritter sent out a [detailed report](https://lists.torproject.org/pipermail/tor-dev/2014-October/007613.html) of issues he encountered while setting up his own Tor network using “full-featured independent tor daemons”, rather than a [network simulator](https://www.torproject.org/docs/faq#PrivateTorNetwork) like Shadow or Chutney.

Cthulhu asked for assistance in overhauling the [GoodBadISP page](https://bugs.torproject.org/13421), which is the starting point for many relay operators around the world. If you have some time to spare, or know some ISPs not yet on the list, it would be greatly appreciated if they could be added to the page. This new effort to reach out to hosting providers could be of great value after years of what Roger Dingledine has [described](https://lists.torproject.org/pipermail/tor-relays/2014-October/005495.html) as a “slash and burn” agriculture model of operating Tor nodes.

Vladimir Martyanov started a [discussion](https://lists.torproject.org/pipermail/tor-dev/2014-October/007619.html) on the question of whether Tor developers should ensure that tor can still be built using compilers that do not support the C99 programming language standard, such as older versions of Microsoft Visual Studio.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, Cthulhu, Roger Dingledine, Karsten Loesing, and Harmony.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
