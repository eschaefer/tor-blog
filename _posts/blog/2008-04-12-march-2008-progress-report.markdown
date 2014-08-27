---
layout: post
title: "March 2008 Progress Report"
permalink: march-2008-progress-report
date: 2008-04-12
author: phobos
category: blog
tags: ["progress report", "release candidate", "torbrowser", "torbutton"]
---

Tor 0.2.0.23-rc (released Mar 24) is the fourth release candidate for the 0.2.0 series. It makes bootstrapping faster if the first directory mirror you contact is down. The bundles also include the new Vidalia 0.1.2 release.  
 [http://archives.seul.org/or/talk/Mar-2008/msg00204.html](http://archives.seul.org/or/talk/Mar-2008/msg00204.html "http://archives.seul.org/or/talk/Mar-2008/msg00204.html")

Tor 0.2.0.22-rc (released Mar 18) is the third release candidate for the 0.2.0 series. It enables encrypted directory connections by default for non-relays, fixes some broken TLS behavior we added in 0.2.0.20-rc, and resolves many other bugs. The bundles also include Vidalia 0.1.1 and Torbutton 1.1.17.  
 [http://archives.seul.org/or/talk/Mar-2008/msg00136.html](http://archives.seul.org/or/talk/Mar-2008/msg00136.html "http://archives.seul.org/or/talk/Mar-2008/msg00136.html")

Tor 0.2.0.21-rc (released Mar 2) is the second release candidate for the 0.2.0 series. It makes Tor work well with Vidalia again, fixes a rare assert bug, and fixes a pair of more minor bugs. The bundles also include Vidalia 0.1.0 and Torbutton 1.1.16.  
 [http://archives.seul.org/or/talk/Mar-2008/msg00025.html](http://archives.seul.org/or/talk/Mar-2008/msg00025.html "http://archives.seul.org/or/talk/Mar-2008/msg00025.html")

Torbutton 1.1.16 (released Mar 3) and 1.1.17 (released Mar 15) fix many more potential privacy and identity leaks, mostly based on exploits found by Greg Fleischer, and try to start adding support for Firefox 3.  
 [https://torbutton.torproject.org/dev/CHANGELOG](https://torbutton.torproject.org/dev/CHANGELOG "https://torbutton.torproject.org/dev/CHANGELOG")

Vidalia 0.1.0 (released Mar 1), 0.1.1 (released Mar 17), and 0.1.2 (released Mar 24) changes the build process from make to cmake, starts doing encrypted geoip fetches rather than plaintext geoip fetches, checks if the user is running a dangerous or obsolete version of Tor and pops up a window warning them, waits to turn the Vidalia taskbar onion green until Tor reports that it has established a circuit, folds in the patches from Tor Browser Bundle to have Vidalia launch a browser and/or an http proxy, and fixes many miscellaneous bugs.  
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.2/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.2/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.2/CHANGELOG")

From the Tor 0.2.0.23-rc ChangeLog:  
“When a tunneled directory request is made to a directory server that's down, notice after 30 seconds rather than 120 seconds. Also, fail any begindir streams that are pending on it, so they can retry elsewhere. This was causing multi-minute delays on bootstrap.”

From the Tor 0.2.0.22-rc ChangeLog:  
“Enable encrypted directory connections by default for non-relays, so censor tools that block Tor directory connections based on their plaintext patterns will no longer work. This means Tor works in certain censored countries by default again.”

From the Vidalia 0.1.1 ChangeLog:  
“TunnelDirConns and PreferTunneledDirConns are now enabled by default as of Tor 0.2.0.22-rc. Don't check the 'My ISP blocks connections to the Tor network' box simply because TunnelDirConns is enabled. Checking the box still enables encrypted directory connections on older Tors.”

From the Vidlia 0.1.0 ChangeLog:  
“Listen for the DANGEROUS\_VERSION general status event and warn the user if their version of Tor is no longer recommended.”  
“Listen for the CIRCUIT\_ESTABLISHED client status event and only turn the yellow onion status icon green after Tor has successfully established a circuit.”  
“Add a "How do I find a bridge?" link and corresponding help text to the 'Network' settings page.”  
“Add a 'BrowserExecutable' configuration option to launch a Web browser when Tor has built a circuit, and exit Vidalia when the browser is closed.”  
“Add 'ProxyExecutable' and 'ProxyExecutableArguments' configuration options to launch a proxy application with given parameters when Vidalia starts, and close it when Vidalia exits.”  
“Rename the 'Relay' settings page to the 'Sharing' settings page.”

From the Tor 0.2.0.21-rc ChangeLog:  
“We were sometimes miscounting the number of bytes read from the network, causing our rate limiting to not be followed exactly. Bugfix on 0.2.0.16-alpha. Reported by lodger.”

From the Vidalia 0.1.2 ChangeLog:  
“Bridges are no longer required to have a DirPort set as of Tor 0.2.0.13-alpha, so stop forcing it on for bridges. At some point, we'll likely start forcing DirPort to be disabled for bridges, and on by default but optional for normal relays.”

Tor Browser Bundle 1.0.0 (released Mar 20) and 1.0.1 (released Mar 26) makes it work correctly with Polipo again, updates the versions of many of its components, and makes it easier to build the Bundle with custom included "jar" (plug-in) files as well as "xpi" (extension) files.  
 [https://tor-svn.freehaven.net/svn/torbrowser/trunk/README](https://tor-svn.freehaven.net/svn/torbrowser/trunk/README "https://tor-svn.freehaven.net/svn/torbrowser/trunk/README")

We moved the Tor Browser Bundle website into the main Tor website, so it can re-use our translation infrastructure. Currently its frontpage is available in English, German, Italian, Polish, and Russian.

