---
layout: post
title: "June 2008 Progress Report"
permalink: blog/june-2008-progress-report
date: 2008-07-23
author: phobos
category: blog
tags: ["bridges", "openssl", "progress report", "tor", "tor browser bundle", "translations", "vidalia"]
---

Torbutton 1.2.0rc1 (released June 1), the first release candidate for the next stable series of the security-enhanced Torbutton Firefox extension, features functional support for Firefox 3. However, this support has not been extensively tested. In particular, timezone masking does not work at all. The workaround is to manually set the environment variable 'TZ' to 'UTC' before starting Firefox. This works on both Linux and Windows:
 [http://archives.seul.org/or/talk/Jun-2008/msg00044.html](http://archives.seul.org/or/talk/Jun-2008/msg00044.html "http://archives.seul.org/or/talk/Jun-2008/msg00044.html")

Tor 0.2.0.27-rc (released June 3) adds a few features we left out of the earlier release candidates. In particular, we now include an IP-to-country GeoIP database, so controllers can easily look up what country a given relay is in, and so bridge relays can give us some sanitized summaries about which countries are making use of bridges. (See proposal 126-geoip-fetching.txt for details.)
 [http://archives.seul.org/or/talk/Jun-2008/msg00055.html](http://archives.seul.org/or/talk/Jun-2008/msg00055.html "http://archives.seul.org/or/talk/Jun-2008/msg00055.html")

Torbutton 1.2.0rc2 (released June 8) features a fix for an annoying bug on MacOS, and adds much clamored for options to start Firefox in a specific Tor state:
 [http://archives.seul.org/or/talk/Jun-2008/msg00103.html](http://archives.seul.org/or/talk/Jun-2008/msg00103.html "http://archives.seul.org/or/talk/Jun-2008/msg00103.html")

Tor 0.2.0.28-rc (released June 13) fixes an anonymity-related bug, fixes a hidden-service performance bug, and fixes a bunch of smaller bugs.
 [http://archives.seul.org/or/talk/Jun-2008/msg00165.html](http://archives.seul.org/or/talk/Jun-2008/msg00165.html "http://archives.seul.org/or/talk/Jun-2008/msg00165.html")

Tor 0.2.1.1-alpha (released June 13) fixes a lot of memory fragmentation problems that were making the Tor process bloat especially on Linux; makes our TLS handshake blend in better; sends "bootstrap phase" status events to the controller, so it can keep the user informed of progress (and problems) fetching directory information and establishing circuits; and adds a variety of smaller features. [http://archives.seul.org/or/talk/Jun-2008/msg00185.html](http://archives.seul.org/or/talk/Jun-2008/msg00185.html "http://archives.seul.org/or/talk/Jun-2008/msg00185.html")

Vidalia 0.1.4 (released June 13) adds a bootstrap progress bar, UPnP support, a new set of freely licensed GUI icons, and fixes a few bugs.
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.4/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.4/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.4/CHANGELOG")

The Tor Browser Bundle 1.1.0 (released June 13) replaces startup batch script with application (RelativeLink) so there is a helpful icon, optionally installs Pidgin (for Tor IM Browser Bundle), optionally uses WinRAR to produce a self-extracting split bundle, and includes upgraded versions of Tor, Vidalia, and Torbutton.
 [https://svn.torproject.org/svn/torbrowser/trunk/README](https://svn.torproject.org/svn/torbrowser/trunk/README "https://svn.torproject.org/svn/torbrowser/trunk/README")

Tor 0.2.1.2-alpha (released June 20) includes a new "TestingTorNetwork" config option to make it easier to set up your own private Tor network; fixes several big bugs with using more than one bridge relay; fixes a big bug with offering hidden services quickly after Tor starts; and uses a better API for reporting potential bootstrapping problems to the controller.
 [http://archives.seul.org/or/talk/Jun-2008/msg00247.html](http://archives.seul.org/or/talk/Jun-2008/msg00247.html "http://archives.seul.org/or/talk/Jun-2008/msg00247.html")

Vidalia 0.1.5 (released June 21) switches Vidalia's internal string representation so it can use the new Pootle-based translation system.
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.5/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.5/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.5/CHANGELOG")

Torbutton 1.2.0rc3 and 1.2.0rc4 (both released June 27) provide improved addon compatibility, better preservation of Firefox preferences that we touch, fixing issues with Tor toggle breaking for some option combos, and an improved 'Restore Defaults' button.
 [https://torbutton.torproject.org/dev/CHANGELOG](https://torbutton.torproject.org/dev/CHANGELOG "https://torbutton.torproject.org/dev/CHANGELOG")

We finally got around to writing down the details of many of our architecture and technical design changes:

Proposal 137 ("Keep controllers informed as Tor bootstraps") modifies Tor so it keeps Vidalia informed of each "bootstrap phase" -- that is, progress Tor makes at learning directory information, making connections to the network, etc. Now Vidalia has a progress bar on Tor startup that explains what's going on. Further, Tor reports "bootstrap problems" when it believes it's having troubles starting up correctly, and Vidalia can now tell the user. All of this is in as of the Tor 0.2.1.2-alpha release (June 20).
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/137-bootstra...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/137-bootstrap-phases.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/137-bootstrap-phases.txt")

Proposal 138 ("Remove routers that are not Running from consensus documents") modifies the directory "networkstatus consensus" documents so they no longer list relays that are believed to be unusable. They used to list these relays so clients could decide for themselves, but in practice clients just ignored them. This change saves 30% to 40% in download bandwidth for consensus documents. It is included in the 0.2.1.2-alpha release (June 20).
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/138-remove-d...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/138-remove-down-routers-from-consensus.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/138-remove-down-routers-from-consensus.txt")

Proposal 139 ("Download consensus documents only when it will be trusted") tries to make Tor clients better handle the case when new directory authorities have been added to the system, or when directory authorities have changed (for example, this could happen if we have another bug like the one in May that caused us to change keys for half the directory authorities). Now clients specify which directory authorities they trust, so the directory mirrors can give them a consensus document they'll be willing to use. This change is included in Tor 0.2.1.1-alpha, and a bugfix on it was included in Tor 0.2.1.2-alpha.
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/139-conditio...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/139-conditional-consensus-download.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/139-conditional-consensus-download.txt")

Proposal 140 ("Provide diffs between consensuses") is still under development, but is scheduled to be included in the Tor 0.2.1.x tree. The idea is that most parts of the consensus document don't change from one hour to the next, so we can give clients a diff on the previous one rather than a whole new document, changing the size of the document every client must download every few hours from 92KB on average to 13KB on average.
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/140-consensu...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/140-consensus-diffs.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/140-consensus-diffs.txt")

Proposal 141 ("Download server descriptors on demand") is still under discussion, and may not be ready until for inclusion until Tor 0.2.2.x. This is the more detailed version of our "grand scaling plan" first mentioned in April. The idea is to have clients download networkstatus consensus documents as they do now, but rather than preemptively fetching every relay descriptor just in case, they fetch descriptors "just in time" only when they need them. The trick is to keep the bandwidth overhead low while not introducing too many new anonymity attacks e.g. due to leaking which relays you're picking.
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/141-jit-sd-d...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/141-jit-sd-downloads.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/141-jit-sd-downloads.txt")

We've instrumented a Tor client to collect stats on how much bandwidth we use now for directory overhead and how much we'd save with this new approach:
 [http://archives.seul.org/or/dev/Jun-2008/msg00024.html](http://archives.seul.org/or/dev/Jun-2008/msg00024.html "http://archives.seul.org/or/dev/Jun-2008/msg00024.html")

Proposals 142 ("Combine Introduction and Rendezvous Points") and 143 ("Improvements of Distributed Storage for Tor Hidden Service Descriptors") are still in the discussion phase. Their goal is to improve the experience for clients accessing Tor hidden services, both by making the handshake faster and by making hidden service reachability more reliable and more robust.
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/142-combine-...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/142-combine-intro-and-rend-points.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/142-combine-intro-and-rend-points.txt")
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/143-distribu...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/143-distributed-storage-improvements.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/143-distributed-storage-improvements.txt")

The "spoofing Firefox cipher suites and extensions" features are now in the Tor 0.2.1.1-alpha release, meaning they're in the Tor Browser Bundle 1.1.0 release also. From the 0.2.1.1-alpha ChangeLog:
"More work on making our TLS handshake blend in: modify the list of ciphers advertised by OpenSSL in client mode to even more closely resemble a common web browser. We cheat a little so that we can advertise ciphers that the locally installed OpenSSL doesn't know about."

We've done some initial security auditing (though there's always room for more, and we plan to do some more concrete auditing in July).

Nick also wrote some early thoughts on doing pass-through to an Apache server to improve scanning resistance:
 [http://archives.seul.org/or/dev/Jun-2008/msg00014.html](http://archives.seul.org/or/dev/Jun-2008/msg00014.html "http://archives.seul.org/or/dev/Jun-2008/msg00014.html")

The Tor Browser Bundle 1.1.0 (released June 13) replaces startup batch script with application (RelativeLink) so there is a helpful icon, optionally installs Pidgin (for Tor IM Browser Bundle), optionally uses WinRAR to produce a self-extracting split bundle, and includes upgraded versions of Tor, Vidalia, and Torbutton.

We also looked into running two Firefoxes in parallel:
 [https://svn.torproject.org/svn/torbrowser/trunk/docs/two-firefox.txt](https://svn.torproject.org/svn/torbrowser/trunk/docs/two-firefox.txt "https://svn.torproject.org/svn/torbrowser/trunk/docs/two-firefox.txt")
and we even hacked in some Torbutton fixes that will come out in version 1.2.0rc3 that should get us closer:
 [http://archives.seul.org/or/cvs/Jun-2008/msg00213.html](http://archives.seul.org/or/cvs/Jun-2008/msg00213.html "http://archives.seul.org/or/cvs/Jun-2008/msg00213.html")

Speaking of which, we also hacked in another feature in Torbutton 0.1.2rc2, to add a "locked" mode so Tor Browser Bundle can start Torbutton and not fear that the user will click and disable Tor. I believe TBB 1.1.0 doesn't use this feature yet though.
 [http://archives.seul.org/or/cvs/Jun-2008/msg00186.html](http://archives.seul.org/or/cvs/Jun-2008/msg00186.html "http://archives.seul.org/or/cvs/Jun-2008/msg00186.html")

From the Tor 0.2.1.2-alpha ChangeLog:
"If you have more than one bridge but don't know their digests, you would only learn a request for the descriptor of the first one on your list. (Tor considered launching requests for the others, but found that it already had a connection on the way for $0000...0000 so it didn't open another.) Bugfix on 0.2.0.x."
"If you have more than one bridge but don't know their digests, and the connection to one of the bridges failed, you would cancel all pending bridge connections. (After all, they all have the same digest.) Bugfix on 0.2.0.x."
"If you're using bridges, generate "bootstrap problem" warnings as soon as you run out of working bridges, rather than waiting for ten failures -- which will never happen if you have less than ten bridges."

We put up a new webpage to describe bridges, how to fetch bridge relay addresses, etc:
 [https://www.torproject.org/bridges](https://www.torproject.org/bridges "https://www.torproject.org/bridges")

We also modified the BridgeDB database (that is, the server that runs [https://bridges.torproject.org/](https://bridges.torproject.org/ "https://bridges.torproject.org/") and answers mail to [bridges@torproject.org](mailto:bridges@torproject.org)) to autodetect if the address hitting [https://bridges.torproject.org/](https://bridges.torproject.org/ "https://bridges.torproject.org/") is currently a Tor exit relay, and if so to treat it specially -- that is, we reserve a set of bridge addresses and give those out only to folks coming in over Tor.

The updated BridgeDB version now makes sure to give out at least one bridge that's listed as Stable in the bridge authority's networkstatus document, and at least one bridge that listens on port 443. The goal here is to increase the odds that at least one of the bridges we give the user will be usable even if he's in a tightly firewalled situation.

From the Tor 0.2.0.27-rc ChangeLog:
"Include an IP-to-country GeoIP file in the tarball, so bridge relays can report sanitized summaries of the usage they're seeing."

We finished work on a patch for OpenSSL that will make it keep less buffer space around. Currently fast Tor relays use (waste) as much as 100M of memory in OpenSSL's buffers. This patch was accepted and included in the main OpenSSL tree in June:
 [http://marc.info/?l=openssl-cvs&m=121246471627426&w=2](http://marc.info/?l=openssl-cvs&m=121246471627426&w=2 "http://marc.info/?l=openssl-cvs&m=121246471627426&w=2")

The Vidalia 0.1.4 release has folded the UPnP library and GUI changes into the main Vidalia tree, along with a "test" button to try speaking UPnP at the local router and tell the user whether it worked; these features will be available by default in the 0.2.0.x stable release.

We've put a lot of effort into reducing Tor's memory footprint again. The main issue was a "memory fragmentation" problem in Linux's memory allocator, which was causing Tor servers on Linux to slowly grow without bound. As of Tor 0.2.1.2-alpha, the issue appears to be substantially better. Many more details are here:
 [http://archives.seul.org/or/dev/Jun-2008/msg00001.html](http://archives.seul.org/or/dev/Jun-2008/msg00001.html "http://archives.seul.org/or/dev/Jun-2008/msg00001.html")

From the Tor 0.2.1.2-alpha ChangeLog:
"New TestingTorNetwork config option to allow adjustment of previously constant values that, while reasonable, could slow bootstrapping. Implements proposal 135. Patch from Karsten Loesing."
"When building a consensus, do not include routers that are down. This will cut down 30% to 40% on consensus size. Implements proposal 138."

From the Tor 0.2.1.2-alpha ChangeLog:
"New TestingTorNetwork config option to allow adjustment of previously constant values that, while reasonable, could slow bootstrapping. Implements proposal 135. Patch from Karsten Loesing."
"When building a consensus, do not include routers that are down. This will cut down 30% to 40% on consensus size. Implements proposal 138."

We've added clear user-oriented instructions for the Tor Browser Bundle split-download page:
 [https://www.torproject.org/torbrowser/split.html.en](https://www.torproject.org/torbrowser/split.html.en "https://www.torproject.org/torbrowser/split.html.en")

We're starting work on a "gettor" email auto-responder script that will let people mail [gettor@torproject.org](mailto:gettor@torproject.org) and retrieve a copy of Tor from their mailbox. More info forthcoming in July.

More generally, we have a new [https://www.torproject.org/finding-tor](https://www.torproject.org/finding-tor "https://www.torproject.org/finding-tor") page that describes various mechanisms such as mirrors.

In July we plan to deploy a more automated mechanism for tracking which Tor mirrors are up-to-date.

We have our translation server up and online:
 [https://translation.torproject.org/](https://translation.torproject.org/ "https://translation.torproject.org/")

We have imported the strings from Vidalia, Torbutton, and Torcheck, and we currently have active translations for Spanish, French, German, Italian, Polish, Romanian, Swedish, Turkish, Finnish, Russian, Chinese, and Arabic.

We have a more useful overall translation tutorial here:
 [https://www.torproject.org/translation-portal](https://www.torproject.org/translation-portal "https://www.torproject.org/translation-portal")

And we have internal documentation here for how to deal with the translation stuff behind the scenes:
 [https://svn.torproject.org/svn/tor/trunk/doc/translations.txt](https://svn.torproject.org/svn/tor/trunk/doc/translations.txt "https://svn.torproject.org/svn/tor/trunk/doc/translations.txt")

In July we plan to add the strings for Vidalia's installer; the challenge is that we need to write a script to convert from the "nsh" (nullscript installer language) format to the "po" (preferred by Pootle) format and back.

In July we also expect to see the first version of our "wml to po and back" conversion tool, that will allow us to start putting our website pages into the translation server.

