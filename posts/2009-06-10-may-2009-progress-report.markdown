---
layout: post
title: "May 2009 Progress Report"
permalink: may-2009-progress-report
date: 06/10/2009
author: phobos
category: blog
tags: ["anonymity advocacy", "metrics", "progress report", "proposals", "translations"]
---

 **New releases**  
On May 25, we released Tor 0.2.1.15-rc.  
On May 17, we released Tor VM 0.0.2.  
On May 25, we released Vidalia 0.1.13 containing

- Remove an old warning on the relay settings page that running a bridge  
 relay requires Tor 0.2.0.8-alpha or newer. 
- Add a workaround for a bug that prevented Vidalia's tray icon from  
 getting added to the system notification area on Gnome when Vidalia was  
 run on system startup. Patch by Steve Tyree. (Ticket #247) 
- Fix a bug that prevented the control panel from displaying when  
 running on the Enlightenment window manager. Patch by Steve Tyree. 
- Rename the CMake variables used to store the location of Qt's lupdate  
 and lrelease executables. Recent versions of CMake decided to use the  
 same variable name, which was stomping on mine, resulting in the wrong  
 lupdate and lrelease executables being used. 
- Use the TorProcess subclass of QProcess for launching Tor when hashing  
 a control password so we can take advantage of its PATH+=:/usr/sbin  
 trick on Debian there too. 
- If a RouterDescriptor object is empty, don't try to display it in the  
 router descriptor details viewer. (Ticket #479)
- Wait until Vidalia has registered for log events via the control port  
 before ignoring Tor's output on stdout. Previously we would start  
 ignoring Tor's stdout after successfully authenticating, but before  
 registering for log events which, in some cases, could lead to  
 messages not appearing in the message log. 
- Update many translations and remove others than are no longer  
 up-to-date enough to be useful.

On May 25th, we released Tor Browser Bundle 1.2.0 containing

- Switch to launching Firefox directly from Vidalia to  
 allow multiple instances of Firefox 
- Update Firefox to 3.0.10 
- Update to Qt 4.5.1
- Update Firefox prefs.js to stop scanning for plugins 
- Update libevent to 1.4.11
- Include the Tor geoip database
- Update Vidalia to 0.1.13
- Update Tor to 0.2.1.15-rc

**Design, develop, and implement enhancements that make Tor a better  
tool for users in censored countries.**

Matt added "fetch bridges" features to Vidalia 0.2.x. This provides a link to automatically request bridges from [https://bridges.torproject.org](https://bridges.torproject.org "https://bridges.torproject.org") for users.

**Architecture and technical design docs for Tor enhancements  
related to blocking-resistance.**  
Proposal 160 aims to let authorities modify the bandwidth they put in  
the consensus for each relay. This step will allow us to adjust the  
weights we advertise for clients, once the measurements from TorFlow  
start giving us better weights.  
 [https://git.torproject.org/checkout/tor/master/doc/spec/proposals/160-ba...](https://git.torproject.org/checkout/tor/master/doc/spec/proposals/160-bandwidth-offset.txt "https://git.torproject.org/checkout/tor/master/doc/spec/proposals/160-bandwidth-offset.txt")

Proposal 161 describes how node bandwidth ratios are  
 computed and how they can be produced in parallel.  
 [https://git.torproject.org/checkout/tor/master/doc/spec/proposals/161-co...](https://git.torproject.org/checkout/tor/master/doc/spec/proposals/161-computing-bandwidth-adjustments.txt "https://git.torproject.org/checkout/tor/master/doc/spec/proposals/161-computing-bandwidth-adjustments.txt")

Proposal 162 describes "consensus flavors": the size of the networkstatus  
consensus is critical, since every user fetches it every few hours. So  
we need a way to add new fields -- and remove old fields -- in a way  
that lets old clients continue to use the consensus. The current plan  
is to build and distribute several different versions at once, so each  
client can fetch the one with the format they expect.  
 [https://git.torproject.org/checkout/tor/master/doc/spec/proposals/162-co...](https://git.torproject.org/checkout/tor/master/doc/spec/proposals/162-consensus-flavors.txt "https://git.torproject.org/checkout/tor/master/doc/spec/proposals/162-consensus-flavors.txt")

Proposal 163 starts to consider the problem of clients using relays as  
single-hop proxies. If many clients start doing this (say, to improve  
their own performance), it puts additional risk on the relays, since now  
an attacker can expect to discover both client origins and destinations  
by attacking the relay. Our current strategy for forcing clients to use  
more than one hop is quite fragile, and it looks like we will soon need  
more robust strategies.  
 [https://git.torproject.org/checkout/tor/master/doc/spec/proposals/163-de...](https://git.torproject.org/checkout/tor/master/doc/spec/proposals/163-detecting-clients.txt "https://git.torproject.org/checkout/tor/master/doc/spec/proposals/163-detecting-clients.txt")

Proposal 164 suggests ways to make it easier for relay operators to  
discover why they are not listed in the networkstatus consensus. We have  
a handle of people each week ask us on IRC why their relay isn't listed,  
and currently the only way to answer is to have a competent directory  
authority operator go dig around in various files in his datadirectory.  
 [https://git.torproject.org/checkout/tor/master/doc/spec/proposals/164-re...](https://git.torproject.org/checkout/tor/master/doc/spec/proposals/164-reporting-server-status.txt "https://git.torproject.org/checkout/tor/master/doc/spec/proposals/164-reporting-server-status.txt")

Proposal 165 focuses on simplifying the steps required to add a new  
directory authority. The current approach requires manual work from every  
directory authority operator within a space of several hours. As the  
number of authorities grows, this synchronization is becoming impractical  
-- and that's causing us to leave the number of authorities small, which  
makes us vulnerable to other attacks. Once this proposal is finalized  
and deployed, we'll hopefully be able to add new authorities more  
smoothly.  
 [https://git.torproject.org/checkout/tor/master/doc/spec/proposals/165-si...](https://git.torproject.org/checkout/tor/master/doc/spec/proposals/165-simple-robust-voting.txt "https://git.torproject.org/checkout/tor/master/doc/spec/proposals/165-simple-robust-voting.txt")

**Grow the Tor network and user base. Outreach.**  
Jacob attended CONFidence in Krakow, Poland as a keynote speaker. [http://2009.confidence.org.pl/](http://2009.confidence.org.pl/ "http://2009.confidence.org.pl/")

Andrew and Jacob attended the Soul of a New Machine conference in Berkeley, CA. [http://hrc.berkeley.edu/events/newmachineconference/](http://hrc.berkeley.edu/events/newmachineconference/ "http://hrc.berkeley.edu/events/newmachineconference/")

Roger and Andrew attended the 7th Annual Chinese Internet Research Conference in Philadelphia, PA. [http://www.global.asc.upenn.edu/index.php?page=167](http://www.global.asc.upenn.edu/index.php?page=167 "http://www.global.asc.upenn.edu/index.php?page=167")

Karsten attended SIGINT 09 in Cologne.

Mike gave a presentation on TorFlow at CodeCon.

Roger met with Nick, Paul Syverson and Aaron Johnson at Yale to work more on Paul's research question: if we trust some Tor relays differently than others, how should we select our paths to be safe, and how do we analyze how safe the paths are?

Roger did a talk for about 15 OSI people in Budapest, Hungary.

**Preconfigured privacy (circumvention) bundles for USB or LiveCD**  
The two large changes were the ability to run multiple instances of Firefox at once, such that a user's personal firefox shouldn't share data with the firefox from our bundle. The other change is the ability to stop TBB firefox from scanning the system for potential plugins, like Windows Media, Java, etc.

Started work on a hardened branch of Incognito live CD to help protect users from possible bugs in the programs running.

**Scalability, load balancing, directory overhead, efficiency.**

We documented the metrics we collect to help us determine the best ways to scale the Tor network. [http://blog.torproject.org/blog/performance-measurements-and-blockingres...](http://blog.torproject.org/blog/performance-measurements-and-blockingresistance-analysis-tor-network "http://blog.torproject.org/blog/performance-measurements-and-blockingresistance-analysis-tor-network") A number of nodes are now collecting this information to assist our network-wide measurements.

Much progress on torctl and torflow tools being used to measure real and potential performance of nodes in the public tor network.

Mike wrote proposal 161 describing how node bandwidth ratios are  
 computed and how they can be produced in parallel. The proposal can be found at [http://git.torproject.org/checkout/tor/master/doc/spec/proposals/161-com...](http://git.torproject.org/checkout/tor/master/doc/spec/proposals/161-computing-bandwidth-adjustments.txt "http://git.torproject.org/checkout/tor/master/doc/spec/proposals/161-computing-bandwidth-adjustments.txt")

Karsten finished a first patch to dump statistics about local queues to disk every 15 minutes. A first impression of how these data could be evaluated can be found in [http://freehaven.net/~karsten/volatile/bufferstats-2009-05-25.pdf](http://freehaven.net/~karsten/volatile/bufferstats-2009-05-25.pdf "http://freehaven.net/~karsten/volatile/bufferstats-2009-05-25.pdf"). The goal is to see if our buffer allocation algorithms are sufficient or need tweaking.

**More reliable (e.g. split) download mechanism.**  
Developed the ability to split Apple OS X bundles into 1.44MB chunks. The functionality is native to OS X versions 10.4 and newer. It will not work in versions 10.3.9 or earlier releases.

**Translation work, ultimately a browser-based approach**  
11 Polish updates  
4 German updates  
Portugese torbutton updates  
Danish torbutton updates  
Romanian torbutton updates  
11 Italian updates  
3 Chinese updates

