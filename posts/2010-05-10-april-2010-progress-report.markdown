---
layout: post
title: "April 2010 Progress Report"
permalink: april-2010-progress-report
date: 05/10/2010
author: phobos
category: blog
tags: ["alpha releases", "bug fixes", "enhancements", "metrics", "progress report", "tor browser bundle"]
---

 **New releases**

- On April 24, we released Tor 0.2.2.13-alpha. This version addresses the recent connection and memory overload problems we’ve been seeing on relays, especially relays with their DirPort open. If your relay has been crashing, or you turned it off because it used too many resources, give this release a try.

o Major bugfixes:  
 - Teach relays to defend themselves from connection overload. Relays  
 now close idle circuits early if it looks like they were intended  
 for directory fetches. Relays are also more aggressive about closing  
 TLS connections that have no circuits on them. Such circuits are  
 unlikely to be re-used, and tens of thousands of them were piling  
 up at the fast relays, causing the relays to run out of sockets  
 and memory. Bugfix on 0.2.0.22-rc (where clients started tunneling  
 their directory fetches over TLS).

o Minor features:  
 - Finally get rid of the deprecated and now harmful notion of "clique  
 mode", where directory authorities maintain TLS connections to  
 every other relay.  
 - Directory authorities now do an immediate reachability check as soon  
 as they hear about a new relay. This change should slightly reduce  
 the time between setting up a relay and getting listed as running  
 in the consensus. It should also improve the time between setting  
 up a bridge and seeing use by bridge users.  
 - Directory authorities no longer launch a TLS connection to every  
 relay as they startup. Now that we have 2k+ descriptors cached,  
 the resulting network hiccup is becoming a burden. Besides,  
 authorities already avoid voting about Running for the first half  
 hour of their uptime.

- On April 20, 2010 we released Tor 0.2.2.12-alpha. This release fixes a critical bug in how directory authorities handle and vote on descriptors. It was causing relays to drop out of the consensus.

Changes in version 0.2.2.12-alpha - 2010-04-20  
 o Major bugfixes:  
 - Many relays have been falling out of the consensus lately because  
 not enough authorities know about their descriptor for them to get  
 a majority of votes. When we deprecated the v2 directory protocol,  
 we got rid of the only way that v3 authorities can hear from each  
 other about other descriptors. Now authorities examine every v3  
 vote for new descriptors, and fetch them from that authority. Bugfix  
 on 0.2.1.23.  
 - Fix two typos in tor\_vasprintf() that broke the compile on Windows,  
 and a warning in or.h related to bandwidth\_weight\_rule\_t that  
 prevented clean compile on OS X. Fixes bug 1363; bugfix on  
 0.2.2.11-alpha.  
 - Fix a segfault on relays when DirReqStatistics is enabled  
 and 24 hours pass. Bug found by keb. Fixes bug 1365; bugfix on  
 0.2.2.11-alpha.

o Minor bugfixes:  
 - Demote a confusing TLS warning that relay operators might get when  
 someone tries to talk to their OrPort. It is neither the operator's  
 fault nor can they do anything about it. Fixes bug 1364; bugfix  
 on 0.2.0.14-alpha.

- On April 15, we released Tor 0.2.2.11-alpha. It fixes yet another instance of broken OpenSSL libraries that was causing some relays to drop out of the consensus.

o Major bugfixes:  
 - Directory mirrors were fetching relay descriptors only from v2  
 directory authorities, rather than v3 authorities like they should.  
 Only 2 v2 authorities remain (compared to 7 v3 authorities), leading  
 to a serious bottleneck. Bugfix on 0.2.0.9-alpha. Fixes bug 1324.  
 - Fix a parsing error that made every possible value of  
 CircPriorityHalflifeMsec get treated as "1 msec". Bugfix  
 on 0.2.2.7-alpha. Rename CircPriorityHalflifeMsec to  
 CircuitPriorityHalflifeMsec, so authorities can tell newer relays  
 about the option without breaking older ones.  
 - Fix SSL renegotiation behavior on OpenSSL versions like on Centos  
 that claim to be earlier than 0.9.8m, but which have in reality  
 backported huge swaths of 0.9.8m or 0.9.8n renegotiation  
 behavior. Possible fix for some cases of bug 1346.

o Minor features:  
 - Experiment with a more aggressive approach to preventing clients  
 from making one-hop exit streams. Exit relays who want to try it  
 out can set "RefuseUnknownExits 1" in their torrc, and then look  
 for "Attempt by %s to open a stream" log messages. Let us know  
 how it goes!  
 - Add support for statically linking zlib by specifying  
 --enable-static-zlib, to go with our support for statically linking  
 openssl and libevent. Resolves bug 1358.

o Minor bugfixes:  
 - Fix a segfault that happens whenever a Tor client that is using  
 libevent2's bufferevents gets a hup signal. Bugfix on 0.2.2.5-alpha;  
 fixes bug 1341.  
 - When we cleaned up the contrib/tor-exit-notice.html file, we left  
 out the first line. Fixes bug 1295.  
 - When building the manpage from a tarball, we required asciidoc, but  
 the asciidoc -> roff/html conversion was already done for the  
 tarball. Make 'make' complain only when we need asciidoc (either  
 because we're compiling directly from git, or because we altered  
 the asciidoc manpage in the tarball). Bugfix on 0.2.2.9-alpha.  
 - When none of the directory authorities vote on any params, Tor  
 segfaulted when trying to make the consensus from the votes. We  
 didn't trigger the bug in practice, because authorities do include  
 params in their votes. Bugfix on 0.2.2.10-alpha; fixes bug 1322.

o Testsuite fixes:  
 - In the util/threads test, no longer free the test\_mutex before all  
 worker threads have finished. Bugfix on 0.2.1.6-alpha.  
 - The master thread could starve the worker threads quite badly on  
 certain systems, causing them to run only partially in the allowed  
 window. This resulted in test failures. Now the master thread sleeps  
 occasionally for a few microseconds while the two worker-threads  
 compete for the mutex. Bugfix on 0.2.0.1-alpha.

- Tor Browser Bundle for GNU/Linux was updated throughout the month, from versions 1.0.1 to 1.0.4. The details are:  
1.0.4: Released 2010-04-24  
 Update Tor to 0.2.2.13-alpha

1.0.3: Released 2010-04-20  
 Update Tor to 0.2.2.12-alpha

1.0.2: Released 2010-04-18  
 Update Tor to 0.2.2.10-alpha  
 Update to Vidalia 0.2.8

1.0.1: Released 2010-04-08  
 Stop TBB from crashing when it tries to download files  
 Update Torbutton to 1.2.5

- On April 4, we released Tor Browser Bundle for Windows version 1.3.4. The changes were an update to Firefox 3.5.9 to address some security issues, and update the Torbutton Firefox extension to 1.2.5.
- On April 8, we released the latest Torbutton Firefox Extension version, 1.2.5. This release includes a number of bugfixes and some new features. The details are:

\* bugfix: bug 1169: Fix blank popup conflict with CoolPreviews  
 \* bugfix: bug 1246: Fix IST and other HH:30 timezone issues.  
 \* bugfix: bug 1219: Fix the toggle warning loop issue on settings change.  
 \* bugfix: bug 1321: Fix a session restore bug when closing the last window  
 \* bugfix: bug 1302: Update useragent to FF3.6.3 on WinNT6.  
 \* bugfix: bug 1157: Add logic to handle torbutton crashed state conflicts  
 \* bugfix: bug 1235: Improve the 'changed-state' refresh warning message  
 \* bugfix: bug 1337: Bind alert windows to correct browser window  
 \* bugfix: bug 1055: Make the error console the default log output location  
 \* bugfix: bug 1032: Fix an exception in the localhost proxy filter  
 \* misc: Always tell a website our window size is rounded even if it's not  
 \* misc: Add some suggestions to warning about loading external content  
 \* new: Add option to always update Torbutton via Tor. On by default  
 \* new: Redirect Google queries elsewhere on captcha (default ixquick)  
 \* new: Strip identifying info off of Google searchbox queries

- On April 11, we released Vidalia 0.2.8. It contains updated translations, updates to the universal plug and play libraries, and better compatibility with newer versions of the Nokia Qt toolkit.

o Stop using our custom dock icon implementation on OS X and just use  
 QSystemTrayIcon everywhere. Fixes the build on Snow Leopard.  
 (Ticket #562)  
 o Update the bundled CA certificates to re-enable downloading bridges  
 from bridges.torproject.org via SSL.  
 o Include a pre-configured qt.conf file in the Mac OS X bundles that  
 disable Qt plugin loading from the default directories. Otherwise,  
 users who have Qt installed in a system-wide location would end up  
 loading the libraries twice and crashing.  
 o Include libgcc\_s\_dw2-1.dll in the Windows installers, since Qt 4.6 now  
 depends on that DLL. Including the .dll is currently hardcoded, so the  
 Windows installer must be built using Qt 4.6. (Ticket #555)  
 o Update the included version of miniupnpc to 1.4.20100407.  
 o Add Burmese and Thai UI translations.

**Design, develop, and implement enhancements that make Tor a better tool for users in censored countries.**

Karsten did major backend processing work on the [http://metrics.torproject.org](http://metrics.torproject.org "http://metrics.torproject.org") data and website. These improvements allow for an automated process to update the various graphs and analyze the data sets. The whole system is better documented to assist someone in replicating the environment from scratch.

**Outreach and Advocacy**

- Jacob talked at SOURCE Boston about Tor, censorship circumvention, and running relays. [http://www.sourceconference.com/](http://www.sourceconference.com/ "http://www.sourceconference.com/"). Jacob's presentation can be found at [https://svn.torproject.org/svn/projects/presentations/SOURCE-Boston-2010...](https://svn.torproject.org/svn/projects/presentations/SOURCE-Boston-2010.pdf "https://svn.torproject.org/svn/projects/presentations/SOURCE-Boston-2010.pdf").
- Andrew lectured about anonymous communications and Tor at the Portland campus of the University of Southern Maine.
- Roger lectured about anonymous communications and Tor at the Albuquerque campus of the University of New Mexico.
- Andrew was interviewed by Radio Free Asia: Vietnam about using Tor for online privacy and anonymity. [http://www.rfa.org/vietnamese/in\_depth/TOR-free-anti-censorship-tool-KhA...](http://www.rfa.org/vietnamese/in_depth/TOR-free-anti-censorship-tool-KhAn%20-04262010195030.html "http://www.rfa.org/vietnamese/in\_depth/TOR-free-anti-censorship-tool-KhAn%20-04262010195030.html")

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**

Released new versions of Tor Browser Bundle for GNU/Linux and Windows. See above for details.

**Scalability, load balancing, directory overhead, efficiency.**

From the 0.2.2.12-alpha release notes:  
Directory authorities now do an immediate reachability check as soon as they hear about a new relay. This change should slightly reduce the time between setting up a relay and getting listed as running in the consensus. It should also improve the time between setting up a bridge and seeing use by bridge users.

In March, we changed a setting on a majority of the Directory Authorities called CircPriorityHalflifeMsec. Based upon research at the University of Waterloo, changing this setting could improve the overall performance of the network by fine tuning the earned weighted mean average bit bucket for better performance. Due to a bug in the CircPriorityHalflifeMsec parsing, the average latency in the network increased dramatically. At the same time, China unblocked the list of public and bridge relays, flooding hundreds of thousands of clients back into the network. It seems the network responded poorly to both events.

**More reliable (e.g. split) download mechanism.**

The GNU/Linux tor browser bundle with localizations was added to the get-tor email auto-responder.

Translation work, ultimately a browser-based approach.

- Updated text strings for the get-tor email auto-responder to make it easier for translators to complete the work.
- Added new translations of Vietnamese, Greek and Serbian to all projects.
- Many updated translated strings in German, Polish, Greek, Dutch, Finnish, Russian, Japanese, Chinese, French, Burmese, Spanish, Farsi, Arabic, Swedish, Turkish, and Norwegian.

