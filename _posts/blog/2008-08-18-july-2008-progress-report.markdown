---
layout: post
title: "July 2008 Progress Report"
permalink: july-2008-progress-report
date: 2008-08-18
author: phobos
category: blog
tags: ["bridges", "progress report", "proposals", "research", "tor", "torbrowser", "torbutton", "translation", "vidalia"]
---

 **Releases:**

Torbutton 1.2.0rc5 (released July 6) provides improved addon compatibility, better preservation of Firefox preferences that we touch, fixing issues with Tor toggle breaking for some option combos, and an improved 'Restore Defaults' button. This version also features Firefox 3 cookie jar support, and support for storing cookie jars in memory.  
 [http://archives.seul.org/or/talk/Jul-2008/msg00026.html](http://archives.seul.org/or/talk/Jul-2008/msg00026.html "http://archives.seul.org/or/talk/Jul-2008/msg00026.html")

Vidalia 0.1.6 (released July 8) fixes a bug introduced in 0.1.3 that could cause excessive CPU usage or crashing on some platforms; continues to prepare Vidalia's strings for easier translation; adds a Romanian GUI and installer translation; and updated the Farsi, Finnish, French, German, and Swedish translations.  
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.6/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.6/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.6/CHANGELOG")

Tor 0.2.0.29-rc (released July 8) fixes two big bugs with using bridges, fixes more hidden-service performance bugs, and fixes a bunch of smaller bugs.  
 [http://archives.seul.org/or/talk/Jul-2008/msg00038.html](http://archives.seul.org/or/talk/Jul-2008/msg00038.html "http://archives.seul.org/or/talk/Jul-2008/msg00038.html")

Torbutton 1.2.0rc6 (released July 12) features fixes for a nasty history loss bug, an exception during Tor toggle, javascript being disabled in some tabs, better pref handling, and more.  
 [http://archives.seul.org/or/talk/Jul-2008/msg00049.html](http://archives.seul.org/or/talk/Jul-2008/msg00049.html "http://archives.seul.org/or/talk/Jul-2008/msg00049.html")

Tor 0.2.0.30 (released July 15) is the first stable release of the 0.2.0.x branch. The previous stable branch (0.1.2.x) went stable in April of 2007. We are still waiting for Torbutton and Vidalia to stabilize before announcing the Windows and OS X packages on the or-announce announcements  
list. We expect to do that in August.

Tor Browser Bundle 1.1.1 (released July 20) updates Vidalia to release 0.1.6, updates Pidgin Portable to 2.4.3, updates Pidgin OTR plugin to 3.2, updates Tor to 0.2.1.2-alpha, updates Torbutton to 1.2.0rc6, and sets TZ=UTC environment variable in RelativeLink (needed by Torbutton).  
 [https://svn.torproject.org/svn/torbrowser/trunk/README](https://svn.torproject.org/svn/torbrowser/trunk/README "https://svn.torproject.org/svn/torbrowser/trunk/README")

Torbutton 1.2.0 (released July 30) is finally a stable release for the new Torbutton tree that includes application-level privacy protections.  
 [https://svn.torproject.org/svn/torbutton/trunk/src/CHANGELOG](https://svn.torproject.org/svn/torbutton/trunk/src/CHANGELOG "https://svn.torproject.org/svn/torbutton/trunk/src/CHANGELOG")

From the Tor 0.2.0.29-rc ChangeLog:  
"When a hidden service was trying to establish an introduction point, and Tor had built circuits preemptively for such purposes, we were ignoring all the preemptive circuits and launching a new one instead. Bugfix on 0.2.0.14-alpha."  
"When a hidden service was trying to establish an introduction point, and Tor \*did\* manage to reuse one of the preemptively built circuits, it didn't correctly remember which one it used, so it asked for another one soon after, until there were no more preemptive circuits, at which point it launched one from scratch. Bugfix on 0.0.9.x."

The upcoming Tor 0.2.1.3-alpha and 0.2.1.4-alpha releases include more fixes for hidden service performance and robustness, have slightly improved bootstrap status event behavior, and start hunting down a horrible bug that looks like it could leak private information:  
 [https://bugs.torproject.org/flyspray/index.php?do=details&id=779](https://bugs.torproject.org/flyspray/index.php?do=details&id=779 "https://bugs.torproject.org/flyspray/index.php?do=details&id=779")

**Proposals:**

Proposal 145 (Separate "suitable as a guard" from "suitable as a new guard") suggests one approach for separating the role of "is still useful as an entry guard" from "should be an option when choosing a new entry guard". This step will help us load balance over the network better.  
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/145-newguard...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/145-newguard-flag.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/145-newguard-flag.txt")

Proposal 146 (Add new flag to reflect long-term stability) discusses how to ship the Tor client with a set of alternate sources for initial bootstrap directory information. We already have this feature in Tor 0.2.0.x, called the "fallback consensus", but we never enabled it because the Tor client would spend too long trying directory mirrors that were long since gone from the network. This proposal moves us closer to being able to distinguish the more long-term reliable mirrors.  
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/146-long-ter...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/146-long-term-stability.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/146-long-term-stability.txt")

Proposal 147 (Eliminate the need for v2 directories in generating v3 directories) helps wean us off of needing the old deprecated v2 directory design. Currently we only use it to give advance warning to the v3 authorities about relays that haven't heard about yet, so they can fetch information about those relays before the time arrives to make an official vote about their state.  
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/147-prevotin...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/147-prevoting-opinions.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/147-prevoting-opinions.txt")

Proposal 148 (Stream end reasons from the client side should be uniform) describes a simple fix for a potential anonymity flaw in Tor's core protocol for passing explanations from one end of a Tor circuit to the other when an application stream ends.  
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/148-uniform-...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/148-uniform-client-end-reason.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/148-uniform-client-end-reason.txt")

Proposal 149 (Using data from NETINFO cells) starts talking about how to make use of the timestamp and IP address listed in Tor's new NETINFO cells. In theory we can use them to decide if our clock is skewed, and to decide if a traffic analysis man-in-the-middle attack is happening against us. In practice it appears more complex than we expected.  
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/149-using-ne...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/149-using-netinfo-data.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/149-using-netinfo-data.txt")

Proposal 150 (Exclude Exit Nodes from a circuit) allows users to specify which relays should never be used as the last (exit) hop in a circuit. We took the proposal one step further and allowed users to also specify IP addresses and netmasks for which relays to avoid in the exit position.  
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/150-exclude-...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/150-exclude-exit-nodes.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/150-exclude-exit-nodes.txt")

Proposal 151 (Improving Tor Path Selection) is a draft proposal to implement the results of Fallon Chen's Google Summer of Code project. Her plan is to measure the expected time it takes to establish a circuit, and then abandon circuits that take significantly longer than that to form. The assumption is that circuits that take a long time to set up will generally have unacceptably high latency as well.  
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/151-path-sel...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/151-path-selection-improvements.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/151-path-selection-improvements.txt")

Proposal 154 (Automatic Software Update Protocol) starts the discussion of how to let Vidalia automatically manage updates for Tor, Polipo, Vidalia, etc. This is very important for keeping users up to date with respect to security and stability fixes. We will especially aim to do the updates over Tor, a) for privacy, and b) so users who are blocked from the Tor website will still be able to upgrade seamlessly.  
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/154-automati...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/154-automatic-updates.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/154-automatic-updates.txt")

**Research:**

Karsten Loesing's report on 7 ways to improve the performance and robustness of Tor hidden services:  
 [http://freehaven.net/~karsten/hidserv/discussion-2008-07-15.pdf](http://freehaven.net/~karsten/hidserv/discussion-2008-07-15.pdf "http://freehaven.net/~karsten/hidserv/discussion-2008-07-15.pdf")

Four new research papers on Tor came out in July:  
 [http://freehaven.net/anonbib/#loesing2008performance](http://freehaven.net/anonbib/#loesing2008performance "http://freehaven.net/anonbib/#loesing2008performance")  
 [http://freehaven.net/anonbib/#improved-clockskew](http://freehaven.net/anonbib/#improved-clockskew "http://freehaven.net/anonbib/#improved-clockskew")  
 [http://freehaven.net/anonbib/#mccoy-pet2008](http://freehaven.net/anonbib/#mccoy-pet2008 "http://freehaven.net/anonbib/#mccoy-pet2008")  
 [http://freehaven.net/anonbib/#danezis-pet2008](http://freehaven.net/anonbib/#danezis-pet2008 "http://freehaven.net/anonbib/#danezis-pet2008")

We continued evaluating the TBB footprints here:  
 [https://svn.torproject.org/svn/torbrowser/trunk/docs/traces.txt](https://svn.torproject.org/svn/torbrowser/trunk/docs/traces.txt "https://svn.torproject.org/svn/torbrowser/trunk/docs/traces.txt")

In particular, we added a new "Registry modifications" section to that file, describing some new traces that appear to be left behind after operating Tor Browser Bundle, even from the USB key. One of the most worrying is the "user assist" registry key that gets set, and (incredible as it sounds) is obfuscated by rot-13 before being set.

**Ease of Use:**

Tor Browser Bundle 1.1.1 (released July 20) updates Vidalia to release 0.1.6, updates Pidgin Portable to 2.4.3, updates Pidgin OTR plugin to 3.2, updates Tor to 0.2.1.2-alpha, updates Torbutton to 1.2.0rc6, and sets TZ=UTC environment variable in RelativeLink (needed by Torbutton).

The first Incognito (Gentoo-based Tor LiveCD) release of 2008 is also nearing completion, and we expect to see it released in August.

Finally, we contracted to start work on the Tor VM project. The idea is to run a Linux kernel and a Tor client inside a thin VM (like QEMU) on Windows, and then transparently intercept outgoing connections and redirect them into Tor. This approach will a) make proxy-avoiding side-channel and sidejacking attacks less devastating, and b) isolate the Tor client from the rest of the OS to provide a more robust security approach. Current design document is under development at  
 [https://svn.torproject.org/svn/torvm/trunk/doc/design.html](https://svn.torproject.org/svn/torvm/trunk/doc/design.html "https://svn.torproject.org/svn/torvm/trunk/doc/design.html")

**Getting Tor:**

We have established our "gettor" email auto-responder script that lets people mail [gettor@torproject.org](mailto:gettor@torproject.org) and retrieve a copy of Tor from their mailbox. We still need to ponder more usability issues, such as translation.  
 [https://www.torproject.org/finding-tor](https://www.torproject.org/finding-tor "https://www.torproject.org/finding-tor")

We have also automated the process of checking Tor website mirrors: there's a new update-mirrors.pl script in the website directory that generates a list of mirrors ordered by when they last synced with the main website.  
 [https://www.torproject.org/mirrors](https://www.torproject.org/mirrors "https://www.torproject.org/mirrors")

**Translations:**

We have our translation server up and online:  
 [https://translation.torproject.org/](https://translation.torproject.org/ "https://translation.torproject.org/")

We revised our translation tutorial here:  
 [https://www.torproject.org/translation-portal](https://www.torproject.org/translation-portal "https://www.torproject.org/translation-portal")

Users continued to submit updated translations for many different languages.

We continued enhancements to the Chinese and Russian Tor website  
translations. We added Vidalia, Torbutton, and website translations  
into Farsi.

We also added the strings for Vidalia's installer; this required writing several scripts to convert from the "nsh" (nullscript installer language) format to the "po" (preferred by Pootle) format and back.

