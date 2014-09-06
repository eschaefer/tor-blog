---
layout: post
title: "August 2010 Progress Report"
permalink: blog/august-2010-progress-report
date: 2010-09-13
author: phobos
category: blog
tags: ["alpha releases", "progress report", "scalability", "translations"]
---

 **Releases**

- On August 21st we released Tor Browser Bundle 1.0.10 for GNU/Linux. See [https://blog.torproject.org/blog/tor-browser-bundle-1010-gnulinux-releas...](https://blog.torproject.org/blog/tor-browser-bundle-1010-gnulinux-released "https://blog.torproject.org/blog/tor-browser-bundle-1010-gnulinux-released")
- On August 18, we released Tor 0.2.2.15-alpha. It fixes a big bug in hidden service availability, fixes a variety of other bugs that were preventing performance experiments from moving forward, fixes several bothersome memory leaks, and generally closes a lot of smaller bugs that have been filling up trac lately. See [https://blog.torproject.org/blog/tor-02215-alpha-released](https://blog.torproject.org/blog/tor-02215-alpha-released "https://blog.torproject.org/blog/tor-02215-alpha-released")
- Released two new versions of Orbot, Tor for Android.
> Version 1.0.2
> - added "check" yes/no dialog prompt
> - debugged iptables/transprox settings on Android 1.6 and 2.2
> - added proxy settings help screen and fixed processSettings() NPE
>
> Version 1.0.1
> - found and fixed major bug in per-app trans proxying; list of apps was being cached and iptables rules were not properly updated as the user changed the selection in the list
- On August 6, we released Libevent 2.0.6-rc, the first release
candidate of the new Libevent 2.0 series. The main new feature that
we want from Libevent 2.0 is its support for buffer-based (rather than
socket-based) network abstractions, which will let us support Windows the
way it wants to be supported. The new Libevent includes a wide variety of
other features that will make our lives easier too, ranging from making
it easier to support multi-threaded crypto operations to making it easier
to modularly change Tor's transport from TLS-over-TCP to other options. See [http://levent.git.sourceforge.net/git/gitweb.cgi?p=levent/levent;a=blob;...](http://levent.git.sourceforge.net/git/gitweb.cgi?p=levent/levent;a=blob;f=ChangeLog;hb=fe008ed656766266b93cdf2083f5b8bc50e6aad3 "http://levent.git.sourceforge.net/git/gitweb.cgi?p=levent/levent;a=blob;f=ChangeLog;hb=fe008ed656766266b93cdf2083f5b8bc50e6aad3")

**Funding**
We finished the first year of our NSF grant, and wrote up the annual
(interim) report on what metrics work we've done and what research
projects we've helped with. We were then awarded the second year of the
two-year grant.

**Design, develop, and implement enhancements that make Tor a better
tool for users in censored countries.**

Continuing research into China's Great Firewall shows bridges are surviving for 1-2 weeks before being blocked. We're working to improve the bridge database such that it only gives out bridges that work in a requested country. Right now, we hand out a random selection of 3 bridges regardless of potential country of usage. In China, bridges and relays are still blocked by IP address and TCP port combinations.

**Architecture and technical design docs for Tor enhancements
related to blocking-resistance.**

We've brainstormed future tasks that need to be done for Tor, broken down
into two sets by upcoming priority:
 [https://trac.torproject.org/projects/tor/wiki/sponsors/SponsorD/March201...](https://trac.torproject.org/projects/tor/wiki/sponsors/SponsorD/March2011 "https://trac.torproject.org/projects/tor/wiki/sponsors/SponsorD/March2011")
and
 [https://trac.torproject.org/projects/tor/wiki/sponsors/SponsorD/June2011](https://trac.torproject.org/projects/tor/wiki/sponsors/SponsorD/June2011 "https://trac.torproject.org/projects/tor/wiki/sponsors/SponsorD/June2011")

We wrote up project sketches of how to tackle some of these tasks, such as:

- Bridge relay images for the cloud. [https://trac.torproject.org/projects/tor/ticket/1853](https://trac.torproject.org/projects/tor/ticket/1853 "https://trac.torproject.org/projects/tor/ticket/1853")
- Bundling the http request and headers with the initial begin cell, to save a round-trip and improve client preformance. [https://trac.torproject.org/projects/tor/ticket/1849](https://trac.torproject.org/projects/tor/ticket/1849 "https://trac.torproject.org/projects/tor/ticket/1849")
- A performance experiment to raise the minimum bandwidth for being a relay, thus reducing the overall capacity of the network but improving the average performance of each relay. [https://trac.torproject.org/projects/tor/ticket/1854](https://trac.torproject.org/projects/tor/ticket/1854 "https://trac.torproject.org/projects/tor/ticket/1854")
- A preliminary design for UDP transport between Tor relays. [https://trac.torproject.org/projects/tor/ticket/1855](https://trac.torproject.org/projects/tor/ticket/1855 "https://trac.torproject.org/projects/tor/ticket/1855")
- Tor clients should remember bridge relay information and statistics across restarts. [https://trac.torproject.org/projects/tor/ticket/1852](https://trac.torproject.org/projects/tor/ticket/1852 "https://trac.torproject.org/projects/tor/ticket/1852")
- We should have bridge relays automatically monitor whether they can reach websites like Baidu, to give us early warnings when the bridges become blocked. [https://trac.torproject.org/projects/tor/ticket/1851](https://trac.torproject.org/projects/tor/ticket/1851 "https://trac.torproject.org/projects/tor/ticket/1851")

**Outreach and Advocacy**

- Roger met with the University of California - San Diego research group to help them better understand the research challenges in Tor. The full trip report is available at [https://blog.torproject.org/blog/trip-report-ucsd](https://blog.torproject.org/blog/trip-report-ucsd "https://blog.torproject.org/blog/trip-report-ucsd"). Roger's presentation can be found at [https://svn.torproject.org/svn/projects/presentations/slides-ucsd10.pdf](https://svn.torproject.org/svn/projects/presentations/slides-ucsd10.pdf "https://svn.torproject.org/svn/projects/presentations/slides-ucsd10.pdf").
- Roger met with a researcher from The Cooperative Association for Internet Data Analysis (CAIDA) to discuss Tor, metrics, and analyzing our growing collection of data about the Tor network.
- Roger attended the "Workshop on Cyber Security Data for Experimentation" organized by the National Science Foundation (NSF). The premise of the workshop was that many academics need real-world data sets to solve problems, whereas industry is the place with the real-world data sets and they don't have any real reason to share. By getting the academics and the industry people talking, with government funders nearby, they hoped to better understand the problems and maybe move things forward.
Roger was there (and on the first panel) because of Tor's work on gathering Tor network snapshots, performance data, and user statistics. Tor's approach represents one way out of the trap where researchers never quite get the data they want, or if they do it isn't open enough (which hinders whether anybody else can reproduce their results). The full trip report is available at [https://blog.torproject.org/blog/trip-report-nsf-data-workshop](https://blog.torproject.org/blog/trip-report-nsf-data-workshop "https://blog.torproject.org/blog/trip-report-nsf-data-workshop").
- Roger did a talk to a half dozen NSF program managers, to bring them up to speed on what Tor is up to and what sort of measurement and research projects we're working on and should work on next. The presentation can be found at [https://svn.torproject.org/svn/projects/presentations/slides-nsf10.pdf](https://svn.torproject.org/svn/projects/presentations/slides-nsf10.pdf "https://svn.torproject.org/svn/projects/presentations/slides-nsf10.pdf").
- Erinn discussed Tor and free software at DebConf 2010 in New York City. [http://debconf10.debconf.org/](http://debconf10.debconf.org/ "http://debconf10.debconf.org/").
- Andrew and Paul presented at The International Conference on Cyber Security. [http://www.iccs.fordham.edu/](http://www.iccs.fordham.edu/ "http://www.iccs.fordham.edu/"). Andrew's presentation can be found at [https://svn.torproject.org/svn/projects/presentations/2010-iccs-tor-over...](https://svn.torproject.org/svn/projects/presentations/2010-iccs-tor-overview.pdf "https://svn.torproject.org/svn/projects/presentations/2010-iccs-tor-overview.pdf"). Paul presented the current attacks on Tor's design from a research perspective, as well as giving a briefing on current topics of research into trusted routing within Tor.
- Ian, Roger, and others attended Usenix Security 2010, [http://www.usenix.org/events/sec10/index.html](http://www.usenix.org/events/sec10/index.html "http://www.usenix.org/events/sec10/index.html").

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**

- Torbrowser Bundle for GNU/Linux version 1.0.10 released. See above for the details.
- Torbrowser Bundle for OSX works on OS X 10.4 and 10.5. 10.6 users continue to experience issues with the launching of the Firefox browser. Erinn and Steven are continuing to debug the 10.6 issues.

**Bridge relay and bridge authority work.**

We're developing designs to better handle bridge distribution. Part of this is to enable Tor clients to become bridges and then relays by default. The other part of this is for Tor clients to always have a set of working bridges, requesting new bridges in advance, or be able to track bridge address changes and update accordingly.

**Scalability, load balancing, directory overhead, efficiency.**

- Accepted Proposal 174 for "Optimistic Data for Tor: Server Side" from Ian Goldberg. This change will save one OP-Exit round trip (down to one from two). There are still two SOCKS Client-OP round trips (negligible time) and two Exit-Server round trips. Depending on the ratio of the Exit-Server (Internet) RTT to the OP-Exit (Tor) RTT, this will decrease the latency by 25 to 50 percent. Experiments validate these predictions. [Goldberg, PETS 2010 rump session; see https://thunk.cs.uwaterloo.ca/optimistic-data-pets2010-rump.pdf] The full proposal can be read at [https://gitweb.torproject.org/tor.git/blob\_plain/HEAD:/doc/spec/proposal...](https://gitweb.torproject.org/tor.git/blob_plain/HEAD:/doc/spec/proposals/174-optimistic-data-server.txt "https://gitweb.torproject.org/tor.git/blob\_plain/HEAD:/doc/spec/proposals/174-optimistic-data-server.txt").
- Mike Perry fixed a number of bugs in the bandwidth authority and exit scanner codebases. The exit scanner codebase is updated with the work of a Google Summer of Code student.
- A Google Summer of Code student, Harry Bock, worked on improving the Tor DNSEL codebase. TorDNSEL is a DNSBL-style interface for querying information about Tor exit nodes, to be more thorough, more usable, and more maintainable. Out of this effort came TorBEL, a set of specifications and Python tools that try to address this problem. The full writeup on the new software can be found on our blog at [https://blog.torproject.org/blog/torbel-tor-bulk-exit-list-tools](https://blog.torproject.org/blog/torbel-tor-bulk-exit-list-tools "https://blog.torproject.org/blog/torbel-tor-bulk-exit-list-tools").

**Translations**
Runa implemented a change to the publishing of translated website pages. We now only publish a non-English page to the website if the text is 80% translated or more. This has cleared out hundreds of older, untranslated pages from the website that were misinforming and confusing readers.

Updated translations for all documents in Arabic, Persian, German, French, Polish, Romanian, Russian, Norwegian, Mandarin Chinese, and Turkish.

