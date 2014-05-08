---
layout: post
title: "December 2008 Progress Report"
permalink: december-2008-progress-report
date: 02/02/2009
author: phobos
category: blog
tags: ["alpha releases", "anonymity advocacy", "bug fixes", "progress report", "security fixes"]
---

 **Releases**  
Tor 0.2.1.8-alpha (released December 8) fixes some crash bugs in earlier alpha releases, builds better on unusual platforms like Solaris and old OS X, and fixes a variety of other issues.  
 [http://archives.seul.org/or/talk/Dec-2008/msg00129.html](http://archives.seul.org/or/talk/Dec-2008/msg00129.html "http://archives.seul.org/or/talk/Dec-2008/msg00129.html")

Tor Browser Bundle 1.1.6 (released December 2) and 1.1.7 (released December 12) update Tor to 0.2.1.8-alpha, include a new version of Firefox, and attempt to wrestle with the "AllowMultipleInstances=false" design that could allow us to run Tor Browser Bundle alongside a normal Firefox.  
 [https://svn.torproject.org/svn/torbrowser/trunk/README](https://svn.torproject.org/svn/torbrowser/trunk/README "https://svn.torproject.org/svn/torbrowser/trunk/README")

Tor 0.2.1.9-alpha (released December 25) fixes many more bugs, some of them security-related.  
 [http://archives.seul.org/or/talk/Jan-2009/msg00029.html](http://archives.seul.org/or/talk/Jan-2009/msg00029.html "http://archives.seul.org/or/talk/Jan-2009/msg00029.html")

**Bug fixes**  
Security fixes in the Tor 0.2.1.8-alpha release:  
 - When the client is choosing entry guards, now it selects at most one guard from a given relay family. Otherwise we could end up with all of our entry points into the network run by the same operator. Suggested by Camilo Viecco. Fix on 0.1.1.11-alpha.  
 - The "ClientDNSRejectInternalAddresses" config option wasn't being consistently obeyed: if an exit relay refuses a stream because its exit policy doesn't allow it, we would remember what IP address the relay said the destination address resolves to, even if it's an internal IP address. Bugfix on 0.2.0.7-alpha; patch by rovv.  
 - The "User" and "Group" config options did not clear the supplementary group entries for the Tor process. The "User" option is now more robust, and we now set the groups to the specified user's primary group. The "Group" option is now ignored. For more detailed logging on credential switching, set CREDENTIAL\_LOG\_LEVEL in common/compat.c to LOG\_NOTICE or higher. Patch by Jacob Appelbaum and Steven Murdoch. Bugfix on 0.0.2pre14. Fixes bug 848.

Performance scalability fixes from the Tor 0.2.1.9-alpha ChangeLog:  
 - Clip the MaxCircuitDirtiness config option to a minimum of 10 seconds. Warn the user if lower values are given in the configuration. Bugfix on 0.1.0.1-rc. Patch by Sebastian.  
 - Clip the CircuitBuildTimeout to a minimum of 30 seconds. Warn the user if lower values are given in the configuration. Bugfix on 0.1.1.17-rc. Patch by Sebastian.

Relay stability fixes from the Tor 0.2.1.9-alpha ChangeLog:  
 - Fix a logic error that would automatically reject all but the first configured DNS server. Bugfix on 0.2.1.5-alpha. Possible fix for part of bug 813/868. Bug spotted by coderman.  
 - When we can't initialize DNS because the network is down, do not automatically stop Tor from starting. Instead, retry failed dns\_init() every 10 minutes, and change the exit policy to reject \*:\* until one succeeds. Fixes bug 691.

Karsten discovered a bug where some directory authorities would take many minutes to send out a network status, because they were rate limiting too low. The short-term fix is to get those authorities to set  
 "MaxAdvertisedBandwidth 10 KB"  
in their torrc, so they don't spend as much of their bandwidth relaying ordinary Tor traffic.  
 [https://bugs.torproject.org/flyspray/index.php?do=details&id=847](https://bugs.torproject.org/flyspray/index.php?do=details&id=847 "https://bugs.torproject.org/flyspray/index.php?do=details&id=847")  
We need to consider longer-term solutions too, where clients actually recover more gracefully from this situation.

**Advocacy**  
We finally made our 3-year development roadmap public:  
 [https://blog.torproject.org/blog/our-three-year-development-roadmap-publ...](https://blog.torproject.org/blog/our-three-year-development-roadmap-published "https://blog.torproject.org/blog/our-three-year-development-roadmap-published")

Jillian York continued blogging for us about the good uses of Tor:  
 [http://www.knightpulse.org/blog/tor](http://www.knightpulse.org/blog/tor "http://www.knightpulse.org/blog/tor")

"Syria: Using Tor for Censorship Resistance", Dec 1  
 [http://www.knightpulse.org/blog/08/12/01/syria-using-tor-censorship-resi...](http://www.knightpulse.org/blog/08/12/01/syria-using-tor-censorship-resistance "http://www.knightpulse.org/blog/08/12/01/syria-using-tor-censorship-resistance")

"Australia Addresses Internet Circumvention", Dec 19  
 [http://www.knightpulse.org/blog/08/12/19/australia-addresses-internet-ci...](http://www.knightpulse.org/blog/08/12/19/australia-addresses-internet-circumvention "http://www.knightpulse.org/blog/08/12/19/australia-addresses-internet-circumvention")

Howcast produced a quick video for the masses on how to circumvent censorship. We were technical consultants for this video. It's tough to talk about Tor, when the first question you're trying to answer is "What is a proxy? And why do I care?" Howcast did a great job for a high-level overview of circumvention technologies in four minutes.  
 [https://blog.torproject.org/blog/how-circumvent-internet-proxy-howcast](https://blog.torproject.org/blog/how-circumvent-internet-proxy-howcast "https://blog.torproject.org/blog/how-circumvent-internet-proxy-howcast")

Wendy was a panelist at a conference organized by Paul Ohm and others at Colorado U at the beginning of December on law, wiretapping, and research-oriented data collection: "The Law and Ethics of Network Monitoring":  
 [http://www.silicon-flatirons.org/events.php?id=544](http://www.silicon-flatirons.org/events.php?id=544 "http://www.silicon-flatirons.org/events.php?id=544")

Roger, Karsten, Sebastian, Steven, Jacob, Mike, Peter, Wendy, Frank, Christian, and others attended the 25C3 conference in Berlin, Dec 27-30.  
Roger gave a talk there, similar to the DC08 talk but focusing entirely on 'present' and 'future': "Security and anonymity vulnerabilities in Tor: past, present, and future"  
 [http://freehaven.net/~arma/slides-25c3.pdf](http://freehaven.net/~arma/slides-25c3.pdf "http://freehaven.net/~arma/slides-25c3.pdf")

There was a workshop after Roger's talk on Germany and data retention. Sebastian Hahn was really great at representing Tor there, particularly because it was right after Roger's talk so he missed half of it, and because it was mostly in German. Roger tried to add the points that a) he really still does want to do Tor talks for German law enforcement (we got a few leads), and b) the major German Tor relay busts were in 2006-2007, not 2008, and maybe we're finally making progress.

Jacob was among the presenters at 25C3 on a talk about how they had managed to forge a root SSL certificate. In short, this meant that they could pretend to be any https site on the Internet, and no browser would complain. Nick wrote up a response explaining how it works and how it can affect Tor users:  
"The MD5 certificate collision attack, and what it means for Tor"  
 [http://blog.torproject.org/blog/md5-certificate-collision-attack%2C-and-...](http://blog.torproject.org/blog/md5-certificate-collision-attack%2C-and-what-it-means-tor "http://blog.torproject.org/blog/md5-certificate-collision-attack%2C-and-what-it-means-tor")

**New features**  
New feature from the Tor 0.2.1.8-alpha ChangeLog:  
 - New DirPortFrontPage option that takes an html file and publishes it as "/" on the DirPort. Now relay operators can provide a disclaimer without needing to set up a separate webserver. There's a sample disclaimer in contrib/tor-exit-notice.html.

We continued work on Thandy (our secure updater) this month.

Thandy itself is working smoothly at this point -- it can contact the central repository, check all the keys, look in the registry and compare the currently installed version to the new choices, fetch the right packages, check all the signatures, and launch the install.

We also now have a branch of Vidalia that has the GUI components for our updater in and working. It launches the updater to check for updates periodically, and there's a "check now" button. It does the update via Tor if Tor is up and running, and via direct connection otherwise.

We had hoped to be able to get away with patching our current .nsi Windows installer, but it turns out that "nsi silent (non-GUI) install" and "Vista" are not compatible concepts: Vista only likes MSI-based silent installs, due to that whole permissions thing that Vista gets so excited about.

So we now have a shiny new wxs-based msi installer for Tor on Windows:  
 [https://svn.torproject.org/svn/tor/trunk/contrib/tor.wxs.in](https://svn.torproject.org/svn/tor/trunk/contrib/tor.wxs.in "https://svn.torproject.org/svn/tor/trunk/contrib/tor.wxs.in")  
with buildbot-style output here:  
 [https://data.peertech.org/torbld](https://data.peertech.org/torbld "https://data.peertech.org/torbld")

The new installer has been tested for install, upgrade, repair and removal. But that's just Tor, and our recommended download bundle contains four components: Tor, Vidalia (the GUI), Torbutton (our Firefox extension), and either Privoxy or Polipo (an http proxy configured to use Tor -- we're migrating from Privoxy to Polipo).

So, the next step is to work on MSI installer files for the other three, plus a meta-msi file for the bundle. We're aiming to have a first go of that at the beginning of January. That way we can give a simpler demo of "download this bundle, then it will automatically notice that it should upgrade Tor, and it will fetch the new package and upgrade."

In other news, Roger had a long chat with Justin Cappos in early December. Justin did his PhD thesis on security of package managers, and is now a post-doc at UW working on (among other things) auto-update frameworks. See the beginning of a thread here:  
 [http://archives.seul.org/or/dev/Dec-2008/msg00010.html](http://archives.seul.org/or/dev/Dec-2008/msg00010.html "http://archives.seul.org/or/dev/Dec-2008/msg00010.html")

**Translations**  
We have our translation server up and online:  
 [https://translation.torproject.org/](https://translation.torproject.org/ "https://translation.torproject.org/")  
 [https://www.torproject.org/translation-portal](https://www.torproject.org/translation-portal "https://www.torproject.org/translation-portal")

We continued enhancements to the Chinese and Russian Tor website translations. Our Farsi translation from this summer is slowly becoming obsolete; we should solve that at some point.

