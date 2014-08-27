---
layout: post
title: "November 2010 Progress Report"
permalink: november-2010-progress-report
date: 2010-12-16
author: phobos
category: blog
tags: ["enhancements", "fixes", "progress report", "translations"]
---

 **New Releases**

- On November 16 we released the latest in the Tor -alpha series. Tor 0.2.2.18-alpha fixes several crash bugs that have been nagging us lately, makes unpublished bridge relays able to detect their IP address, and fixes a wide variety of other bugs to get us much closer to a stable release. [https://blog.torproject.org/blog/tor-02218-alpha-available](https://blog.torproject.org/blog/tor-02218-alpha-available "https://blog.torproject.org/blog/tor-02218-alpha-available")
- On November 23, we released the latest in the Tor -stable series. Tor 0.2.1.27 makes relays work with OpenSSL 0.9.8p and 1.0.0.b --yet another OpenSSL security patch broke its compatibility with Tor. We also took this opportunity to fix several crash bugs, integrate a new directory authority, and update the bundled GeoIP database. [https://blog.torproject.org/blog/tor-02127-released](https://blog.torproject.org/blog/tor-02127-released "https://blog.torproject.org/blog/tor-02127-released")
- On November 21, we released the latest in the Tor -alpha series. Yet another OpenSSL security patch broke its compatibility with Tor: Tor 0.2.2.19-alpha makes relays work with OpenSSL 0.9.8p and 1.0.0.b. [https://blog.torproject.org/blog/tor-02219-alpha-out](https://blog.torproject.org/blog/tor-02219-alpha-out "https://blog.torproject.org/blog/tor-02219-alpha-out")
- On November 26, we released updated Tor Browser Bundles. There are new  
browser bundles out with the updated Tor versions (0.2.2.19-alpha and 0.2.1.27)  
that work with the latest OpenSSL. [https://blog.torproject.org/blog/new-tor-browser-bundle-packages](https://blog.torproject.org/blog/new-tor-browser-bundle-packages "https://blog.torproject.org/blog/new-tor-browser-bundle-packages")
- On November 30th, we released the latest Arm relay monitor. Damian writes,  
"What's new since August of 2009, you ask? Lots. The project has been under  
very active development, continuing to add usability improvements to make relay  
operation nicer and less error prone. If you're really curious what I've been up  
to this last year then it's all available in the change log."  
For those unfamiliar, arm is a terminal monitor for Tor relays and, to a growing  
extent, end users. [https://blog.torproject.org/blog/arm-release-140](https://blog.torproject.org/blog/arm-release-140 "https://blog.torproject.org/blog/arm-release-140")

**Advocacy**

- We released our first ever Annual Report for 2009. It highlights what we've accomplished in 2009. [https://www.torproject.org/about/financials.html.en](https://www.torproject.org/about/financials.html.en "https://www.torproject.org/about/financials.html.en")
- Andrew presented to the U.S. Dept of Commerce Information Systems Technical  
Advisory Committee (ISTAC) about Tor and its relation to US Export Controls.  
More about ISTAC can be found here, [http://tac.bis.doc.gov/ischart.htm](http://tac.bis.doc.gov/ischart.htm "http://tac.bis.doc.gov/ischart.htm").  
Andrew's presentation can be found at [https://svn.torproject.org/svn/projects/presentations/2010-11-03-ISTAC-t...](https://svn.torproject.org/svn/projects/presentations/2010-11-03-ISTAC-tor-circumvention-overview.pdf "https://svn.torproject.org/svn/projects/presentations/2010-11-03-ISTAC-tor-circumvention-overview.pdf")
- Linus and Erinn attended FSCONS as a guest speaker in Sweden, [http://fscons.org/](http://fscons.org/ "http://fscons.org/"). Erinn was invited back to be a main speaker next year. Linus' presentation can be found at [https://svn.torproject.org/svn/projects/presentations/FSCONS-2010.pdf](https://svn.torproject.org/svn/projects/presentations/FSCONS-2010.pdf "https://svn.torproject.org/svn/projects/presentations/FSCONS-2010.pdf").
- Erinn spoke at Codebits in Portugal about Tor, Free Software, and Anonymity,  
 [http://codebits.eu/](http://codebits.eu/ "http://codebits.eu/"). Her presentation can be found at [https://svn.torproject.org/svn/projects/presentations/2010-11-Codebits.p...](https://svn.torproject.org/svn/projects/presentations/2010-11-Codebits.pdf "https://svn.torproject.org/svn/projects/presentations/2010-11-Codebits.pdf").
- Andrew was interviewed for Internet Evolution, [http://www.internetevolution.com/radio.asp?doc\_id=196479](http://www.internetevolution.com/radio.asp?doc_id=196479 "http://www.internetevolution.com/radio.asp?doc\_id=196479") about Tor and online anonymity.
- Roger visited Nick Hopper's research group at UMN, [http://www-users.cs.umn.edu/~hopper/](http://www-users.cs.umn.edu/~hopper/ "http://www-users.cs.umn.edu/~hopper/"). He helped with a number of areas around a Tor simulator, how to anonymously collect Tor internal statistics, effect of guard nodes on security, how to model Tor user behavior, overlaying a censorship resistant publishing system, and some ideas on how to better count tor users anonymously.
- Jake and Karen attended a training held with Human Rights Watch and Access.

**Bridge relay work**  
Mike's initial research into bridges shows that we get 700-800 new bridges a day, but around 500 of them stay online and are reliable enough to give to users. We are developing ways to create more bridges through packaging that turns users into a bridge by default, a hardware router that acts as a bridge and transparent tor proxy, and creating images for cloud computing providers such as Amazon, Rackspace, and Microsoft. We're tracking the progress of these projects at:

- Bridge-by-default bundles, [https://trac.torproject.org/projects/tor/milestone/Experimental%20Bridge...](https://trac.torproject.org/projects/tor/milestone/Experimental%20Bridge%20Bundles "https://trac.torproject.org/projects/tor/milestone/Experimental%20Bridge%20Bundles")
- Hardware bridge/router, [https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/Torouter](https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/Torouter "https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/Torouter").
- Cloud computing images, [https://trac.torproject.org/projects/tor/wiki/sponsors/SponsorE/PhaseOne](https://trac.torproject.org/projects/tor/wiki/sponsors/SponsorE/PhaseOne "https://trac.torproject.org/projects/tor/wiki/sponsors/SponsorE/PhaseOne").

**Scalability, load balancing, directory overhead, efficiency**

- Sebastian and Nick spent some time debugging and resolving the issues with the OpenSSL changes to address a security announcement. The results of this work  
is included in the Tor 0.2.1.27 and 0.2.2.19-alpha releases. Initially, we did not see any direct relevance to Tor: [https://blog.torproject.org/blog/new-openssl-vulnerability-tor-not-affec...](https://blog.torproject.org/blog/new-openssl-vulnerability-tor-not-affected "https://blog.torproject.org/blog/new-openssl-vulnerability-tor-not-affected")
- Karsten implemented the new user number estimate based on directory requests to many directory mirrors in the metrics portal, [https://metrics.torproject.org/users.html](https://metrics.torproject.org/users.html "https://metrics.torproject.org/users.html").
- Karsten finished tech report on estimating user numbers together with Sebastian and with very helpful comments from Roger and Thomas. The report is available on the metrics website, [https://metrics.torproject.org/papers.html#techreports](https://metrics.torproject.org/papers.html#techreports "https://metrics.torproject.org/papers.html#techreports") and the specific report is at [https://metrics.torproject.org/papers/countingusers-2010-11-30.pdf](https://metrics.torproject.org/papers/countingusers-2010-11-30.pdf "https://metrics.torproject.org/papers/countingusers-2010-11-30.pdf").
- Karsten implemented a few Tor patches, most of them related to metrics, that  
were kindly reviewed and merged by Nick: made log granularity configurable (#1668, 0.2.3.x); included GeoIP database identifier in extra-info descriptors (#1883, 0.2.3.x); turned on dirreq-stats by default (#2174, 0.2.3.x); fixed a bug where fast relays exceeded the 50K limit for extra-info descriptors (#2183, 0.2.2.x); reduced exit-stats to top 10 ports (#2196, 0.2.2.x).
- Karsten implemented a few metrics website improvements: all servlets use a database connection pool for their queries; ExoneraTor uses the database tables instead of files; we upgraded to R 2.11.1 after finding out that the reshape package has a problem with large POSIXlt vectors.
- Karsten fixed the Python version of the VisiTor script that was contributed by Kiyoto Tamura. 
- Nick did some multithreaded crypto hacking, wrote the missing code to have clients fetch microdescriptors, and spent a good while longer bughunting in Tor,  
particularly for issues related to brokenness in and around openssl.
- Nick also spent a while chasing down more lingering Libevent bugs that don't affect Tor directly; having Libevent useful for more people means that we get more contributors for the Libevent codebase, which in turn helps Tor indirectly. Tor is heavily dependent on libevent, therefore the better libevent becomes, the better Tor becomes.

**Translations**  
We are migrating all translation work over to [https://www.transifex.net/projects/p/torproject/](https://www.transifex.net/projects/p/torproject/ "https://www.transifex.net/projects/p/torproject/"). Runa spent the month preparing the po/pot files for migration, committing translations still residing in pootle at translation.torproject.org.

