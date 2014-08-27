---
layout: post
title: "October 2010 Progress Report"
permalink: october-2010-progress-report
date: 2010-11-09
author: phobos
category: blog
tags: ["arm", "bug fixes", "https everywhere", "metrics", "progress report", "tor browser bundle", "translations"]
---

 **New Releases**

- On October 29th, we released updated Tor Browser Bundles for OS X, Linux, and Windows. This is an upgrade to Firefox 3.6.12 which fixes a critical bug and OS X users' Torbutton will now show up. [https://blog.torproject.org/blog/new-tor-browser-bundles-released-take-t...](https://blog.torproject.org/blog/new-tor-browser-bundles-released-take-two "https://blog.torproject.org/blog/new-tor-browser-bundles-released-take-two")
- On October 28th, we released new OSX Vidalia bundles which include Tor 0.2.2.17-alpha. Vidalia 0.2.10 changed the way we deal with the geoip databases by dropping the remote geoip lookups. This caused a lot of headaches for OS X users because of the layout of the package, but it's fixed in this version. [https://blog.torproject.org/blog/mac-os-x-vidalia-bundle-02217-alpha-out](https://blog.torproject.org/blog/mac-os-x-vidalia-bundle-02217-alpha-out "https://blog.torproject.org/blog/mac-os-x-vidalia-bundle-02217-alpha-out")
- On October 27th, we released a new Tor Check to fix links to documentation urls, and clarify what users should do when getting the success result. [https://check.torproject.org](https://check.torproject.org "https://check.torproject.org").
- On October 27th, we released new Tor Browser Bundles for OSX, Linux, and Windows. The main notable upgrades for these are Firefox 3.6.11 and Pidgin 2.7.4 in the Windows IM bundle. [https://blog.torproject.org/blog/new-tor-browser-bundles-released](https://blog.torproject.org/blog/new-tor-browser-bundles-released "https://blog.torproject.org/blog/new-tor-browser-bundles-released")
- On October 29th, we released new Tor Browser Bundles. This is an upgrade to Firefox 3.6.12 which fixes a critical bug and OS X users' Torbutton will now show up. [https://blog.torproject.org/blog/new-tor-browser-bundles-released-take-t...](https://blog.torproject.org/blog/new-tor-browser-bundles-released-take-two "https://blog.torproject.org/blog/new-tor-browser-bundles-released-take-two")
- On October 17th, The HTTPS Everywhere Extension for Firefox version 0.2.3.development.1 was released.
- On October 6th, Arm 1.3.7 was released. [http://www.atagar.com/arm/](http://www.atagar.com/arm/ "http://www.atagar.com/arm/"). Changelog at [http://www.atagar.com/arm/log.php](http://www.atagar.com/arm/log.php "http://www.atagar.com/arm/log.php")
- On October 7th, we released a hotfix to Arm 1.3.7: fix (10/7/10, r23463): crashing from type issue in the graph panel (caught by tomb)
- On October 9th, we released the new [https://www.torproject.org](https://www.torproject.org "https://www.torproject.org") website after 4 months of design and conversion work. It features an entirely redesigned Information Architecture, user experience design, and codebase. Andrew, Roger, Sebastian, Runa, and many volunteers contributed to this release.

**Design, develop, and implement enhancements that make Tor a better  
tool for users in censored countries.**  
Nick continued to work on the codebase around microdescriptors. Microdescriptors will allow clients on very low bandwidth connections to use the tor network more quickly than waiting to download the current directory information.

**Grow the Tor network and user base. Outreach.**

- Roger speaks at Internet Dagarna in Sweden, [http://www.internetdagarna.se/](http://www.internetdagarna.se/ "http://www.internetdagarna.se/"). The video of his talk is provided by the Internet Foundation at  
 [http://www.youtube.com/watch?v=35l56KjTCb8&p=5BE29144D1FD2779](http://www.youtube.com/watch?v=35l56KjTCb8&p=5BE29144D1FD2779 "http://www.youtube.com/watch?v=35l56KjTCb8&p=5BE29144D1FD2779").
- Roger, Ian, and others attended WPES2010, Workshop on Privacy in the Electronic Society, [http://wpes10.csi.muohio.edu/](http://wpes10.csi.muohio.edu/ "http://wpes10.csi.muohio.edu/").
- Roger, Ian, and others attended 17th ACM Conference on Computer and Communications Security, [http://www.sigsac.org/ccs/CCS2010/](http://www.sigsac.org/ccs/CCS2010/ "http://www.sigsac.org/ccs/CCS2010/").
- Roger, Paul, and Andrew attended the Information Technology Study Group (ITSG).
- Jacob attended Bluehat, [http://technet.microsoft.com/en-us/security/cc261637.aspx](http://technet.microsoft.com/en-us/security/cc261637.aspx "http://technet.microsoft.com/en-us/security/cc261637.aspx").
- Roger gave a lecture at the State University of New York -Stonybrook.
- Jacob attended the Workshop on Elliptic Curve Cryptography, [http://2010.eccworkshop.org/](http://2010.eccworkshop.org/ "http://2010.eccworkshop.org/").
- Roger, Mike, Jacob, Erinn represented Tor at the Google Summer of Code Mentor Summit.
- Roger gave a lecture at Stanford University, [http://crypto.stanford.edu/seclab/sem.html](http://crypto.stanford.edu/seclab/sem.html "http://crypto.stanford.edu/seclab/sem.html").
- Andrew, Karen, and Linus met with the Swedish Foreign Ministry, Swedish International Development Agency, [http://www.sida.se/](http://www.sida.se/ "http://www.sida.se/"), and NORDUnet, [http://www.nordu.net/](http://www.nordu.net/ "http://www.nordu.net/").

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**  
Working with the TA(I)LS LiveCD/LiveUSB team to get architecture designs, specifications, and goals written down and published. The desired state is to be able to analyze the live system for a number of security and anonymity properties through security and code audits.

**Bridge relay and bridge authority work.**

Mike began investigating the odd reality that we only report 500 bridges available at any point in time. Hundreds to thousands of people become bridges each week, but only around 500 are reported as being available at any point in time. This seems an odd coincidence to Mike and others. Research continues.

**Scalability, load balancing, directory overhead, efficiency.**

- Karsten incorporated Kevin Berry's Google Summer of Code work into the metrics portal, [https://blog.torproject.org/blog/tor-metrics-google-summer-code-2010](https://blog.torproject.org/blog/tor-metrics-google-summer-code-2010 "https://blog.torproject.org/blog/tor-metrics-google-summer-code-2010"). This enables all graphs to be dynamically generated with minimal load to the server.
- Karsten and Sebastian continue to research an alternate way to more accurately count Tor users while still preserving their anonymity by design. They expect to have a report out in December 2010.
- Mike fixed some bugs relating to Bandwidth and Exit Authorities. These fixes are for code stability.
- Update to the October 1 2010 Maxmind GeoLite Country database. This updates the mapping of IP Address to Geolocation of relays.
- Nick commits a huge number of bug fixes, code refactoring, and general logic corrections as discovered through code audits, buffer events integration, and volunteer reviews.
- Karsten extended total relay bandwidth graph, [https://metrics.torproject.org/network.html#bandwidth](https://metrics.torproject.org/network.html#bandwidth "https://metrics.torproject.org/network.html#bandwidth") by bandwidth history as  
reported by relays and added new graph on directory bytes written by relays, [https://metrics.torproject.org/network.html#dirbytes](https://metrics.torproject.org/network.html#dirbytes "https://metrics.torproject.org/network.html#dirbytes").
- Karsten changed most servlets to JSPs, added database connection pool, made the  
Tomcat application generate CSV files upon request, etc. These changes  
are not visible to most people, but they were necessary to clean up the  
grown metrics website. As a result, it's much easier now to add new  
graphs to the website.
- Karsten helped a volunteer to write a Python version of the VisiTor script, [https://metrics.torproject.org/tools.html#visitor](https://metrics.torproject.org/tools.html#visitor "https://metrics.torproject.org/tools.html#visitor"),  
and wrote a spec for the exit list file format, [https://trac.torproject.org/projects/tor/ticket/2064#comment:1](https://trac.torproject.org/projects/tor/ticket/2064#comment:1 "https://trac.torproject.org/projects/tor/ticket/2064#comment:1").
- Karsten found a new approach for combining directory request statistics from multiple relays to estimate total user numbers. The result is a much more reliable metric than the one we're using right now, [https://metrics.torproject.org/users.html#direct-users](https://metrics.torproject.org/users.html#direct-users "https://metrics.torproject.org/users.html#direct-users"). Asked Olaf Selke (operator of blugmagie), Teun Nijssen (operator of TORy), and a few more to turn on directory request statistics on their relays. Updated tech report on Privacy-preserving Ways to Estimate the Number of Tor Users with new results, [https://gitweb.torproject.org/karsten/metrics.git/blob\_plain/refs/heads/...](https://gitweb.torproject.org/karsten/metrics.git/blob_plain/refs/heads/counting-users:/report/counting-users/countingusers.pdf "https://gitweb.torproject.org/karsten/metrics.git/blob\_plain/refs/heads/counting-users:/report/counting-users/countingusers.pdf").

**Footprints from Tor Browser Bundle.**  
Tor Browser Bundle in OS X contains sandboxing technology by Robert Malmgren AB, [http://www.romab.com/](http://www.romab.com/ "http://www.romab.com/"). The sandbox is designed to both protect the user from security exploits in Firefox and restrict the footprint left on a system by the Tor Browser Bundle. Currently, this solution is OS X only.

**Translation work, ultimately a browser-based approach.**  
Updated translations in Spanish, Ukrainian, Mandarin, Dutch, German, Greek, Urdu, Italian, and Icelandic.

