---
layout: post
title: "August 2008 Progress Report"
permalink: august-2008-progress-report
date: 09/22/2008
author: phobos
category: blog
tags: ["bridges", "incognito", "progress report", "releases", "stable release", "tor weather", "translations", "updates"]
---

 **Releases**

Vidalia 0.1.7 (released August 2) fixes a bug that caused Vidalia to not recognize Tor's version correctly in Tor 0.2.0.x, adds an "nsh2po" tool that helps Pootle translate the Vidalia bundle installer strings, adds "TZ=UTC" to the BrowserExecutable's environment variables when launched via Vidalia, and updates the Czech, French, and German translations.  
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.7/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.7/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.7/CHANGELOG")

Incognito 2008.1 (released August 2) is a Gentoo-based Tor LiveCD. This new release adds a "walkthrough" which will launch on startup; adds language support for Arabic, Green, Hebrew, Russian, and Swedish; improves the support for Chinese and Japanese fonts; adds support for VMWare and partial support for VirtualBox; switches to Tor 0.2.0.30 and Torbutton 1.2.0; and adds some new privacy-supporting software and removes some applications that are too likely to leak private information.  
 [https://svn.torproject.org/svn/incognito/trunk/ChangeLog](https://svn.torproject.org/svn/incognito/trunk/ChangeLog "https://svn.torproject.org/svn/incognito/trunk/ChangeLog")

Tor 0.2.1.3-alpha (released August 3) implements most of the pieces to prevent infinite-length circuit attacks (see proposal 110); fixes a bug that might cause exit relays to corrupt streams they send back; allows address patterns (e.g. 255.128.0.0/16) to appear in ExcludeNodes and ExcludeExitNodes config options; and fixes a big pile of bugs.  
 [http://archives.seul.org/or/talk/Aug-2008/msg00039.html](http://archives.seul.org/or/talk/Aug-2008/msg00039.html "http://archives.seul.org/or/talk/Aug-2008/msg00039.html")

Tor 0.2.1.4-alpha (released August 4) fixes a pair of crash bugs in 0.2.1.3-alpha.  
 [http://archives.seul.org/or/talk/Aug-2008/msg00039.html](http://archives.seul.org/or/talk/Aug-2008/msg00039.html "http://archives.seul.org/or/talk/Aug-2008/msg00039.html")

Tor Browser Bundle 1.1.2 (released August 9) updates Vidalia to version 0.1.6, updates Firefox to 2.0.0.16, updates Tor to 0.2.1.4-alpha, updates Torbutton to 1.2.0, and disables the TZ=UTC environment variable trick since Vidalia 0.1.7 now handles that for us.  
 [https://svn.torproject.org/svn/torbrowser/trunk/README](https://svn.torproject.org/svn/torbrowser/trunk/README "https://svn.torproject.org/svn/torbrowser/trunk/README")

Vidalia 0.1.8 (released August 17) makes the bandwidth graph window look better for languages like Farsi, includes ssleay32.dll in the Windows packages so Vidalia won't crash when it finds an incompatible version of ssleay32.dll in the user's $PATH, makes "escape" and "return" shortcuts for the settings window, and fixes a variety of other bugs.  
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.8/CHANG...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.8/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.8/CHANGELOG")

Tor 0.2.0.30 (released July 15, announced August 21) switches to a more efficient directory distribution design, adds features to make connections to the Tor network harder to block, allows Tor to act as a DNS proxy, adds separate rate limiting for relayed traffic to make it easier for clients to become relays, fixes a variety of potential anonymity problems, and includes the usual huge pile of other features and bug fixes.  
 [http://archives.seul.org/or/announce/Aug-2008/msg00000.html](http://archives.seul.org/or/announce/Aug-2008/msg00000.html "http://archives.seul.org/or/announce/Aug-2008/msg00000.html")

Tor Browser Bundle 1.1.3 (released August 22) fixes a bug in the 0.1.2 release that messed up translations in the homepage, adds "small=1" to the homepage URL so it doesn't show the huge green onion by default, and updates Vidalia to 0.1.8.  
 [https://svn.torproject.org/svn/torbrowser/trunk/README](https://svn.torproject.org/svn/torbrowser/trunk/README "https://svn.torproject.org/svn/torbrowser/trunk/README")

Tor 0.2.1.5-alpha (released August 31) moves us closer to handling IPv6 destinations, puts in a lot of the infrastructure for adding authorization to hidden services, lays the groundwork for having clients read their load balancing information out of the networkstatus consensus rather than the individual router descriptors, addresses two potential anonymity issues, and fixes a variety of smaller issues.  
 [http://archives.seul.org/or/talk/Sep-2008/msg00072.html](http://archives.seul.org/or/talk/Sep-2008/msg00072.html "http://archives.seul.org/or/talk/Sep-2008/msg00072.html")

**Blocking resistance**  
The Tor 0.2.1.3-alpha and 0.2.1.4-alpha releases include more fixes for hidden service performance and robustness, have slightly improved bootstrap status event behavior, and start hunting down a horrible bug that looks like it could leak private information:  
 [https://bugs.torproject.org/flyspray/index.php?do=details&id=779](https://bugs.torproject.org/flyspray/index.php?do=details&id=779 "https://bugs.torproject.org/flyspray/index.php?do=details&id=779")

Now that the Tor 0.2.0.30 release has been declared stable, ordinary users will finally get bridge features, the new harder-to-block network protocol, and other features by default.

**Core Development**  
We're working on a draft for a new "automatic software update" protocol, code-named Glider, that incorporates the previous proposals 153 and 154 but is easier to extend to other packages, and is easier to implement and maintain on the server side. We hope to have this new draft out as an actual proposal document, along with some early prototypes of the server side, in September.  
 [https://svn.torproject.org/svn/updater/trunk/specs/glider-spec.txt](https://svn.torproject.org/svn/updater/trunk/specs/glider-spec.txt "https://svn.torproject.org/svn/updater/trunk/specs/glider-spec.txt")  
Part of the ongoing development question is how to write the client side of this auto update engine in a convenient and easy language like Python, yet have it still be extremely compact on the client side -- since Windows doesn't include Python by default, shipping a Python interpreter with the auto updater could add 10MB to the package size.

Roger sent the list of "research directions we should look at" to or-dev, so more people could look at it:  
 [http://archives.seul.org/or/dev/Aug-2008/msg00031.html](http://archives.seul.org/or/dev/Aug-2008/msg00031.html "http://archives.seul.org/or/dev/Aug-2008/msg00031.html")  
We are working these items into a more comprehensive research and development roadmap; stay tuned.

**Advocacy**  
We answered a lot of press organizations about Tor and the Olympics this month. Our main goal was to explain to technical people how bridges work, what they're for, and explain that in most countries right now Tor works just fine out of the box, so bridges are the backup plan for later down the arms race. The CCC (and others) succeeded in making some good press articles, e.g.  
 [http://www.rsf.org/article.php3?id\_article=27991](http://www.rsf.org/article.php3?id_article=27991 "http://www.rsf.org/article.php3?id\_article=27991")  
 [http://www.guardian.co.uk/technology/2008/aug/07/censorship.hacking](http://www.guardian.co.uk/technology/2008/aug/07/censorship.hacking "http://www.guardian.co.uk/technology/2008/aug/07/censorship.hacking")  
 [http://www.guardian.co.uk/commentisfree/2008/aug/05/china.censorship](http://www.guardian.co.uk/commentisfree/2008/aug/05/china.censorship "http://www.guardian.co.uk/commentisfree/2008/aug/05/china.censorship")

Roger attended Black Hat and Defcon. His Defcon talk was:  
"Attacks/Vulnerabilities on Tor: past, present, future"  
Slides are at [http://freehaven.net/~arma/slides-dc08.pdf](http://freehaven.net/~arma/slides-dc08.pdf "http://freehaven.net/~arma/slides-dc08.pdf")  
He had a packed room of 500+ people. Lucky Green summarized his take-away from the talk as "we would love to work with you if you find any problems with Tor, and we have a good track record of working well with the community." That sounds like what we were aiming for. We're still waiting for the video to come out so we can link to it from the documentation page.

We also talked a lot with the Mozilla people about privacy-impacting bugs in Firefox. We have a list now:  
 [https://www.torproject.org/torbutton/design/#FirefoxBugs](https://www.torproject.org/torbutton/design/#FirefoxBugs "https://www.torproject.org/torbutton/design/#FirefoxBugs")  
and should start looking for good Firefox developers to fix them and funding to incent them to do so.

We put up our mid-August NLnet reports:  
 [https://www.torproject.org/projects/hidserv#Aug08](https://www.torproject.org/projects/hidserv#Aug08 "https://www.torproject.org/projects/hidserv#Aug08")  
 [https://www.torproject.org/projects/lowbandwidth#Aug08](https://www.torproject.org/projects/lowbandwidth#Aug08 "https://www.torproject.org/projects/lowbandwidth#Aug08")

Jacob spent a long week of hacking in Argentina, for DebConf 8 (the yearly Debian Conference). Lots of Tor advocacy. Another box of Tor stickers applied to many many laptops. Lots of people were interested in Tor and many many people installed Tor on both laptops and servers. This advocacy resulted in at least two new high bandwidth nodes that he helped the administrators configure. The first is in Japan. The second is our first major high bandwidth node in New Zealand.

Coverity (coverity.com) is now scanning Tor. It found a bunch of minor memory leaks, a few false positives, and some other miscellaneous bugs. Nick fixed almost all of the bugs in a quick afternoon, excepting some testing code that has some resource leaks. Jacob is going to work on getting other Tor related projects into Coverity.

Mike Perry has been working lately on publicity for moving more high-profile websites to use SSL correctly. Last year at Defcon he reported a bug in how many sites (including GMail) handle their cookies: he basically described an easy way for anybody in Starbucks to steal your GMail cookie and log into your gmail account, even if you are always very careful to only use "https" when logging in to your gmail account. The attack works because cookies \*can\* be set with an "only present this cookie on an SSL connection" flag when they're created, but no sites actually set this flag because they are concerned about usability. This attack is easy to perform as a Tor exit relay too. This year, Mike presented an actual tool that performs this attack on a local wireless network in an automated way. Some high-profile sites are slowly moving to use more secure login approaches.

Matt Edman finished running the "Vidalia logo design contest". The contest resulted in 76 entries. There were a lot of questionable submissions (Vidalia ninjas?!), but there were also a few great ones. He is tending towards this entry as his choice for the new Vidalia logo:  
 [http://www.worth1000.com/view.asp?entry=479229](http://www.worth1000.com/view.asp?entry=479229 "http://www.worth1000.com/view.asp?entry=479229")

**Usability**  
Incognito 2008.1 (released August 2) is a Gentoo-based Tor LiveCD. This new release adds a "walkthrough" which will launch on startup; adds language support for Arabic, Green, Hebrew, Russian, and Swedish; improves the support for Chinese and Japanese fonts; adds support for VMWare and partial support for VirtualBox; switches to Tor 0.2.0.30 and Torbutton 1.2.0; and adds some new privacy-supporting software and removes some applications that are too likely to leak private information.  
 [https://svn.torproject.org/svn/incognito/trunk/ChangeLog](https://svn.torproject.org/svn/incognito/trunk/ChangeLog "https://svn.torproject.org/svn/incognito/trunk/ChangeLog")

Incognito now comes with much more thorough documentation about which software packages are included, and how they are configured:  
 [http://www.browseanonymouslyanywhere.com/incognito/uploadfiles/docs.html](http://www.browseanonymouslyanywhere.com/incognito/uploadfiles/docs.html "http://www.browseanonymouslyanywhere.com/incognito/uploadfiles/docs.html")

Incognito's next step is to work on a "hardened" option that uses a more secure kernel and other applications. The goal is to keep the same usability but be even less vulnerable to application-level and kernel-level attacks that could be used to gain access to the system and then try to unveil the user.

Tor Browser Bundle 1.1.2 (released August 9) updates Vidalia to release 0.1.6, updates Firefox to 2.0.0.16, updates Tor to 0.2.1.4-alpha, updates Torbutton to 1.2.0, and disables the TZ=UTC environment variable trick since Vidalia 0.1.7 now handles that for us.  
 [https://svn.torproject.org/svn/torbrowser/trunk/README](https://svn.torproject.org/svn/torbrowser/trunk/README "https://svn.torproject.org/svn/torbrowser/trunk/README")

Tor Browser Bundle 1.1.3 (released August 22) fixes a bug in the 0.1.2 release that messed up translations in the homepage, adds "small=1" to the homepage URL so it doesn't show the huge green onion by default, and updates Vidalia to 0.1.8.  
 [https://svn.torproject.org/svn/torbrowser/trunk/README](https://svn.torproject.org/svn/torbrowser/trunk/README "https://svn.torproject.org/svn/torbrowser/trunk/README")

We're working on a new branch of Vidalia that can be used in Tor Browser Bundle, for launching Firefox directly without needing the extra installer scripts called "Firefox Portable". If we get this working, then we can hopefully make progress on running multiple Firefoxes at once (one used for Tor launched by TBB, and one used for non-Tor).  
 [http://trac.vidalia-project.net/browser/vidalia/branches/alt-launcher](http://trac.vidalia-project.net/browser/vidalia/branches/alt-launcher "http://trac.vidalia-project.net/browser/vidalia/branches/alt-launcher")

The German CCC organization put together a version of the Tor Browser Bundle called the "Freedom Stick" for use in teaching the media about the Chinese firewall and the Olympics:  
 [http://chinesewall.ccc.de/freedomstick-en.html](http://chinesewall.ccc.de/freedomstick-en.html "http://chinesewall.ccc.de/freedomstick-en.html")

**Scalability**  
From the Tor 0.2.1.5-alpha ChangeLog:  
"More progress toward proposal 141: Network status consensus documents and votes now contain bandwidth information for each router and a summary of that router's exit policy. Eventually this will be used by clients so that they do not have to download every known descriptor before building circuits."

We're worked on getting "Tor Weather" back up and working:  
 [https://weather.torproject.org/](https://weather.torproject.org/ "https://weather.torproject.org/")  
Weather is a service to let relay operators get notified when their relay is unreachable for an extended period of time. It's still in its early experimental stages, but it's already proved useful to its early testers. It's also using SSL as its base URL now.

Jacob has also been working on a Tor network map, to visualize where our relays are. Using all of the known descriptors, it maps each node with some GeoIP code and plot it onto a map. You can interact with the data to see the IP address of each node, the node name and the city/country information if we could find it. Sadly, it \*will\* lock your browser up for one or two minutes, as there's a lot of data to parse:  
 [http://freehaven.net/~ioerror/maps/v3-tormap.html](http://freehaven.net/~ioerror/maps/v3-tormap.html "http://freehaven.net/~ioerror/maps/v3-tormap.html")

