---
layout: post
title: "July 2010 Progress Report"
permalink: july-2010-progress-report
date: 2010-08-12
author: phobos
category: blog
tags: ["alpha releases", "bug fixes", "development", "enhancements", "orbot", "performance improvements", "portable bundles", "progress report", "research", "research progress", "research reports", "research results", "tor browser bundle"]
---

 **New releases**

- On July 4th, we released Tor Browser Bundle 1.3.7 for Microsoft Windows. This is a security update for Firefox and Pidgin. The changes are: update to Firefox 3.5.10 and Pidgin Instant Messenger 2.7.1r2 to fix some security issues.
- On July 6th, we released Tor Browser Bundle 1.0.8 for GNU/Linux distributions. This fixes a number of security issues with included software. The updates include:
  - Update libpng to 1.4.3 (see CVE-2010-1205)
  - Update Firefox to 3.5.10
  - Update HTTPS Everywhere to 0.2.1

- On July 12th, we released the Tor 0.2.2.14-alpha. This latest -alpha greatly improves client-side handling of circuit build timeouts, which are used to estimate speed and improve performance. We also move to a much better GeoIP database, port Tor to Windows CE, introduce new compile ﬂags that improve code security, add an eighth v3 directory authority, and address a lot of more minor issues. See [https://blog.torproject.org/blog/tor-02214-alpha-released](https://blog.torproject.org/blog/tor-02214-alpha-released "https://blog.torproject.org/blog/tor-02214-alpha-released") for full changelog.
- On July 15th, we released the latest version of OrBot, tor for the Android operating system, version 0.0.8. Fixes include:
  - Updated Settings & App configuration screens
  - Changed progress dialog display
  - Significant application re-arch
  - Fixed force stop crash on install
  - Integrated Tor 0.2.2.13-alpha-dev binary
  - Fixed su shell cmd error handling & root perms issue
  - #1570: Added new setup wizard on install to clarify root / non-root capabilities
  - #1716: Per-app traffic routing prefs not persisted
  - #1509: Help window is too big for the screen on android 1.6
  - #1513: Orbot can’t be told to exit & added ’Exit’ menu option
  - #1530: Capture sh cmd stout for debugging errors & updated debug log screen
  - #1531: Don’t loop ad infinitum in Orbot fails only retries 3 times now
  - #1272: Orbot should store Tor files in the cache
  - #1273: Info should mention anonymity problems with ProxySurf

- On July 22nd, we released updated Tor Browser Bundles for Windows. Versions 1.3.8 and 1.3.9 are upgrades to fix security issues with Firefox and Pidgin. Firefox is updated to 3.5.11.Pidgin Instant Messenger client is updated to 2.7.2.

**Design, develop, and implement enhancements that makeTor a better tool for users in censored countries.**

- We worked with some Nigerians to determine that the Nigerian government is not mandating Internet censorship. Rather, a few ISPs in Nigeria have closed loopholes that allowed some people to obtain Internet access without paying for an account. The blog post,subsequent comments, and research results are at [https://blog.torproject.org/blog/dear-nigerians-help-us-help-you](https://blog.torproject.org/blog/dear-nigerians-help-us-help-you "https://blog.torproject.org/blog/dear-nigerians-help-us-help-you").
- Jacob, Robert Hogan, and Damon McCoy submitted a proposal to separate streams by port or host from the Tor client. The full proposal can be read at [http://archives.seul.org/or/dev/Jul-2010/msg00021.html](http://archives.seul.org/or/dev/Jul-2010/msg00021.html "http://archives.seul.org/or/dev/Jul-2010/msg00021.html"). The motivation for this proposal is as follows:  
> Streams are currently attached to circuits without regard to their content, destination host,or destination port. We propose two options, IsolateStreamsByPort and IsolateStreamsByHost to change the default behavior.
> 
> The contents of some streams will always have revealing plain text information; these streamsshould be treated diﬀerently than other streams that may or may not have unencrypted PII content. DNS, with the exception of DNSCurve, is always unencrypted. It is reasonable to assume that other protocols may exist that have a similar issue and may cause user concern. It is also the case that we must balance network load issues and stream privacy. The Tor network will not currently scale to one circuit per connection nor should it anytime soon.
> 
> Circuits are currently created with a few constraints and are rotated within a reasonable timewindow. This allows a rogue exit nodes to correlate all streams on a given circuit.
- Continuing research into how the Chinese firewall is currently able to block 90% of the Tor relays and bridges. It seems the firewall is configured to block specific IP Address and TCPPort combinations, as changing combinations on individual IP addresses results in updates to the blocking scheme. The blocking updates in the firewall are possibly updated every two weeks. An interesting area of research would be to do a technical analysis of blocking methods around the world on both landline and mobile Internet connections.

**Grow the Tor network and user base. Outreach.**

- Roger trained more Internews staﬀ on what Tor is and how to use it.
- Tor held its second annual developer meeting in Potsdam, Germany. 24 committed employees, contractors, and volunteers were invited to the ”un-conference”. It was held over two days at the Hasso Plattner Institute at the University of Potsdam. The developers picked the topics and led the discussions over the two days. Topics ranged from an itemization and ownership of all 40 products tor produces to fundraising and financial details of our successful A-133 compliance audit. The current list of products and owners is at [https://trac.torproject.org/projects/tor/wiki/projects/ProductsandAssignments.](https://trac.torproject.org/projects/tor/wiki/projects/ProductsandAssignments)We also rolled out a new project management system and methodology to keep track of our growing ecosystem of software, advocacy, and related projects. See [https://trac.torproject.org/projects/tor/wiki/projects/HowWeDoProjectManagement](https://trac.torproject.org/projects/tor/wiki/projects/HowWeDoProjectManagement)for the details.
- Andrew, Ian, Paul, Karsten, and Steven presented at the 2010 Privacy Enhancing Technologies Symposium in Berlin, Germany. [http://petsymposium.org/2010/](http://petsymposium.org/2010/ "http://petsymposium.org/2010/"). Proceedings of the symposium are online through Springer at [http://www.springerlink.com/content/978-3-642-14526-1/](http://www.springerlink.com/content/978-3-642-14526-1/ "http://www.springerlink.com/content/978-3-642-14526-1/").
  - Ian’s current research was presented by a co-author, Ryan Henry, on ”Making a Nymbler Nymble Using VERBS”. The abstract is available at [http://www.springerlink.com/content/3818173868g05737/](http://www.springerlink.com/content/3818173868g05737/ "http://www.springerlink.com/content/3818173868g05737/").
  - Ian’s other current research topic was presented at HotPETS as a paper in progress on speeding up the Tor handshake. This will be turned into a formal proposal to Tor in August 2010. Ian has actual code and results from live testing on the Tor network as well.
  - Paul’s current research was presented by a co-author, Aaron Johnson, on ”Preventing Active Timing Attacks in Low-Latency Anonymous Communication”. The abstract is available at [http://www.springerlink.com/content/l8r648rr30187115/](http://www.springerlink.com/content/l8r648rr30187115/ "http://www.springerlink.com/content/l8r648rr30187115/").
  - Karsten presented on the vast quantities of data available to researchers at [http://metrics.torproject.org](http://metrics.torproject.org "http://metrics.torproject.org"). We’re soon going to put all of this into a queryable database for easier access and research. This data is licensed under a Creative Commons Zero license, as defined at [http://creativecommons.org/publicdomain/zero/1.0/](http://creativecommons.org/publicdomain/zero/1.0/ "http://creativecommons.org/publicdomain/zero/1.0/"). This material is supported in part by the National Science Foundation under Grant No. CNS-0959138.
  - Steven’s current research was presented by a co-author, Claudia Diaz, on ”Impact of Network Topology on Anonymity and Overhead in Low-Latency Anonymity Networks”. The abstract is available at [http://www.springerlink.com/content/53535522423n2v68/](http://www.springerlink.com/content/53535522423n2v68/ "http://www.springerlink.com/content/53535522423n2v68/").

- Jacob and Seth Shoen of the EFF gave a talk about Tor and Internet Circumvention at The Next HOPE conference in New York City. Their talk is listed at [http://c2047862.cdn.cloudfiles.rackspacecloud.com/tnha08.mp3](http://c2047862.cdn.cloudfiles.rackspacecloud.com/tnha08.mp3 "http://c2047862.cdn.cloudfiles.rackspacecloud.com/tnha08.mp3") or the full talks from the conference are online at [http://thenexthope.org/talks-list/](http://thenexthope.org/talks-list/ "http://thenexthope.org/talks-list/").
- Jacob gave a talk about Tor and Internet Circumvention at DEF CON 18 in Las Vegas, [http://defcon.org/html/defcon-18/dc-18-index.html](http://defcon.org/html/defcon-18/dc-18-index.html "http://defcon.org/html/defcon-18/dc-18-index.html").
- Roger’s advice on choosing a circumvention system was translated and published in Volume 2 of the China Rights Forum, [http://www.hrichina.org/public/contents/category?cid=175033](http://www.hrichina.org/public/contents/category?cid=175033 "http://www.hrichina.org/public/contents/category?cid=175033").

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**  
Erinn continues to work on a Tor Browser Bundle for Apple’s OS X. The Apple TBB is turning into a very tricky item to produce. Even with proper sandboxing support, the TBB leaves a large number of modified files behind due to the way Apple handles dmgs, and running binaries. Compounding progress is the way Firefox integrates into the system, resulting in code patches to the Firefox source.  
Erinn continues to improve Tor Browser Bundle for Linux with feedback from initial users and other volunteer developers.

**Bridge relay and bridge authority work.**  
Tor now has another developer working on bridge authority and bridge database work. The goal is to be able to work down the list of items at [https://trac.torproject.org/projects/tor/wiki/projects/BridgeDB](https://trac.torproject.org/projects/tor/wiki/projects/BridgeDB "https://trac.torproject.org/projects/tor/wiki/projects/BridgeDB") over the next three months.

**Scalability, load balancing, directory overhead, eﬃciency.**

- Mike continues to tune the code for Bandwidth Authorities to better measure and load-balance the Tor network.
- Karsten completed his research into alternative GeoIP databases to more accurately asess from where Tor clients connect. The original research started in April 2010, and was published at [http://archives.seul.org/or/dev/Apr-2010/msg00021.html](http://archives.seul.org/or/dev/Apr-2010/msg00021.html "http://archives.seul.org/or/dev/Apr-2010/msg00021.html"). From the 0.2.2.14-alpha change log, we chose to move to the June 2010 Maxmind GeoLite country db (rather than the June 2009 ip-to-country GeoIP db) for our statistics that count how many users relays are seeing from each country. Now we have more accurate data for many African countries. This will be reﬂected in more accurate country graphs at [http://metrics.torproject.org/](http://metrics.torproject.org/ "http://metrics.torproject.org/").
- Karsten is conducting research into how to more accurately count tor clients than our current methods. The goal here is to get more accurate counts per country than the current sampling method without being able to de-anonymize any individual or group of Tor users.
- Karsten is rolling out new passive performance metrics about Tor. The goal is to better measure the Tor performance to gather more data to make better decisions. The start of the topic is at [http://archives.seul.org/or/dev/Jul-2010/msg00016.html](http://archives.seul.org/or/dev/Jul-2010/msg00016.html "http://archives.seul.org/or/dev/Jul-2010/msg00016.html").
- We completed the first four of seven milestones on our National Science Foundation Grant No. CNS-0959138. The completed milestones are:
  1. Establish a preliminary metrics website to automatically publish daily graphs of collected data. Start with a) estimated user counts for China and Iran, and b) the results of our ”torperf” performance scans.
  2. Technical report: Document our current approaches to measuring statistical data in the Tor anonymity network, and the legal/ethical/technical/social constraints around safe measurements.
  3. Publish a summary of what data and tools we have already, and what data and tools we hope to have. Then begin collaborating (ongoing) with the other researchers in the Anonymous Communications field to integrate our data and tools into their work so they can solve the problems we’re actually seeing rather than the problems they speculate we might have.
  4. Instrument Tor relays to track resource load, including queue sizes, average cell latency, and number of active connections. Safely aggregate these results, then publish ongoing snapshots in our public dataset, and integrate them into our metrics website.

**More reliable (e.g. split) download mechanism.**  
Erinn and Steven are working on an automated building system for packages. This will enable quicker, more reliable releases. The build system will also enable us to produce nightly packages of the current working codebases for Tor and related software.

**Footprints from Tor Browser Bundle.**  
Erinn continues work on footprints of the Tor Browser Bundle for Linux and Apple OS X.

**Translation work, ultimately a browser-based approach.**  
Updates to documentation and website in German, Russian, Polish, Swedish, Farsi, Turkish, Norwegian, French, Italian, Spanish, and Albanian.

