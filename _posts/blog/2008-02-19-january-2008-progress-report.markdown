---
layout: post
title: "January 2008 Progress Report"
permalink: january-2008-progress-report
date: 2008-02-19
author: phobos
category: blog
tags: ["bridges", "incognito", "progress report", "tor", "torbrowser", "torbutton"]
---

Tor 0.2.0.18-alpha (released Jan 25) adds a sixth v3 directory authority run by CCC, fixes a big memory leak in 0.2.0.17-alpha, and adds new config options that can warn or reject connections to ports generally associated with vulnerable-plaintext protocols.  
 [http://archives.seul.org/or/talk/Jan-2008/msg00442.html](http://archives.seul.org/or/talk/Jan-2008/msg00442.html "http://archives.seul.org/or/talk/Jan-2008/msg00442.html")

Tor 0.2.0.16-alpha and 0.2.0.17-alpha (released Jan 17) add a fifth v3 directory authority run by Karsten Loesing, and generally clean up a lot of features and minor bugs.  
 [http://archives.seul.org/or/talk/Jan-2008/msg00254.html](http://archives.seul.org/or/talk/Jan-2008/msg00254.html "http://archives.seul.org/or/talk/Jan-2008/msg00254.html")

Tor 0.1.2.19 (released Jan 17) fixes a huge memory leak on exit relays, makes the default exit policy a little bit more conservative so it's safer to run an exit relay on a home system, and fixes a variety of smaller issues.  
 [http://archives.seul.org/or/announce/Jan-2008/msg00000.html](http://archives.seul.org/or/announce/Jan-2008/msg00000.html "http://archives.seul.org/or/announce/Jan-2008/msg00000.html")

We continued work on the "BridgeDB" module: major progress on January was to improve robustness of the email subsystem so it is better at detecting forged mails that claim to be from gmail but are actually from elsewhere.

Work continued toward the upcoming Torbutton 1.1.13 release (which came out Feb 1). This new release has several significant security-related fixes:  
 [https://torbutton.torproject.org/dev/CHANGELOG](https://torbutton.torproject.org/dev/CHANGELOG "https://torbutton.torproject.org/dev/CHANGELOG")

Work continued toward the upcoming Vidalia 0.1.0 release: support for launching Firefox and Polipo as supporting applications; support for learning from Tor when the first circuit is ready so it can inform the user; and many other bugfixes including a few security fixes:  
 [http://trac.vidalia-project.net/browser/vidalia/trunk/CHANGELOG](http://trac.vidalia-project.net/browser/vidalia/trunk/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/trunk/CHANGELOG")

We added a "How do I find a bridge?" link and corresponding help text to Vidalia's 'Network' settings page.

From the Tor 0.2.0.16-alpha ChangeLog:  
“Do not try to download missing certificates until we have tried to check our fallback consensus.” This change gets us closer to being able to bootstrap without ever needing to contact the central directory authorities.

New proposal "Version 2 Tor connection protocol" that specifies the details of our proposed new TLS handshake and how it interacts with current clients and servers:  
 [https://www.torproject.org/svn/trunk/doc/spec/proposals/130-v2-conn-prot...](https://www.torproject.org/svn/trunk/doc/spec/proposals/130-v2-conn-protocol.txt "https://www.torproject.org/svn/trunk/doc/spec/proposals/130-v2-conn-protocol.txt")

New proposal "Block Insecure Protocols by Default" in collaboration with researchers at University of Colorado to warn and/or refuse users when they try to use ports commonly associated with vulnerable-plaintext protocols:  
 [https://www.torproject.org/svn/trunk/doc/spec/proposals/129-reject-plain...](https://www.torproject.org/svn/trunk/doc/spec/proposals/129-reject-plaintext-ports "https://www.torproject.org/svn/trunk/doc/spec/proposals/129-reject-plaintext-ports")

Implemented in Tor 0.2.0.18-alpha:  
“New config options WarnPlaintextPorts and RejectPlaintextPorts so Tor can warn and/or refuse connections to ports commonly used with vulnerable-plaintext protocols. Currently we warn on ports 23, 109, 110, and 143, but we don't reject any.”

Started work on a roadmap of all the future features and extensions we know we need. It's still mostly in outline form at this point:  
 [https://www.torproject.org/svn/trunk/doc/design-paper/roadmap-future.pdf](https://www.torproject.org/svn/trunk/doc/design-paper/roadmap-future.pdf "https://www.torproject.org/svn/trunk/doc/design-paper/roadmap-future.pdf")

From the Tor 0.2.0.18-alpha ChangeLog:  
“If we've gone 12 hours since our last bandwidth check, and we estimate we have less than 50KB bandwidth capacity but we could handle more, do another bandwidth test.” Bridge relays that weren't getting any use were seeing their bandwidth estimate fall to 0 after the first few days of uptime.

From the Tor 0.2.0.16-alpha ChangeLog:  
“Make bridges round reported GeoIP stats info up to the nearest multiple of 8, not down. Now we can distinguish between "0 people from this country" and "1 person from this country", without needing to collect precise statistics.”  
“Bridge authorities are no longer willing to serve bridge descriptors over unencrypted connections.” This will discourage people from writing tools that don't bother using encrypted connections.

We continued to deploy the new design for the normalized TLS handshake. Thanks to some assistance from an OpenSSL development team member, we were able to get closer to completing a new version-2 style TLS handshake. In early February we have successfully made such a handshake: so we expect that February will be the month when this feature finally rolls out.

From the Tor 0.1.2.19 ChangeLog:  
“Exit policies now reject connections that are addressed to a relay's public (external) IP address too, unless ExitPolicyRejectPrivate is turned off. We do this because too many relays are running nearby to services that trust them based on network address.” This change will allow more people to run relays comfortably, thus expanding the network.  
“Stop thinking that 0.1.2.x directory servers can handle "begin\_dir" requests. Should ease bugs 406 and 419 where 0.1.2.x relays are crashing or mis-answering these types of requests.”  
“Fix a memory leak on exit relays; we were leaking a cached\_resolve\_t on every successful resolve. Reported by Mike Perry.”

From the Tor 0.2.0.16-alpha ChangeLog:  
“Major performance improvement: Switch our old ring buffer implementation for one more like that used by free Unix kernels. The wasted space in a buffer with 1MB of data will now be more like 8KB than 1MB. The new implementation also avoids realloc();realloc(); patterns that can contribute to memory fragmentation.”

The Tor Browser Bundle now has its own webpage, complete with an installation guide and screenshots:  
 [https://torbrowser.torproject.org/](https://torbrowser.torproject.org/ "https://torbrowser.torproject.org/")

The new 0.0.6 Tor Browser Bundle (released Jan 29) includes Polipo, includes a newer Tor release, and fixes a few configuration aspects to make it more secure:  
 [https://tor-svn.freehaven.net/svn/torbrowser/branches/stable/README](https://tor-svn.freehaven.net/svn/torbrowser/branches/stable/README "https://tor-svn.freehaven.net/svn/torbrowser/branches/stable/README")

A new version of the Incognito Privacy LiveCD was released on Jan 26. It includes new versions of many components, and also some bugfixes on the USB support:  
 [http://anonymityanywhere.com/incognito/](http://anonymityanywhere.com/incognito/ "http://anonymityanywhere.com/incognito/")

