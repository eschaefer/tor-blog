---
layout: post
title: "May 2008 Progress Report"
permalink: may-2008-progress-report
date: 2008-06-25
author: phobos
category: blog
tags: ["bridges", "browser bundle", "progress report", "tor", "torbutton", "vidalia"]
---

Tor 0.2.0.26-rc (released May 13) fixes a major security vulnerability caused by a bug in Debian's OpenSSL packages. All users running any 0.2.0.x version should upgrade, whether they're running Debian or not.  
 [http://archives.seul.org/or/talk/May-2008/msg00048.html](http://archives.seul.org/or/talk/May-2008/msg00048.html "http://archives.seul.org/or/talk/May-2008/msg00048.html")

Vidalia 0.1.3 (released May 25) adds a hidden service configuration UI designed and implemented by Domenik Bork, as well as a few other bugfixes.  
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.3/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.3/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.3/CHANGELOG")

The Tor Browser Bundle 1.0.2 (released May 3) and 1.0.3 (released May 16) include upgraded versions of Tor, Vidalia, Torbutton, and Firefox.

We added three new part-time developers in May. We hired Matt Edman as a part-time employee at the beginning of May, to work on Vidalia maintenance, bugfixes, and new features. We also are funding Karsten Loesing to work on making hidden service rendezvous and interaction faster, and Peter Palfrader to work on lowering the overhead of directory requests, especially during bootstrap, which should directly improve the experience for Tor users on modems or cell phones.

Google has agreed to give us some funding to work on auto-update for Windows. Our plan is for Vidalia to look at the majority-signed network status consensus to decide when to update and to what version (Tor already lists what versions are considered safe, in each network status document). We should actually do the update via Tor if possible, for additional privacy, and we need to make sure to check package signatures to ensure package validity. Last, we need to give the user an interface for these updates, including letting her opt to migrate from one major Tor version to the next.

We continued enhancements to the Chinese and Russian Tor website translations. Vidalia also added a Turkish translation.

From the Vidalia 0.1.3 ChangeLog:  
"If we're running Tor >= 0.2.0.13-alpha, then check the descriptor annotations for each descriptor before deciding to do a geoip lookup on its IP address. If the annotations indicate it is a special purpose descriptor (e.g., bridges), then don't do the lookup at all."

"Remove the 'Run Tor as a Service' checkbox. Lots of people seem to be clicking it even though they don't really need to, and we end up leaving them in a broken state after a reboot."

"Only display the running relays in the big list of relays to the left of the network map. Listing a big pile of unavailable relays is not particularly useful, and just clutters up the list."

We worked toward a Torbutton 1.2.0rc1 release candidate, which will include support for Firefox 3 along with a huge pile of privacy-related bugfixes.

We spent much of the first half of May dealing with a surprise massive security vulnerability in a crypto library that comes with Debian:  
 [http://archives.seul.org/or/announce/May-2008/msg00000.html](http://archives.seul.org/or/announce/May-2008/msg00000.html "http://archives.seul.org/or/announce/May-2008/msg00000.html")

You can read a more detailed explanation of the effects of the flaw here:  
 [https://blog.torproject.org/blog/debian-openssl-flaw%3A-what-does-it-mea...](https://blog.torproject.org/blog/debian-openssl-flaw%3A-what-does-it-mean-tor-clients%3F "https://blog.torproject.org/blog/debian-openssl-flaw%3A-what-does-it-mean-tor-clients%3F")

Part of dealing with the flaw meant doing some quick design work so we could let new Tor users be safe without making it so old Tor users were cut off from the network:  
 [https://www.torproject.org/svn/trunk/doc/spec/proposals/136-legacy-keys....](https://www.torproject.org/svn/trunk/doc/spec/proposals/136-legacy-keys.txt "https://www.torproject.org/svn/trunk/doc/spec/proposals/136-legacy-keys.txt")

Sometime in late June or early July we will disable this workaround, meaning all the 0.2.0.x users who haven't upgraded yet will be cut off.

We are preparing for the Tor gathering at the Privacy Enhancing Technologies Symposium in Leuven in July. This is looking like it will be the largest physical gathering of Tor developers ever -- main developers attending include Roger Dingledine, Nick Mathewson, Jacob Appelbaum, Mike Perry, Matt Edman, Steven Murdoch, and Karsten Loesing; Tor researchers include Paul Syverson and Ian Goldberg; and we'll have 5 of our 7 Google Summer of Code students there as well.  
 [https://blog.torproject.org/events/roger%2C-nick%2C-steven%2C-matt%2C-ka...](https://blog.torproject.org/events/roger%2C-nick%2C-steven%2C-matt%2C-karsten%2C-paul%2C-jacob-pets "https://blog.torproject.org/events/roger%2C-nick%2C-steven%2C-matt%2C-karsten%2C-paul%2C-jacob-pets")  
 [http://petsymposium.org/2008/program.php](http://petsymposium.org/2008/program.php "http://petsymposium.org/2008/program.php")

The upcoming TBB release in June will include optional instant messaging support via Pidgin + Off-The-Record Messaging; replace the startup batch script with an actual application (named RelativeLink), so TBB now has a helpful Tor icon rather than an ugly batch file icon; and optionally support using WinRAR to produce a self-extracting split bundle.

We now have a more thorough set of TBB build instructions:  
 [https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/INSTALL](https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/INSTALL "https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/INSTALL")

We also documented the build and deploy process for a new TBB version:  
 [https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/DEPLOYMENT](https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/DEPLOYMENT "https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/DEPLOYMENT")

We finished integrating a UPnP library into Vidalia. This feature allows users who want to set up a Tor relay but don't want to muck with manual port forwarding on their router/firewall to just click a button and have Vidalia interact with their router/firewall automatically. This approach won't work in all cases, but it should work in at least some. The upcoming Vidalia 0.1.4 (scheduled for June) release has folded the UPnP library and GUI changes into the main Vidalia tree, along with a "test" button to try speaking UPnP at the local router and tell the user whether it worked; these features will be available by default in the 0.2.0.x stable release.

We spent May hunting for a better online translation option, since Launchpad (intended to be used for Vidalia translation) has an ugly interface and can't handle our file formats well, and Babelzilla (intended to be used for Torbutton translation) artificially limited the number of concurrent translators we could have.

In early June we hit upon Pootle, which is a translation server that we host, as opposed to a shared web service that other organizations host. We've set up a test server at [http://translation.torproject.org/](http://translation.torproject.org/ "http://translation.torproject.org/") and imported strings for Vidalia, Torbutton, and Torcheck. We hope to have a lot more to show here in June.

