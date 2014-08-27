---
layout: post
title: "December 2009 Progress Report"
permalink: december-2009-progress-report
date: 2010-02-13
author: phobos
category: blog
tags: ["bug fixes", "enhancements", "metrics", "progress report", "releases", "translations"]
---

 **New releases, new hires, new funding**  
Erinn Clark joins Tor to develop, enhance, and upgrade our package build system. Her initial goals are to configure, maintain, and automate builds of tor and vidalia for Windows, OS X, ubuntu, debian, centos, fedora, and opensuse systems. Secondary goals are to develop a builtbot system that includes as many disparate operating systems as possible, including Apple OS X and Microsoft  
Windows flavors.  
 On December 2, 2009, we released torbutton 1.2.3. This is the first release that addresses the  
Firefox 3.5.x codebase. It contains the following changes:

- bugfix: bug 950: Preserve useragent and download settings across toggle
- bugfix: bug 1014: Fix XML Parsing Error on XHTML sites in Tor mode
- bugfix: bug 1041: Preserve tab history in FF3.5
- bugfix: bug 1047: Fix spurious user agent change notice
- bugfix: bug 1053: Partial fix for ’TypeError: browser is undefined’ error
- bugfix: bug 1084: Preserve HTTP accept language for Non-Tor usage
- bugfix: bug 1085: Fix test settings issues with dead privoxy
- bugfix: bug 1088: Clean up some namespace issues in the main chrome window
- bugfix: bug 1091: Fix a lockup when ’Ask Every Time’ cookie pref is set
- bugfix: bug 1093: Fix cert acceptance dialogs in Firefox 3.5
- bugfix: bug 1146: Fixes for properly handling tab restore in FF3.5
- bugfix: bug 1152: Close tabs on toggle prevents toggling in FF3.5”
- bugfix: bug 1154: Clarify ”Last Tor test failed” message
- misc: Disable geolocation in FF3.5 during Tor mode
- misc: Disable DNS prefetch in FF3.5 in Tor mode and for Tor-loaded tabs
- misc: Disable offline app cache during Tor mode
- misc: Disable specific site zoom settings during Tor mode
- new: Transfer Google cookies between country-code domains. This should make it such that captchas only need to be solved once per Tor session, as opposed to for each country.

On December 16, 2009, we released Torbutton 1.2.4. This fixes a number of bugs found after two weeks of live testing by users. It contains the following changes:

- bugfix: bug 1169: Fix blank popup conflict with Google Toolbar
- bugfix: bug 1171: Properly store and set network.dns.disablePrefetch
- bugfix: bug 1165: Fix an exception on toggle in FF3.6
- bugfix: bug 1163: Fix history loss in FF3.6
- bugfix: Fix a typo error during logging
- bugfix: Properly handle session restore in FF3.6
- misc: Kill a warning message about missing properties in window-mapper.js
- new: Add a new pref to disable Livemark updates during Tor usage (FF3.5+)

On December 21, 2009, we released an update to the -stable Tor branch, Tor 0.2.1.21. It fixes compatibility with newer OpenSSL libraries that work around the renegotiation bug. The full changelog is:  
 Tor 0.2.1.21 fixes an incompatibility with the most recent OpenSSL library. If you use Tor on Linux / Unix and you’re getting SSL renegotiation errors, upgrading should help. We also recommend an upgrade if you’re an exit relay.  
**Major bugfixes:**

- Work around a security feature in OpenSSL 0.9.8l that prevents our handshake from working unless we explicitly tell OpenSSL that we are using SSL renegotiation safely. We are, of course, but OpenSSL 0.9.8l won’t work unless we say we are.
- Avoid crashing if the client is trying to upload many bytes and the circuit gets torn down at the same time, or if the flip side happens on the exit relay. Bugfix on 0.2.0.1-alpha; fixes bug 1150.

**Minor bugfixes:**

- Do not refuse to learn about authority certs and v2 networkstatus documents that are older than the latest consensus. This bug might have degraded client bootstrapping. Bugfix on 0.2.0.10-alpha. Spotted and fixed by xmux.
- Fix a couple of very-hard-to-trigger memory leaks, and one hard-to- trigger platform-specific option misparsing case found by Coverity Scan.
- Fix a compilation warning on Fedora 12 by removing an impossible-to- trigger assert. Fixes bug 1173.

On December 31, 2009, we released Tor Browser Bundle 1.3.0. The major change was the upgrade of Firefox to the 3.5 branch. The full changelog is:

- upgrade Firefox to 3.5.6
- update Pidgin to 2.6.4
- update Torbutton to 1.2.4
- upgrade Tor to 0.2.1.21

**Design, develop, and implement enhancements that make  
Tor a better tool for users in censored countries.**  
Updated the get-tor email autoresponder to better handle translations into non-English languages. Also updated to better handle split downloads of torbrowser bundle and mac os x vidalia bundles.  
Mike finished his six week analysis of the Firefox 3.5 code base for privacy and anonymity leaks. The notes from the audit are documented in [https://www.torproject.org/torbutton/design/FF35\_AUDIT](https://www.torproject.org/torbutton/design/FF35_AUDIT "https://www.torproject.org/torbutton/design/FF35\_AUDIT").

**Grow the Tor network and user base. Outreach.**

- Jacob presented at the Arab Bloggers Conference in Beirut, Lebanon. [http://www.arabloggers.com/](http://www.arabloggers.com/ "http://www.arabloggers.com/")
- Jacob met with Al Jazeera in Doha, Qatar. [http://www.aljazeera.net/](http://www.aljazeera.net/ "http://www.aljazeera.net/")
- Jacob met with Rainbow House in Amman, Jordan.
- Andrew and Roger attended a circumvention technology workshop in California.
- Jacob, Roger, Karsten, Steven, and others attended 26C3 in Berlin, Germany. [http://events.ccc.de/congress/2009/wiki/index.php/Main\_Page](http://events.ccc.de/congress/2009/wiki/index.php/Main_Page "http://events.ccc.de/congress/2009/wiki/index.php/Main\_Page"). Jacob and Roger presented on ”Tor and censorship: lessons learned”, [http://events.ccc.de/congress/2009/Fahrplan/events/3554.en.html](http://events.ccc.de/congress/2009/Fahrplan/events/3554.en.html "http://events.ccc.de/congress/2009/Fahrplan/events/3554.en.html"). We mirrored the video and slides at [https://blog.torproject.org/blog/tor-and-censorship-lessons-learned](https://blog.torproject.org/blog/tor-and-censorship-lessons-learned "https://blog.torproject.org/blog/tor-and-censorship-lessons-learned").

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**  
On December 31, 2009, we released Tor Browser Bundle 1.3.0. The major change was the upgrade of Firefox to the 3.5 branch. The full changelog is:

- upgrade Firefox to 3.5.6
- update Pidgin to 2.6.4
- update Torbutton to 1.2.4
- upgrade Tor to 0.2.1.21

Mike, Roger, and Andrew met with the Chrome team at Google to discuss integration of Tor into Chrome’s ”incognito mode”. We need some APIs to make the integration smoother, and to be able to scale the Tor Network to handle the expected traffic from Chrome users.

**Scalability, load balancing, directory overhead, efficiency.**

- We did a one weekend test of the performance impact of changing circuit package window from 1000 cells to 101. The test and numbers are based on research by Csaba Kiraly. ”Effectof Tor window size on performance. Email to [or-dev@freehaven.net](mailto:or-dev@freehaven.net), February 2009. http://archives.seul.org/or/dev/Feb-2009/msg00000.html”. The test appeared to be a null operation, it didn’t help nor hurt performance of the network as a whole.
- Karsten continues to work on metrics about the Tor Network. We have a new metrics portal, [http://metrics.torproject.org/](http://metrics.torproject.org/ "http://metrics.torproject.org/") that shows the output, raw data, process for the collection, and the statistical analysis performed. Currently, our basic process is to collect, collate, and transform the data into graphs with R. Two organizations have offered to take the raw data from [http://archives.torproject.org/](http://archives.torproject.org/ "http://archives.torproject.org/") and import it into their data analysis products. We’re continuing to work on both tactics at this time.

**More reliable (e.g. split) download mechanism.**  
OS X split dmg files will be available with each release going forward. The split dmg files are a native format for OS X 10.3 (Panther) and above; so users on low bandwidth connections should easily be able to work with these.

**Translation work, ultimately a browser-based approach.**

- Hundreds of updated translations for torbutton, tor website, vidalia, torcheck, and get-tor in the following languages: Swedish, Brazillian Portugese, Polish, Russian, Spanish, Norwegian, Burmese, Chinese, Farsi, Arabic, Portugese, Ukranian, German, Spanish, French, Finnish, Italian, Dutch, and Turkish.
- Runa applied updates to the process of syncing between the translation portal and live website. And she continues to maintain the translation portal.
- Carolyn found translators for Russian, Ukrainian, and Burmese languages. She’s currently working on finding translators for Arabic, Farsi, and Spanish languages.

