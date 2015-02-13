---
layout: post
title: "January 2011 Progress Report"
permalink: january-2011-progress-report
date: 2011-02-08 11:20:11
author: phobos
category: blog
status: closed
tags: ["anonymity features", "feature enhancements", "metrics", "progress report", "releases", "research reports"]
---

**New releases**

-   On January 4th, we released the latest in the alpha branch of torbutton,  
     version 1.3.1, see  
     [https://blog.torproject.org/blog/torbutton-alpha-131-released-testing](https://blog.torproject.org/blog/torbutton-alpha-131-released-testing "https://blog.torproject.org/blog/torbutton-alpha-131-released-testing")
-   On January 7th, A new release of arm was released, including enhancements  
     targeted at performance and cross platform compatibility. See,  
     [http://www.atagar.com/arm/](http://www.atagar.com/arm/ "http://www.atagar.com/arm/")
-   On January 9th, The Tor Browser Bundles were updated with some important  
     security fixes, see  
     [https://blog.torproject.org/blog/new-tor-browser-bundle-packages-1](https://blog.torproject.org/blog/new-tor-browser-bundle-packages-1 "https://blog.torproject.org/blog/new-tor-browser-bundle-packages-1")
-   On January 10th, we updated the OS X PPC packages after a long hiatus due to  
     failed hardware. They are now available in stable (0.2.1.28) and alpha  
     (0.2.2.20-alpha) versions, both with the latest Vidalia (0.2.10). See,  
     [https://blog.torproject.org/blog/new-ppc-packages-available](https://blog.torproject.org/blog/new-ppc-packages-available "https://blog.torproject.org/blog/new-ppc-packages-available")
-   On January 15th, we released the latest in the stable Tor series, version  
     Tor 0.2.1.29. See,  
     [https://blog.torproject.org/blog/tor-02129-released-security-patches](https://blog.torproject.org/blog/tor-02129-released-security-patches "https://blog.torproject.org/blog/tor-02129-released-security-patches")
-   On January 16, we released many updated packages. See,  
     [https://blog.torproject.org/blog/lots-new-tor-packages](https://blog.torproject.org/blog/lots-new-tor-packages "https://blog.torproject.org/blog/lots-new-tor-packages")
-   On January 15th, we released the latest in the Tor alpha series, version  
     0.2.2.21-alpha. See,  
     [https://blog.torproject.org/blog/tor-02221-alpha-out-security-patches](https://blog.torproject.org/blog/tor-02221-alpha-out-security-patches "https://blog.torproject.org/blog/tor-02221-alpha-out-security-patches")
-   On January 20th, the TAILS LiveCD/USB team released an updated version,  
     0.6.2. It is available at [http://amnesia.boum.org/news/version\_0.6.2/](http://amnesia.boum.org/news/version_0.6.2/ "http://amnesia.boum.org/news/version_0.6.2/").
-   On January 25th, we released Tor 0.2.2.22-alpha. See  
     [https://blog.torproject.org/blog/tor-02222-alpha-out](https://blog.torproject.org/blog/tor-02222-alpha-out "https://blog.torproject.org/blog/tor-02222-alpha-out")
-   Released new VisiTor version 0.0.4 that contains a Python version of the  
     weblog-parsing script contributed by Kiyoto Tamura and two minor fixes. See  
     [https://metrics.torproject.org/tools.html\#visitor](https://metrics.torproject.org/tools.html#visitor "https://metrics.torproject.org/tools.html#visitor")

**Design, develop, and implement enhancements that make Tor a better  
 tool for users in censored countries.**

-   From the 0.2.2.22-alpha release notes, Adjust our TLS Diffie-Hellman  
     parameters to match those used by Apache's mod\_ssl. This is a slight tweak to  
     Tor's TLS handshake that makes relays and bridges that run this new version  
     reachable from Iran again.
-   Started discussion of TLS normalization. The developer discussion is at  
     [http://archives.seul.org/or/dev/Jan-2011/msg00029.html](http://archives.seul.org/or/dev/Jan-2011/msg00029.html "http://archives.seul.org/or/dev/Jan-2011/msg00029.html").
-   Continued discussions of pluggable transports. The draft specification  
     can be found at  
     [https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/idea...](https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/ideas/xxx- "https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/ideas/xxx-")  
     pluggable-transport.txt. The start of the discussion can be found on the or-dev  
     mailing list at [http://archives.seul.org/or/dev/Jan-2011/msg00018.html](http://archives.seul.org/or/dev/Jan-2011/msg00018.html "http://archives.seul.org/or/dev/Jan-2011/msg00018.html").
-   Started discussion of Proposal 176 to change the version 3 handshake to  
     not use TLS renegotiation. Proposal 176 is at  
     [https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/176-...](https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/176-revising "https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/176-revising")  
     -handshake.txt. The developer discussion starts at  
     [http://archives.seul.org/or/dev/Jan-2011/msg00052.html](http://archives.seul.org/or/dev/Jan-2011/msg00052.html "http://archives.seul.org/or/dev/Jan-2011/msg00052.html").
-   Andrew and Roger documented the features in the Tor -alpha software that  
     allow users to use a SOCKS proxy as a circumvention method should Tor be blocked  
     in some manner. [https://www.torproject.org/docs/proxychain.html.en](https://www.torproject.org/docs/proxychain.html.en "https://www.torproject.org/docs/proxychain.html.en").

**Architecture and technical design docs for Tor enhancements  
 related to blocking-resistance.**

-   Continued discussions of pluggable transports. The draft specification  
     can be found at  
     [https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/idea...](https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/ideas/xxx- "https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/ideas/xxx-")  
     pluggable-transport.txt. The start of the discussion can be found on the or-dev  
     mailing list at [http://archives.seul.org/or/dev/Jan-2011/msg00018.html](http://archives.seul.org/or/dev/Jan-2011/msg00018.html "http://archives.seul.org/or/dev/Jan-2011/msg00018.html").

**Hide Tor's network signature.**

-   From the 0.2.2.22-alpha release notes, Adjust our TLS Diffie-Hellman  
     parameters to match those used by Apache's mod\_ssl. This is a slight tweak to  
     Tor's TLS handshake that makes relays and bridges that run this new version  
     reachable from Iran again.
-   Started discussion of TLS normalization. The developer discussion is at  
     [http://archives.seul.org/or/dev/Jan-2011/msg00029.html](http://archives.seul.org/or/dev/Jan-2011/msg00029.html "http://archives.seul.org/or/dev/Jan-2011/msg00029.html").
-   Continued discussions of pluggable transports. The draft specification  
     can be found at  
     [https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/idea...](https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/ideas/xxx- "https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/ideas/xxx-")  
     pluggable-transport.txt. The start of the discussion can be found on the or-dev  
     mailing list at [http://archives.seul.org/or/dev/Jan-2011/msg00018.html](http://archives.seul.org/or/dev/Jan-2011/msg00018.html "http://archives.seul.org/or/dev/Jan-2011/msg00018.html").
-   Started discussion of Proposal 176 to change the version 3 handshake to  
     not use TLS renegotiation. Proposal 176 is at  
     [https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/176-...](https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/176-revising "https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/176-revising")  
     -handshake.txt. The developer discussion starts at  
     [http://archives.seul.org/or/dev/Jan-2011/msg00052.html](http://archives.seul.org/or/dev/Jan-2011/msg00052.html "http://archives.seul.org/or/dev/Jan-2011/msg00052.html")

**Grow the Tor network and user base. Outreach.**

-   Held a successful public hackfest at MIT's Center for Future Civic  
     Media,  
     [https://blog.torproject.org/blog/boston-tor-hackers-join-us-saturday-jan...](https://blog.torproject.org/blog/boston-tor-hackers-join-us-saturday-january- "https://blog.torproject.org/blog/boston-tor-hackers-join-us-saturday-january-")  
     15th.
-   Due to the events in Egypt, Tor usage by activists, and human rights  
     organizations requesting our technical help, we were featured in over 30 news  
     stories, interviews, and articles. The master list of the media highlights is at  
     [https://www.torproject.org/press/inthemedia.html.en](https://www.torproject.org/press/inthemedia.html.en "https://www.torproject.org/press/inthemedia.html.en").

**Bridge relay and bridge authority work.**

-   Karsten did some work to publish sanitized bridge pool assignments. We're  
     going to publish the information which distribution pool a bridge is assigned  
     to. The distribution pool defines whether we're giving out bridges via HTTP,  
     via email, or not at all (reserved pool). The plan is to remove all sensitive  
     information from bridge pool assignments before making them available on  
     [https://metrics.torproject.org/data.html](https://metrics.torproject.org/data.html "https://metrics.torproject.org/data.html"). The discussion was started on  
     the or-dev list  
     at [http://archives.seul.org/or/dev/Jan-2011/msg00033.html](http://archives.seul.org/or/dev/Jan-2011/msg00033.html "http://archives.seul.org/or/dev/Jan-2011/msg00033.html").

**Scalability, load balancing, directory overhead, efficiency.**

-   We released an updated version of Tor  
     Weather, [https://weather.torproject.org](https://weather.torproject.org "https://weather.torproject.org"). Tor Weather is a web application used  
     to allow tor relay operators to sign up for notices when their relay is offline,  
     drops below a threshold of bandwidth served, and receive notifications when a  
     new version of tor is released. This version of the web application was written  
     by the Wesleyan University Humantarian Free and Open Source Software (HFOSS)  
     team working on Tor for their summer project, [http://hfoss.wesleyan.edu/](http://hfoss.wesleyan.edu/ "http://hfoss.wesleyan.edu/").
-   Karsten started improving metrics-db performance, so that it can scale to  
     five years of data with 10K relays and 5K bridges. This included a few tricks  
     to avoid parsing the same data twice. Also changed the database schema to use  
     SQL arrays to store bandwidth histories, which is apparently a less used part of  
     PostgreSQL, because he found a confirmed bug in PostgreSQL 8.2 (released  
     2006-12-05).
-   Karsten found two major, if not blocking, bugs in Torouter when run on the  
     suggested Buffalo hardware. The Excito hardware does not have these problems.  
     The bug numbers are 2334,  
     [https://trac.torproject.org/projects/tor/ticket/2334](https://trac.torproject.org/projects/tor/ticket/2334 "https://trac.torproject.org/projects/tor/ticket/2334"), and 2376,  
     [https://trac.torproject.org/projects/tor/ticket/2376](https://trac.torproject.org/projects/tor/ticket/2376 "https://trac.torproject.org/projects/tor/ticket/2376").
-   Karsten found and fixed a problematic bridge sanitizer bug that made us  
     keep original IP addresses in reject lines. Updated metrics-db and sanitized  
     all bridge descriptors since May 2008 once again. The latter kept two of our  
     computers busy for 2.5 weeks.
-   Karsten started with exporting bridge pool assignments and restarted  
     discussion about preserving hashed IP addresses in bridge descriptors.
-   Karsten upgraded Torperfs to output information about which circuits they  
     used for measuring download times. Made data available on metrics website.  
     Added new graphs combining all Torperf sources and showing the fraction of  
     timeouts and failures. Started Torperfs with custom entry guard selection  
     strategies.
-   Karsten talked to Björn Scheuermann and Florian Tschorsch about  
     performance improvements in Tor. Working on a patch with them to be included in  
     Tor 0.2.3.x.
-   Karsten improved graphs on metrics-web by adding more countries and by  
     allowing users to customize the graph image resolution.

**More reliable download mechanism.**

-   Sebastian and Erinn started to tackle Thandy and Hudson work. They solved  
     the Hudson issue on Windows and made a good deal of progress on getting Thandy  
     set up, understanding the different roles and responsibilities of each in the  
     Thandy system. Installing files by copying into the right place works, but the  
     packaging db that would be required for TBB is not yet working.

**Translations**

-   Updated translations for the following languages: af ak am arn ast be bg bn  
     bn\_IN csb cy dz eo eu fil fur ga gl gun ha he hi ht hu is it km kn kw lb ln lo  
     lt lv mg mi mk ml mn mr ms mt nah nap ne nn nso oc pa pap pms ps sco son sw ta  
     te tg th ti tk uk ur ve wa zh\_HK zu.

