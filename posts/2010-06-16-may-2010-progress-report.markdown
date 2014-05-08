---
layout: post
title: "May 2010 Progress Report"
permalink: may-2010-progress-report
date: 06/16/2010
author: phobos
category: blog
tags: ["advocacy", "conferences", "progress report", "speeches", "tor releases"]
---

 **New releases**

On May 26, Tor Browser Bundle for Microsoft Windows is updated to include the newer Vidalia 0.2.9. This ﬁxes some issues with character set handling, and adds Vietnamese as a new language.

On May 31, we released Tor Browser Bundle for Linux 1.0.6. It contains the following updates:

- Add arch to tarball name so there's no collision
- Add libpng for Arch Linux
- Add HTTPS Everywhere extension
- Update Qt to 4.6.2
- Update Vidalia to 0.2.9
- Update NoScript to 1.9.9.80

On June 1st, we released Tor Browser Bundle for Linux 1.0.7. It uses an older glibc for better compatibility with older linux distributions.

On May 20, we released Vidalia 0.2.9. Fixes include Qt 4.6.2 compatibility, new cert, and some new translations. You can download it at [https://www.torproject.org/vidalia/](https://www.torproject.org/vidalia/ "https://www.torproject.org/vidalia/"). Packages are slowly being updated to include this version of Vidalia.  
The full changelog is:

- Remove the GoDaddy CA certificate bundle since we changed the certificate used to authenticate connections to geoips.vidalia-project.net for downloading GeoIP information from a commercial GoDaddy certificate to a free CACert certificate.
- Define -D\_WIN32\_WINNT=0x0501 on Windows builds so that MiniUPnPc will build with the latest versions of MinGW.
- Modify miniupnpc.c from MiniUPnPc's source so that it will build on Mac OS X 10.4.
- Work around Qt's new behavior for the QT\_WA macro so that Vidalia will work correctly again on Windows with Qt >= 4.6.

On May 2nd, we released an updated stable version of Tor, 0.2.1.26.  
The detailed list of changes is:

o Major bugfixes:  
 - Teach relays to defend themselves from connection overload. Relays  
 now close idle circuits early if it looks like they were intended  
 for directory fetches. Relays are also more aggressive about closing  
 TLS connections that have no circuits on them. Such circuits are  
 unlikely to be re-used, and tens of thousands of them were piling  
 up at the fast relays, causing the relays to run out of sockets  
 and memory. Bugfix on 0.2.0.22-rc (where clients started tunneling  
 their directory fetches over TLS).  
 - Fix SSL renegotiation behavior on OpenSSL versions like on Centos  
 that claim to be earlier than 0.9.8m, but which have in reality  
 backported huge swaths of 0.9.8m or 0.9.8n renegotiation  
 behavior. Possible fix for some cases of bug 1346.  
 - Directory mirrors were fetching relay descriptors only from v2  
 directory authorities, rather than v3 authorities like they should.  
 Only 2 v2 authorities remain (compared to 7 v3 authorities), leading  
 to a serious bottleneck. Bugfix on 0.2.0.9-alpha. Fixes bug 1324.

o Minor bugfixes:  
 - Finally get rid of the deprecated and now harmful notion of "clique  
 mode", where directory authorities maintain TLS connections to  
 every other relay.

o Testsuite fixes:  
 - In the util/threads test, no longer free the test\_mutex before all  
 worker threads have finished. Bugfix on 0.2.1.6-alpha.  
 - The master thread could starve the worker threads quite badly on  
 certain systems, causing them to run only partially in the allowed  
 window. This resulted in test failures. Now the master thread sleeps  
 occasionally for a few microseconds while the two worker-threads  
 compete for the mutex. Bugfix on 0.2.0.1-alpha.

On May 19, we released an updated OrBot (Tor for Android), version 0.0.6, which contains Tor 0.2.2.13-alpha.

On May 26, we released an updated Orbot (Tor for Android), version 0.0.7, which contains a number of usability fixes reported by users. See the bugfixes [in trac](https://trac.torproject.org/projects/tor/query?status=closed&component=Android+(Orbot)-Backend+/+Core&order=priority&col=id&col=summary&col=status&col=type&col=priority&col=milestone&col=component&owner=).

**Design, develop, and implement enhancements that make Tor a better tool for users in censored countries.**

On May 4, China's Great Firewall began blocking connections to the public Tor relays. They also updated their blocking to include bridge relays published via email and https websites. Further research into the blocking mechanisms from inside China show they are simply blocking IP Address and TCP port combinations. Bridge relays that have been seeded into various social networks in China continue to work well.

Tor on the Android OS, called Orbot, continues progress. Work continues on a privacy-preserving web browser, Orweb, and other supporting applications to make Tor on Android more useful for daily users. Nathan got a Tor relay running on a Moons e-7001 “iRobot” tablet, [tor on a tablet](http://guardianproject.info/2010/05/25/tor-on-a-tablet).

**Grow the Tor network and user base. Outreach.**

- Jacob, Roger, Runa, and Linus talked to various NorduNet and SUNET people in Sweden. As a result, we have a new directory authority and bandwidth authority located within NorduNET.
- Erinn and Karen attended the Global Voices Summit 2010 in Santiago, Chile. There were a number of discussions about how to use Tor safely and its usage in activism. Erinn held a detailed Tor training for 5-10 activists in Spanish. [http://summit2010.globalvoicesonline.org](http://summit2010.globalvoicesonline.org "http://summit2010.globalvoicesonline.org")
- Roger gave a few talks as AUSCERT, [http://www.auscert.org.au/](http://www.auscert.org.au/ "http://www.auscert.org.au/")
- Roger was interviewed by The Australian about Internet censorship and privacy. [http://www.theaustralian.com.au/australian-it/call-to-join-tor-network-t...](http://www.theaustralian.com.au/australian-it/call-to-join-tor-network-to-fight-censorship/story-e6frgakx-1225870756466 "http://www.theaustralian.com.au/australian-it/call-to-join-tor-network-to-fight-censorship/story-e6frgakx-1225870756466")
- Roger was interviewed by ComputerWorld Australia about the relationship between China and Tor. [http://www.computerworld.com.au/article/347273/auscert\_2010\_china\_set\_ne...](http://www.computerworld.com.au/article/347273/auscert_2010_china_set_net_blackout_tiananmen_square_anniversary/ "http://www.computerworld.com.au/article/347273/auscert\_2010\_china\_set\_net\_blackout\_tiananmen\_square\_anniversary/")
- Jacob gave the keynote speech at CONFidence in Krakow, Poland, [http://2010.confidence.org.pl/](http://2010.confidence.org.pl/ "http://2010.confidence.org.pl/").
- Jacob, Christian, and others attended pH neutral in Berlin, Germany. [http://ph-neutral.darklab.org/](http://ph-neutral.darklab.org/ "http://ph-neutral.darklab.org/")
- Karen met with a sub-committee of the US Senate Intelligence Committee to discuss the fallacy of cyberwar.

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**  
Continued to work on Linux and Mac OS X tor browser bundles. The Mac version of TBB is going to use a sandboxing technology borrowed from IronFox. This should help minimize the footprint and security concerns about running TBB on OS X computers.

**Scalability, load balancing, directory overhead, efficiency.**  
From the 0.2.1.26 release notes, teach relays to defend themselves from connection overload. Relays now close idle circuits early if it looks like they were intended for directory fetches. Relays are also more aggressive about closing TLS connections that have no circuits on them. Such circuits are unlikely to be re-used, and tens of thousands of them were piling up at the fast relays, causing the relays to run out of sockets and memory. Bugfix on 0.2.0.22-rc (where clients started tunneling their directory fetches over TLS).

**Translation work, ultimately a browser-based approach.**

- Added the Android orbot application to the translation portal.
- By user request, add Serbian to the available languages.
- Translation updates for the following languages: Polish, Arabic, Greek, Serbian, Russian, Swedish, Chinese, Norwegian, Japanese, German, Spanish, Portugese, French, Dutch, Romanian, and Farsi.

