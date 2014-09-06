---
layout: post
title: "October 2008 Progress Report"
permalink: blog/october-2008-progress-report
date: 2008-12-02
author: phobos
category: blog
tags: ["auto-updater", "censorship circumvention", "china", "crashes", "farsi", "torbutton", "translations", "vidalia"]
---

 **Design**
We continued enhancements to the Chinese and Russian Tor website translations. We also have a second Chinese translator for the website now, so hopefully we will get more prompt translations there. Our Farsi translation from this summer is slowly becoming obsolete; we should solve that at some point.

We added a new "30 second summary" web page for Tor:
 [https://www.torproject.org/30seconds](https://www.torproject.org/30seconds "https://www.torproject.org/30seconds")
and a new "easy download" page since the original is so complex:
 [https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

In the upcoming Vidalia 0.2.0 development release:
 - Support changing UI languages without having to restart Vidalia.
 - Updated Czech, Polish, Romanian and Turkish translations.

In the upcoming Vidalia 0.1.10 stable release:
 - Add a prettier dialog for prompting people for their control port password that also includes a checkbox for whether the user wants Vidalia to remember the entered password, a Help button, and a Reset button (Windows only).
 - Fix a crash bug that occurred when the user clicks 'Clear' in the message log toolbar followed by 'Save All'.
 - Uncheck the Torbutton options by default in the Windows bundle installer if Firefox is not installed.
 - Add an Windows bundle installer page that warns the user that they should install Firefox, if it looks like they haven't already done so.

It looks like Australia is soon to be joining the ranks of countries with a nationwide filtering regime:
 [http://arstechnica.com/news.ars/post/20081016-net-filters-required-for-a...](http://arstechnica.com/news.ars/post/20081016-net-filters-required-for-all-australians-no-opt-out.html "http://arstechnica.com/news.ars/post/20081016-net-filters-required-for-all-australians-no-opt-out.html")

**Proposals**
We finished the first iteration of our auto-updater spec:
 [https://svn.torproject.org/svn/updater/trunk/specs/thandy-spec.txt](https://svn.torproject.org/svn/updater/trunk/specs/thandy-spec.txt "https://svn.torproject.org/svn/updater/trunk/specs/thandy-spec.txt")
We detail our current auto-updater progress below.

Proposal 156 (Tracking blocked ports on the client side) moves us closer to having clients be able to automatically detect which ports are blocked by their local firewall, so they can bootstrap faster and avoid picking entry guards that aren't reachable for them. The the next steps here are to a) decide if this overall approach is the right approach, and b) revise the patch to be more memory-friendly.
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/156-tracking...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/156-tracking-blocked-ports.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/156-tracking-blocked-ports.txt")

**Advocacy**
Roger started a "Brainstorming about Tor, Germany, and data retention" thread on or-dev:
 [http://archives.seul.org/or/dev/Oct-2008/msg00001.html](http://archives.seul.org/or/dev/Oct-2008/msg00001.html "http://archives.seul.org/or/dev/Oct-2008/msg00001.html")
which eventually turned into a blog post:
 [https://blog.torproject.org/blog/tor%2C-germany%2C-and-data-retention](https://blog.torproject.org/blog/tor%2C-germany%2C-and-data-retention "https://blog.torproject.org/blog/tor%2C-germany%2C-and-data-retention")
as well as a (rejected) 25C3 submission. While I had originally been thinking of the issue in terms of what the ISP of a Tor relay might do, the discussion also came up about what responsibilities a Tor relay operator has with respect to the vague new data retention laws:
 [http://archives.seul.org/or/talk/Oct-2008/threads.html#00126](http://archives.seul.org/or/talk/Oct-2008/threads.html#00126 "http://archives.seul.org/or/talk/Oct-2008/threads.html#00126")
The ultimate result was a clarified perspective on logging inside Tor:
 [http://archives.seul.org/or/talk/Oct-2008/msg00274.html](http://archives.seul.org/or/talk/Oct-2008/msg00274.html "http://archives.seul.org/or/talk/Oct-2008/msg00274.html")

We finally tracked down and solved the mysterious DoS attacks on some of the Tor directory authorities:
 [http://archives.seul.org/or/talk/Oct-2008/msg00056.html](http://archives.seul.org/or/talk/Oct-2008/msg00056.html "http://archives.seul.org/or/talk/Oct-2008/msg00056.html")

We started chatting with Aaron about his "tor2web" proxy idea for letting non-Tor users access hidden service content:
 [http://tor.theinfo.org/](http://tor.theinfo.org/ "http://tor.theinfo.org/")
Somebody should follow up on that more to encourage him to keep at it.

Announced Joel Reardon's thesis on or-talk, and followed up with him to point him to some pieces of anonbib he needs to read more, to tell him about 25C3, and to remind him to publish his new measurement tools lest they become lost to time.

Roger and Karsten got the patches from proposal 155 into svn, and ultimately into the upcoming 0.2.1.7-alpha release. These were the bulk of the October progress for that NLnet project:
 [https://www.torproject.org/projects/hidserv.html.en#Oct08](https://www.torproject.org/projects/hidserv.html.en#Oct08 "https://www.torproject.org/projects/hidserv.html.en#Oct08")

Mike deleted the router-stability file for his directory authority (ides), which should provide temporary relief from bug 696 (which was causing most of the Stable flags to be assigned wrong, and in turn was causing instant messaging and related connections over Tor to be way more flaky than they should be):
 [https://bugs.torproject.org/flyspray/index.php?do=details&id=696](https://bugs.torproject.org/flyspray/index.php?do=details&id=696 "https://bugs.torproject.org/flyspray/index.php?do=details&id=696")
If his router-stability file gets corrupted again, we will have learned something.

Roger, Jacob, and Mike went to the Google Summer of Code Mentor Summit on Oct 24-26 in Mountain View, where we met with a few hundred other GSoC mentors and generally shared information about Tor and how to make good use of summer students working on free software tools.

We also went to dinner with Niels Provos while we were there, to talk about options for the "Google gives you a captcha if you're using Tor" problem. It looks like the right answer there will be for Torbutton to automate some workaround.

Andrew started working with Jillian York, so she can start blogging about the great uses of Tor. More news in November, e.g.
 [https://blog.torproject.org/blog/knight-pulse%2C-jillian%2C-and-tor](https://blog.torproject.org/blog/knight-pulse%2C-jillian%2C-and-tor "https://blog.torproject.org/blog/knight-pulse%2C-jillian%2C-and-tor")

Matt Edman printed Vidalia T-shirts, and sent them out to the folks who have helped work on Vidalia lately. He is also working with a volunteer to clean up the Vidalia website, make new logos, clean up the installer graphics, etc.

Andrew wrote a blog post about anonymity in South Korea:
 [https://blog.torproject.org/blog/online-anonymity-debate-south-korea](https://blog.torproject.org/blog/online-anonymity-debate-south-korea "https://blog.torproject.org/blog/online-anonymity-debate-south-korea")

**Distribution**
Work on the Tor VM project continues. We have a working prototype available now with a walk-through and screenshots:
 [http://peertech.org/files/demo/testinfo.html](http://peertech.org/files/demo/testinfo.html "http://peertech.org/files/demo/testinfo.html")

We plan to release a more public alpha installer in November.

**Scalability**
From the Tor 0.2.1.7-alpha ChangeLog:
"The "ClientDNSRejectInternalAddresses" config option wasn't being consistently obeyed: if an exit relay refuses a stream because its exit policy doesn't allow it, we would remember what IP address the relay said the destination address resolves to, even if it's an internal IP address. Bugfix on 0.2.0.7-alpha; patch by rovv."

**Packaging**
We changed our auto update design from code-name Glider to code-name Thandy, since there's a World of Warcraft cheat program named Glider and it might be a problem for WoW players that try to use Tor.

We've got the PKI and server-side for the auto updater in place. We wrote up a howto walking through how to set up the server-side for the updater, including how to assign roles and generate keys:
 [https://svn.torproject.org/svn/updater/trunk/doc/HOWTO](https://svn.torproject.org/svn/updater/trunk/doc/HOWTO "https://svn.torproject.org/svn/updater/trunk/doc/HOWTO")

We've also decided that Python should work fine for the client-side too. Mike found some techniques to include only exactly the python libs we need, rather than the whole mess of python libs:
 [http://www.py2exe.org/index.cgi/BetterCompression](http://www.py2exe.org/index.cgi/BetterCompression "http://www.py2exe.org/index.cgi/BetterCompression")
and Martin has been messing with saving some additional space by sharing the openssl lib between Tor and Thandy.

The next steps for November are:
 - Roger is going to figure out what PKI we want for the first round of testing (what roles, which keys, how many, who, etc), and deploy a Thandy server so we can put some basic packages on it for testing.
 - Nick is going to finish the client-side of Thandy, in terms of teaching it how to decide which packages and bundles are out of date, and teaching it to download new files and check all the right signatures.
 - Martin is going to package Thandy plus all the right python libs in an easy Windows exe that hopefully isn't too big.
 - Matt Edman is going to add a simple interface to Vidalia for client-side Thandy configuration: stuff like a GUI for telling the user that new updates have appeared and letting the user click "yes, please update me now", etc.
 - Nick and Matt are going to brainstorm more about the interface between Vidalia and Thandy. For example, which program should keep state about the versions of each package that are installed, which program should be responsible for noticing if an install or upgrade attempt fails, etc.

All the steps but the last I think are going to be pretty straightforward. This last step has the most potential pitfalls in it, since we're trying to keep Thandy general and platform-independent yet \*something\* (either Thandy or Vidalia, or something in between) has to tackle all the crazy Windows-specific pieces.

It also looks like we should move the Tor packages and bundles from NSIS (Nullsoft installer) to MSI installer, as MSI can handle versioning and automatic installs (and uninstalls!) more gracefully. It's not yet clear yet if we're going to try to squeeze that installer shift into the November development timeframe.

**Tor Browser Bundle**
We've started to think about moving the Tor Browser Bundle from Firefox 2 to Firefox 3. This will mean we should measure new traces. We'll do it once Torbutton is known to be more stable on Firefox 3, which should happen in early 2009.

