---
layout: post
title: "July 2009 Progress Report"
permalink: july-2009-progress-report
date: 2009-08-10
author: phobos
category: blog
tags: ["anonymity advocacy", "anonymity fixes", "bug fixes", "progress report", "security fixes", "stable releases", "tor browser bundle"]
---

 **New releases**

On July 8th, we released [Vidalia 0.1.15.](https://blog.torproject.org/blog/vidalia-0115-released).

On July 8th, we updated the Tor 0.2.0.35-stable bundles with the new Vidalia to fix an ssl issue and the Firefox Torbutton extension installation for OS X users.

On July 8th, we released [Tor 0.2.1.17-rc](https://blog.torproject.org/blog/tor-02117rc-released).

[Tor Browser Bundle 1.2.3](https://blog.torproject.org/blog/tor-browser-bundle-123-and-124-released) was released on July 8, 2009.  
 [TBB 1.2.3](https://blog.torproject.org/blog/tor-browser-bundle-123-and-124-released) was replaced by 1.2.4 on July 11, 2009  
 [TBB 1.2.5](https://blog.torproject.org/blog/tor-browser-bundle-125-and-126-released) was released on July 25th. It solely included an update to Tor 0.2.1.18 .  
 [TBB 1.2.6](https://blog.torproject.org/blog/tor-browser-bundle-125-and-126-released) was released on July 28th. It solely included an update to Tor 0.2.1.19.

On July 24th, we released [Tor 0.2.1.18](https://blog.torproject.org/blog/tor-02118-and-02119-released-stable).

On July 28th, we released [Tor 0.2.1.19](https://blog.torproject.org/blog/tor-02118-and-02119-released-stable).

**Make Tor a better tool for users in censored countries**

Tor 0.2.1.18 is our new stable. That is, this is the first stable release  
of the 0.2.1.x branch. The 0.2.0.x branch went stable in July of 2008.  
From the 0.2.1.18 release:

If the bridge config line doesn't specify a port, assume 443.  
This makes bridge lines a bit smaller and easier for users to  
understand.

If we're using bridges and our network goes away, be more willing  
to forgive our bridges and try again when we get an application  
request.

**Architecture and technical design docs for Tor enhancements related to blocking-resistance.**

Proposal 166 details four steps we're taking to safely collect data  
about Tor's network performance and network usage: 1) directory client  
counts by country, 2) entry guard client counts by country, 3) relay  
cell statistics, and 4) exit traffic by port and volume.  
 [https://git.torproject.org/checkout/tor/master/doc/spec/proposals/166-st...](https://git.torproject.org/checkout/tor/master/doc/spec/proposals/166-statistics-extra-info-docs.txt "https://git.torproject.org/checkout/tor/master/doc/spec/proposals/166-statistics-extra-info-docs.txt")

**Hide Tor's network signature**

Part of the reason why Tor might be especially slow in Iran could  
be that they're doing deep packet inspection (DPI) to throttle SSL  
connections. Tor's strategy of looking like SSL might turn out to be a  
bad move in this case. It's hard to tell whether the SSL throttling is  
actually happening, of course, because we get plenty of mixed information  
from our sources in Iran. But if it \*is\* happening, we should start  
investigating traffic obfuscation approaches that a) don't look like SSL,  
but b) don't look recognizably like any other protocol.

Some other Iran circumvention developers have come up with a patch to  
obfuscate ssh traffic:  
 [http://github.com/brl/obfuscated-openssh/tree/master](http://github.com/brl/obfuscated-openssh/tree/master "http://github.com/brl/obfuscated-openssh/tree/master")  
 [http://c-skills.blogspot.com/2008/12/sshv2-trickery.html](http://c-skills.blogspot.com/2008/12/sshv2-trickery.html "http://c-skills.blogspot.com/2008/12/sshv2-trickery.html")

Sometime soon we should start looking at designs to super-encrypt the  
Tor link traffic in this way.

**Grow the Tor network and user base. Outreach**

On July 1st, Andrew gave a detailed Tor talk at the National Cyber Forensics and Training Alliance. Andrew's blog about the event is at [https://blog.torproject.org/blog/visit-ncfta](https://blog.torproject.org/blog/visit-ncfta "https://blog.torproject.org/blog/visit-ncfta").

On July 7th, Andrew was a panelist for the CIMA/NED discussion on Iran and the Role of New Media, [http://cima.ned.org/events/new-media-in-iran.html](http://cima.ned.org/events/new-media-in-iran.html "http://cima.ned.org/events/new-media-in-iran.html"). Andrew's blog about the event is at [https://blog.torproject.org/blog/cimaned-panel-iran-and-new-media](https://blog.torproject.org/blog/cimaned-panel-iran-and-new-media "https://blog.torproject.org/blog/cimaned-panel-iran-and-new-media").

On July 15th, Andrew presented Tor at Webinno22, [http://www.webinnovatorsgroup.com/2009/07/06/the-webinno22-demo-companie...](http://www.webinnovatorsgroup.com/2009/07/06/the-webinno22-demo-companies/ "http://www.webinnovatorsgroup.com/2009/07/06/the-webinno22-demo-companies/"). Further discussions about online privacy startups and business deals with various investors and their seed companies are continuing since this event.

More press interviews and articles:

Iran activists work to elude crackdown on Internet, [http://www.google.com/hostednews/ap/article/ALeqM5hTf-p6Iy3sWHK8BRR58npG...](http://www.google.com/hostednews/ap/article/ALeqM5hTf-p6Iy3sWHK8BRR58npGosLC3AD99L01QO0 "http://www.google.com/hostednews/ap/article/ALeqM5hTf-p6Iy3sWHK8BRR58npGosLC3AD99L01QO0")

[http://blog.taragana.com/n/iran-government-builds-internet-walls-but-act...](http://blog.taragana.com/n/iran-government-builds-internet-walls-but-activists-still-slip-around-in-political-turmoil-119968/ "http://blog.taragana.com/n/iran-government-builds-internet-walls-but-activists-still-slip-around-in-political-turmoil-119968/")

Twitter and Facebook Help Protestors Connect, [http://www.outloud.com/2009/issue96/protest.html](http://www.outloud.com/2009/issue96/protest.html "http://www.outloud.com/2009/issue96/protest.html")

US set to hike aid aimed at Iranians, [http://www.boston.com/news/nation/washington/articles/2009/07/26/us\_to\_i...](http://www.boston.com/news/nation/washington/articles/2009/07/26/us_to_increase_funding_for_hackivists_aiding_iranians/ "http://www.boston.com/news/nation/washington/articles/2009/07/26/us\_to\_increase\_funding\_for\_hackivists\_aiding\_iranians/")

Senate OKs funds to thwart Iran Web censors , [http://www.washingtontimes.com/news/2009/jul/26/senate-help-iran-dodge-i...](http://www.washingtontimes.com/news/2009/jul/26/senate-help-iran-dodge-internet-censorship/ "http://www.washingtontimes.com/news/2009/jul/26/senate-help-iran-dodge-internet-censorship/")

We wrote a follow-up blog post about the number of people using Tor  
from Iran and China in June:  
 [https://blog.torproject.org/blog/measuring-tor-and-iran-part-two](https://blog.torproject.org/blog/measuring-tor-and-iran-part-two "https://blog.torproject.org/blog/measuring-tor-and-iran-part-two")

On July 1-5, Roger, Jake, Mike, and Damian attended Toorcamp in rural  
Washington State. Roger did a talk on current attacks and vulnerabilities  
in Tor.  
 [http://www.toorcamp.org/content/B4](http://www.toorcamp.org/content/B4 "http://www.toorcamp.org/content/B4")

On July 21-23, Roger attended a workshop in DC at the National Academy of  
Sciences. The workshop focused on the combination of Usability, Privacy,  
and Security, and where future funding should concentrate.

On July 31, Roger gave a Defcon talk on the current state of Tor's  
performance challenges and how we're addressing them:  
 [http://defcon.org/html/defcon-17/dc-17-speakers.html#Dingledine](http://defcon.org/html/defcon-17/dc-17-speakers.html#Dingledine "http://defcon.org/html/defcon-17/dc-17-speakers.html#Dingledine")  
 [http://freehaven.net/~arma/slides-dc09.pdf](http://freehaven.net/~arma/slides-dc09.pdf "http://freehaven.net/~arma/slides-dc09.pdf")

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**

[Tor Browser Bundle 1.2.3](https://blog.torproject.org/blog/tor-browser-bundle-123-and-124-released) was released on July 8, 2009.  
 [TBB 1.2.3](https://blog.torproject.org/blog/tor-browser-bundle-123-and-124-released) was replaced by 1.2.4 on July 11, 2009  
 [TBB 1.2.5](https://blog.torproject.org/blog/tor-browser-bundle-125-and-126-released) was released on July 25th. It solely included an update to Tor 0.2.1.18 .  
 [TBB 1.2.6](https://blog.torproject.org/blog/tor-browser-bundle-125-and-126-released) was released on July 28th. It solely included an update to Tor 0.2.1.19.

Upgraded many programs in Incognito to address security concerns and general bugfixes.

**Bridges**

Updated geoip database. From the 0.2.1.18 release:

If the bridge config line doesn't specify a port, assume 443.  
This makes bridge lines a bit smaller and easier for users to  
understand.

If we're using bridges and our network goes away, be more willing  
to forgive our bridges and try again when we get an application  
request.

**Scalability, load balancing, directory overhead, efficiency.**

From the 0.2.1.18 release:  
Network status consensus documents and votes now contain bandwidth  
information for each relay. Clients use the bandwidth values  
in the consensus, rather than the bandwidth values in each  
relay descriptor. This approach opens the door to more accurate  
bandwidth estimates once the directory authorities start doing  
active measurements. Implements part of proposal 141.

When building a consensus, do not include routers that are down.  
This cuts down 30% to 40% on consensus size. Implements proposal  
138.

Authorities now vote for the Stable flag for any router whose  
weighted mean time between failure (MTBF) is at least 5 days, regardless of the mean MTBF.

The main 2009 remaining performance changes are, in order of importance:  
- Get the bwauthority scripts into place so authorities are voting on  
 more accurate bandwidths.  
- Write a proposal for capping the circuit window much lower, and  
 implement it, and backport it to 0.2.1.x.  
- Proposal 151: Mike's plan to track circuit build times and give up on  
 the slow ones.  
- Write a proposal for refilling our bandwidth buckets intra-second.  
 Consider deploying in 0.2.2.x.  
- Figure out what we can do for a less fair round-robin between active  
 circuits. My intuition is heading towards "we don't know what effect  
 each possible change will make, and our other changes are going to  
 have big effects, so we shouldn't deploy anything here quite yet."  
- Get enough authorities upgraded that our bug 969 fixes ("voting wrong  
 on wfu and mtbf") take effect.

**More reliable (e.g. split) download mechanism.**

We have a new Volunteer, Jon, working on maintaining and expanding the list of tor mirrors. Jon has contacted all mirror maintainers and updated the mirrors list. Three were removed, two added, and seven updated with new information. There are 39 active mirrors.

**Translations**

10 Polish website updates  
7 French website updates  
1 Chinese website updates  
German torbutton translations updated  
Finnish torbutton translations updated  
Generate translation infrastructure for our email auto-responder.  
Ukrainian torbutton translation started  
Start of a Thai torbutton translation  
Spanish torbutton translation  
Ukrainian check.torproject.org translation  
Thai check.torproject.org translation

Our Google Summer of Code student, Runa, created a set of scripts to allow translators to translate our website content through the translation web portal. This will greatly simplify the process used to translate the website.

