---
layout: post
title: "February 2008 Progress Report"
permalink: blog/february-2008-progress-report
date: 2008-03-12
author: phobos
category: blog
tags: ["progress report", "release candidate", "tor", "torbrowser", "torbutton"]
---

Tor 0.2.0.20-rc (released Feb 24) is the first release candidate for the 0.2.0 series. It makes more progress towards normalizing Tor's TLS handshake, makes hidden services work better again, helps relays bootstrap if they don't know their IP address, adds optional support for linking in openbsd's allocator or tcmalloc, allows really fast relays to scale past 15000 sockets, and fixes a bunch of minor bugs reported by Veracode.
 [http://archives.seul.org/or/talk/Feb-2008/msg00279.html](http://archives.seul.org/or/talk/Feb-2008/msg00279.html "http://archives.seul.org/or/talk/Feb-2008/msg00279.html")

Tor 0.2.0.19-alpha (released Feb 9) makes more progress towards normalizing Tor's TLS handshake, makes path selection for relays more secure and IP address guessing more robust, and generally fixes a lot of bugs in preparation for calling the 0.2.0 branch stable.
 [http://archives.seul.org/or/talk/Feb-2008/msg00134.html](http://archives.seul.org/or/talk/Feb-2008/msg00134.html "http://archives.seul.org/or/talk/Feb-2008/msg00134.html")

Torbutton 1.1.13 (released Feb 1), 1.1.14 (released Feb 24), and 1.1.15 (released Feb 26) fix many more potential privacy and identity leaks, mostly based on exploits found by Greg Fleischer. They also add support for automatic updates via the usual Firefox extension upgrade approach.
 [https://torbutton.torproject.org/dev/CHANGELOG](https://torbutton.torproject.org/dev/CHANGELOG "https://torbutton.torproject.org/dev/CHANGELOG")

Work continued toward the upcoming Vidalia 0.1.0 release (which came out March 1): support for launching Firefox and Polipo as supporting applications; support for learning from Tor when the first circuit is ready so it can inform the user; and many other bugfixes including a few security fixes.
 [http://trac.vidalia-project.net/browser/vidalia/releases/vidalia-0.1.0/C...](http://trac.vidalia-project.net/browser/vidalia/releases/vidalia-0.1.0/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/releases/vidalia-0.1.0/CHANGELOG")

The Tor 0.2.0.19-alpha release contained many security-related cleanups based on an anonymously submitted code review from a static analysis tool. The Tor 0.2.0.20-rc release contained even more security-related cleanups, based on an external security analysis and audit by Veracode. Hopefully cleanups at this stage will reduce the number of times we need to push out an urgent new stable "0.2.0" release for security reasons.

From the Tor 0.2.0.19-alpha ChangeLog:
“When connecting to a bridge without specifying its key, insert the connection into the identity-to-connection map as soon as a key is learned. This prevents the Tor user's log from showing a confusing complaint periodically.”
“When our consensus networkstatus has been expired for a while, stop being willing to build circuits using it. Now clients won't give themselves away by behaving uniquely if they start up with an old networkstatus view.”

From the Tor 0.2.0.20-rc ChangeLog:
“Choose which bridge to use proportional to its advertised bandwidth, rather than uniformly at random. This should speed up Tor for bridge users. Also do this for people who set StrictEntryNodes.”

From the Tor 0.2.0.19-alpha ChangeLog:
“If we're a relay, avoid picking ourselves as an introduction point, a rendezvous point, or as the final hop for internal circuits.”
“Directory caches now fetch certificates from all authorities listed in a networkstatus consensus, even when they do not recognize them. This bugfix is particularly important for bridge users, since the bridges are their only contact point for fetching new directory information.”

From the Tor 0.2.0.20-rc ChangeLog:
“Servers that don't know their own IP address should go to the authorities for their first directory fetch, even if their DirPort is off or if they don't know they're reachable yet. This will help them bootstrap better.”

From the Tor 0.2.0.20-rc ChangeLog:
“We were comparing the raw BridgePassword entry with a base64'ed version of it, when handling a "/tor/networkstatus-bridges" directory request. Now compare correctly. This bugfix should allow bridge communities (formerly known as bridge families) to work better. Noticed by Veracode.”

From the Tor 0.2.0.19-alpha ChangeLog:
“Do not include recognizeable strings in the commonname part of Tor's x509 certificates.”

From the Tor 0.2.0.20-rc ChangeLog:
“Enable the revised TLS handshake based on the one designed by Steven Murdoch in proposal 124, as revised in proposal 130. It includes version negotiation for OR connections as described in proposal 105. The new handshake is meant to be harder for censors to fingerprint, and it adds the ability to detect certain kinds of man-in-the-middle traffic analysis attacks. The version negotiation feature will allow us to improve Tor's link protocol more safely in the future.”

From the Tor 0.2.0.20-rc ChangeLog:
“Tune parameters for cell pool allocation to minimize amount of RAM overhead used.”
“Add OpenBSD malloc code from phk as an optional malloc replacement on Linux: some glibc libraries do very poorly with Tor's memory allocation patterns. Pass --enable-openbsd-malloc to get the replacement malloc code.”
“Stop imposing an arbitrary maximum on the number of file descriptors used for extremely high-throughput servers. Bug reported by Olaf Selke; patch from Sebastian Hahn.”

From the Tor 0.2.0.19-alpha ChangeLog:
“Patch from "Andrew S. Lists" to catch when we contact a directory mirror at IP address X and he says we look like we're coming from IP address X. This was causing some Tor relays to test their reachability by testing the wrong address, and never actually publish to the main list.”

We cleaned up the Tor Browser Bundle's webpage and instructions based on feedback from users who were visiting Iran and Burma. Also started preparations to make it easy for our translators to provide an alternate languages. As of March 10, we have English, German, Italian, Polish, and Russian translations. We are working to coordinate an Arabic translation too.
 [https://torbrowser.torproject.org/](https://torbrowser.torproject.org/ "https://torbrowser.torproject.org/")

The new Tor Browser Bundle 0.0.7 (released Feb 8) and 0.0.8 (released Feb 15) include security updates for Firefox (2.0.12), security updates for Torbutton (1.1.13), automate generation of internationalized bundles, allow optional extensions to be placed in build-scripts/extensions, build Polipo with regular expression support (activating the forbiddenFile option), and update Polipo configuration based on suggestions from Incognito's Polipo configuration:
 [https://tor-svn.freehaven.net/svn/torbrowser/branches/stable/README](https://tor-svn.freehaven.net/svn/torbrowser/branches/stable/README "https://tor-svn.freehaven.net/svn/torbrowser/branches/stable/README")

