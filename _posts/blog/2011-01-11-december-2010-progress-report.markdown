---
layout: post
title: "December 2010 Progress Report"
permalink: december-2010-progress-report
date: 2011-01-11
author: phobos
category: blog
tags: ["new packages", "new releases", "progress report", "scalability"]
---

 **New Releases**

- On December 14, we released updated Tor Browser Bundles for Windows, OSX, and  
Linux, [https://blog.torproject.org/blog/new-tor-browser-bundle-packages-0](https://blog.torproject.org/blog/new-tor-browser-bundle-packages-0 "https://blog.torproject.org/blog/new-tor-browser-bundle-packages-0")
- On December 17th, we released an updated -stable version of Tor, 0.2.1.28.  
Tor 0.2.1.28 does some code cleanup to reduce the risk of remotely exploitable  
bugs. Thanks to Willem Pinckaers for notifying us of the issue. The Common  
Vulnerabilities and Exposures project has assigned CVE-2010-1676 to this issue.  
We also took this opportunity to change the IP address for one of our directory  
authorities, and to update the geoip database we ship.  
 [https://blog.torproject.org/blog/tor-02128-released-security-patches](https://blog.torproject.org/blog/tor-02128-released-security-patches "https://blog.torproject.org/blog/tor-02128-released-security-patches")
- On December 17th, we released an updated -alpha version of Tor,  
0.2.2.20-alpha. Tor 0.2.2.20-alpha does some code cleanup to reduce the risk of remotely exploitable bugs. We also fix a variety of other significant bugs, change the IP address for one of our directory authorities, and update the minimum version  
that Tor relays must run to join the network. [https://blog.torproject.org/blog/tor-02220-alpha-out-security-patches](https://blog.torproject.org/blog/tor-02220-alpha-out-security-patches "https://blog.torproject.org/blog/tor-02220-alpha-out-security-patches")

**Enhancements that make Tor a better tool for users in censored  
countries.**

- Mike spent the past month and a half primarily working on preparing  
Torbutton for Firefox 4. This was a rather difficult task, as a lot has changed  
in this release, and the Javascript debugger doesn't yet support Firefox 4. The  
new mechanism works just fine for replacing XPCOM components. He also took the  
opportunity to clean up the code a bit. Firefox 3.5 and Firefox 4 both added  
some new APIs that make our job easier. We no longer rely so heavily on  
reimplementing pieces of Firefox using XPCOM re-registration. In fact, the only  
component we still need to hook is the external app launcher, to provide our  
warning message.
- Mike reviewed a proposed Chrome API at: [https://groups.google.com/a/chromium.org/group/chromium-dev/browse\_threa...](https://groups.google.com/a/chromium.org/group/chromium-dev/browse_thread/thread/4c318fb01062678a/89a11a7cbaa48d5f "https://groups.google.com/a/chromium.org/group/chromium-dev/browse\_thread/thread/4c318fb01062678a/89a11a7cbaa48d5f"). The main goal there was to try to steer them away from declarative models and more towards blocking callback APIs that will work better for us. We'll see if it works.

**Blocking Resistance**

Steven worked on plans of how to make Tor look more like other protocols, for  
when Tor's HTTPS-like cloaking is broken or someone blocks Tor along with HTTPS.  
The proposal is to allow Tor bridges to be configured to use one or more plugins  
which offer translation between Tor and obfuscated-Tor. There is now a proposal  
draft here:

[https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/idea...](https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/ideas/xxx-pluggable-transport.txt "https://gitweb.torproject.org/tor.git/blob/HEAD:/doc/spec/proposals/ideas/xxx-pluggable-transport.txt"). Steven wrote a first proof-of-concept (albeit not compliant with the proposal), for a HTTP-like protocol, and put the code here: [https://gitweb.torproject.org/sjm217/pluggable-transport.git](https://gitweb.torproject.org/sjm217/pluggable-transport.git "https://gitweb.torproject.org/sjm217/pluggable-transport.git"). A screenshot of the a Wireshark dump of Steven successfully accessing check.torproject.org is at: [http://www.cl.cam.ac.uk/~sjm217/volatile/pluggable-transport.png](http://www.cl.cam.ac.uk/~sjm217/volatile/pluggable-transport.png "http://www.cl.cam.ac.uk/~sjm217/volatile/pluggable-transport.png").

**Outreach and Advocacy**

- Karen spoke at the Reykjavík Digital Freedom Conference, [http://www.fsfi.is/radstefna2010/](http://www.fsfi.is/radstefna2010/ "http://www.fsfi.is/radstefna2010/").
- Erinn spoke at Moscow State University, [http://www.linux.org.ru/news/security/5624240](http://www.linux.org.ru/news/security/5624240 "http://www.linux.org.ru/news/security/5624240").
- Many tor people attended the CCC's 27C3,  
 [http://events.ccc.de/congress/2010/wiki/Main\_Page](http://events.ccc.de/congress/2010/wiki/Main_Page "http://events.ccc.de/congress/2010/wiki/Main\_Page").
- Karen participated in ``Hivos Digital Natives With a Cause?'' Thinkathon,  
 [http://www.hivos.net/Hivos-Knowledge-Programme/Themes/Digital-Natives-wi...](http://www.hivos.net/Hivos-Knowledge-Programme/Themes/Digital-Natives-with-a-Cause/Publications/Digital-Natives-with-a-Cause-Thinkathon-Position-Papers "http://www.hivos.net/Hivos-Knowledge-Programme/Themes/Digital-Natives-with-a-Cause/Publications/Digital-Natives-with-a-Cause-Thinkathon-Position-Papers").

**Bridge relay and bridge authority work**  
Jacob and Runa continue work on making it easy for people to become Tor bridge  
relays by default. The Torouter project is very much an alpha code quality project, but making progress on OpenWRT-based wireless access points and the Excito B3 hardware. The project page is kept up-to-date at [https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/Torouter](https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/Torouter "https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/Torouter").

**Scalability**

- Karsten wrote a technical report with an "Overview of Statistical Data in the Tor Network". The idea is to give this report to interested researchers who want to know what statistical data we have. The report is available at [https://metrics.torproject.org/papers/data-2010-12-29.pdf](https://metrics.torproject.org/papers/data-2010-12-29.pdf "https://metrics.torproject.org/papers/data-2010-12-29.pdf").
- Erinn and Sebastian worked on some Thandy & Hudson hacking accomplishing:  
1) Hudson and Windows finally cooperate, so now we can have a Windows autobuilder; and 2) setup a basic instance of Thandy-the secure software update platform.
- Mike did a quick modification to the TorFlow statsplitter.py script to have it output the results from the extra-info descriptors to give us breakdowns on port stats in more readable percentages, to compare the default exit policy of blutmagie to Amunet. It looks like the default exit policy causes you to write a heck of a lot more data, and over half of the read data is misc ports. Using these stats to produce new consensus weights to account for this seems like a good task to do.

**Translations**  
We fully migrated from our own Pootle-based translation system to Transifex, [https://www.transifex.net/projects/p/torproject/](https://www.transifex.net/projects/p/torproject/ "https://www.transifex.net/projects/p/torproject/"). A number of translations for various products have already come through for German, Arabic, Burmese, Simplified Chinese, Dutch, Finnish, French, Indonesian, Italian, Norwegian, Persian, Polish, and Romanian.

