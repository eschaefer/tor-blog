---
layout: post
title: "September 2008 Progress Report"
permalink: september-2008-progress-report
date: 2008-10-15
author: phobos
category: blog
tags: ["alpha", "bug fixes", "facebook", "lectures", "media articles", "progress report", "rpm", "stable", "tor browser bundle", "vidalia"]
---

 **Releases**  
Vidalia 0.1.9 (released September 2) fixes a big pile of bugs and inconveniences in the earlier releases. This new release marks the first "stable" release of Vidalia, in that we have now branched into a stable (0.1.x) branch and a development (0.2.x) branch.  
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.9/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.9/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.9/CHANGELOG")

Tor 0.2.0.31 (released September 3) addresses two potential anonymity issues, starts to fix a big bug we're seeing where in rare cases traffic from one Tor stream gets mixed into another stream, and fixes a variety of smaller issues.  
 [http://archives.seul.org/or/announce/Sep-2008/msg00000.html](http://archives.seul.org/or/announce/Sep-2008/msg00000.html "http://archives.seul.org/or/announce/Sep-2008/msg00000.html")

Tor 0.2.1.6-alpha (released September 30) further improves performance and robustness of hidden services, starts work on supporting per-country relay selection, and fixes a variety of smaller issues.  
 [http://archives.seul.org/or/talk/Oct-2008/msg00093.html](http://archives.seul.org/or/talk/Oct-2008/msg00093.html "http://archives.seul.org/or/talk/Oct-2008/msg00093.html")

**Circumvention Enhancements**  
From the Vidalia 0.1.9 ChangeLog:  
"Correct the location of the simplified Chinese help files so they will actually load again."

From the Tor 0.2.1.6-alpha ChangeLog:  
"Start work to allow node restrictions to include country codes. The syntax to exclude nodes in a country with country code XX is "ExcludeNodes {XX}". Patch from Robert Hogan. It still needs some refinement to decide what config options should take priority if you ask to both use a particular node and exclude it."  
This feature should allow users in China to specify that they don't want to enter (and/or exit) in China, which in theory could provide stronger security for them.

From the Tor 0.2.1.6-alpha ChangeLog:  
"Allow ports 465 and 587 in the default exit policy again. We had rejected them in 0.1.0.15, because back in 2005 they were commonly misconfigured and ended up as spam targets. We hear they are better locked down these days."  
This feature lets people use GMail with Tor in more flexible ways. This approach is especially important for people trying to send email in certain configurations when their network wants to block or monitor them.

From the Tor 0.2.1.6-alpha ChangeLog:  
"Provide circuit purposes along with circuit events to the controller."  
This change will allow Vidalia to mark circuits in its graphical interface, so users don't get confused about why Tor is building strange circuits in the background when it's really just doing encrypted directory updates.

Matt and Andrew fixed a bug in the Vidalia bundle installer where it tried to detect if Firefox was installed, and unclick the "install Torbutton" option if not, but it didn't detect right. Now if Firefox is missing we put up a warning explanation about how you really ought to be using Tor with Firefox.

We also finally started working on a fix for the Vidalia bug where if Vidalia launches Tor and then crashes later, when you start Vidalia again it'll cryptically ask for your control password.  
 [https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#TorPasswordPro...](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#TorPasswordPrompt "https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#TorPasswordPrompt")  
The first fix is to add a "reset" button to the cryptic message, that kills Tor for you and restarts it, and a "help" button that explains what's going on. These will be out in the next development Vidalia release, hopefully in October.

Camilo Viecco submitted a patch for our RPM spec (build) file to let us build Red Hat / SuSE packages for 64-bit architectures. Andrew included these patches in 0.2.1.6-alpha.

**Advocacy**  
Steven Murdoch taught a lecture at the FIDIS/IFIP Brno Summer School in the Czech Republic.  
 [http://www.buslab.org/SummerSchool2008/](http://www.buslab.org/SummerSchool2008/ "http://www.buslab.org/SummerSchool2008/")  
The presentation was on anti-censorship in general especially on Tor. The students seemed to be interested so he encouraged them to look at Tor and see if there is anything they'd like to work on. We will see if anything comes from that.

We've also been discussing creating a Facebook application, for allowing relay operators to show off that they are running a Tor relay and hopefully encourage more to do so. We think this is a good enough idea to try building it, so Steven has started to do so. As well as adding bling to a user's profile, it would also allow us to map the network of node operators. This is one of the more promising research fields to resist Sybil attacks, see e.g.  
"A Sybil-proof one-hop DHT, Chris Lesniewski-Laas"  
 [http://pdos.csail.mit.edu/papers/sybil-dht-socialnets08.pdf](http://pdos.csail.mit.edu/papers/sybil-dht-socialnets08.pdf "http://pdos.csail.mit.edu/papers/sybil-dht-socialnets08.pdf")

Steven had a related story regarding host-based security from his trainings in Kyrgyzstan and Poland. See also  
 [http://www.f-secure.com/weblog/archives/00001494.html](http://www.f-secure.com/weblog/archives/00001494.html "http://www.f-secure.com/weblog/archives/00001494.html")

Jacob was in a story by Declan about Internet Traceback plans:  
"The Chinese Government, the NSA, Verisign and the ITU are getting together to trace users"  
 [http://news.cnet.com/8301-13578\_3-10040152-38.html](http://news.cnet.com/8301-13578_3-10040152-38.html "http://news.cnet.com/8301-13578\_3-10040152-38.html")

The current issue of Make Magazine has an article on how to use Tor:  
 [http://www.make-digital.com/make/vol15/?pg=102](http://www.make-digital.com/make/vol15/?pg=102 "http://www.make-digital.com/make/vol15/?pg=102")

Helped Kasimir add new Tor controller features so Torstatus can switch to using the v3 directory system:  
 [http://trunk.torstatus.kgprog.com/](http://trunk.torstatus.kgprog.com/ "http://trunk.torstatus.kgprog.com/")

**Ease of Use**  
Steven is working on a new branch of Vidalia that can be used in Tor Browser Bundle, for launching Firefox directly without needing the extra installer scripts called "Firefox Portable". If we get this working, then we can hopefully make progress on running multiple Firefoxes at once (one used for Tor launched by TBB, and one used for non-Tor).  
 [http://trac.vidalia-project.net/browser/vidalia/branches/alt-launcher](http://trac.vidalia-project.net/browser/vidalia/branches/alt-launcher "http://trac.vidalia-project.net/browser/vidalia/branches/alt-launcher")

Jacob Appelbaum worked on a set of instructions for rebranding Firefox, if we decide that we need to call the browser that ships in the Tor Browser Bundle something other than "Firefox". The instructions aren't complete, for example because we need more replacement logos.  
 [https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/branding/](https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/branding/ "https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/branding/")  
It looks like the process of rebranding Firefox 3 is much more straightforward. We have "move to FF3" on our TBB roadmap.

Work by Martin and Kyle on the Tor VM project continues. We have a very early prototype available now:  
 [http://peertech.org/files/demo/testinfo.html](http://peertech.org/files/demo/testinfo.html "http://peertech.org/files/demo/testinfo.html")  
and we hope to give it some more testing and better documentation in the coming months.

**Scalability**  
Joel Reardon, Ian Goldberg's student at Waterloo, has finished the final version of his thesis "Improving Tor using a TCP-over-DTLS tunnel":  
 [http://uwspace.uwaterloo.ca/handle/10012/4011](http://uwspace.uwaterloo.ca/handle/10012/4011 "http://uwspace.uwaterloo.ca/handle/10012/4011")  
We funded this research (along with 4x matching funding from MITACS in Canada) in the hopes that it would move us close enough to being able to switch to a UDP design that we can put it on the Tor development roadmap at some point. Many large challenges remain, but this is also promising work in that it shows that we can expect very serious performance improvements if we go this route.

We've started hunting more thoroughly for solutions to Bug 676:  
 [https://bugs.torproject.org/flyspray/index.php?do=details&id=696](https://bugs.torproject.org/flyspray/index.php?do=details&id=696 "https://bugs.torproject.org/flyspray/index.php?do=details&id=696")  
The issue is that some of the v3 directory authorities are keeping bad statistics on uptimes and stability of relays, which means they are not assigning the Stable or Guard flag correctly to them. The result is that the networkstatus consensus mislabels them, and clients end up not choosing relays or circuits in an efficient manners. This bug not only results in bad performance for clients, but also results in overloading some relays, leading to worse performance.

From the Tor 0.2.1.6-alpha ChangeLog:  
"Implement most of Proposal 152: allow specialized servers to permit single-hop circuits, and clients to use those servers to build single-hop circuits when using a specialized controller. Patch from Josh Albrecht. Resolves feature request 768."  
"Fixed some memory leaks -- some quite frequent, some almost impossible to trigger -- based on results from Coverity."

Several security- and integrity-related bugfixes from Tor 0.2.0.31:  
"Make sure that two circuits can never exist on the same connection with the same circuit ID, even if one is marked for close. This is conceivably a bugfix for bug 779. Bugfix on 0.1.0.4-rc."  
"Relays now reject risky extend cells: if the extend cell includes a digest of all zeroes, or asks to extend back to the relay that sent the extend cell, tear down the circuit. Ideas suggested by rovv."  
"If not enough of our entry guards are available so we add a new one, we might use the new one even if it overlapped with the current circuit's exit relay (or its family). Anonymity bugfix pointed out by rovv."

