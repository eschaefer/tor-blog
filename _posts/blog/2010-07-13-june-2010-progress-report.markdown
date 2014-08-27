---
layout: post
title: "June 2010 Progress Report"
permalink: june-2010-progress-report
date: 2010-07-13
author: phobos
category: blog
tags: ["advocacy", "measures of the tor network", "monthly status", "outreach", "progress report", "releases", "status report"]
---

 **New releases**

- On June 1, we released the latest Tor Browser Bundle for Linux, version 1.0.7. This is a compatibility release to allow the bundle to work on a wider variety of Linux distributions.
- On June 2, updated the Vidalia bundle for OS X PowerPC to include Vidalia 0.2.9.
- On June 14, we released orbot 0.0.8. This is a maintenance release to ﬁx issues discovered with Android 2.2.
- On June 17, Tor and the EFF released a Firefox extension called HTTPS Everywhere. The goal is to enable encrypted website viewing by default. More about this release at [https://blog.torproject.org/blog/https-everywhere-firefox-addon-helps-yo...](https://blog.torproject.org/blog/https-everywhere-firefox-addon-helps-you-encrypt-web-traffic "https://blog.torproject.org/blog/https-everywhere-firefox-addon-helps-you-encrypt-web-traffic").
- Damian continues to improve and release new versions of ARM, the console-based anonymizing relay monitor, [http://www.atagar.com/arm/](http://www.atagar.com/arm/ "http://www.atagar.com/arm/"). Consider it to be like the graphical control application, Vidalia, for relays without a graphical environment.

**Design, develop, and implement enhancements that make Tor a better tool for users in censored countries.**

- We updated the geoip mapping database to the Maxmind GeoLite Country database in tor after an analysis of various geoip mapping databases. The Maxmind GeoLite Country database has more accurate mappings for many parts of the world, such as Iran, SouthEast Asia, and many African countries.
- China’s Great Firewall continues blocking connections to the public Tor relays. They also updated their blocking to include bridge relays published via email and https websites. We conducted further research into the blocking mechanisms from inside China. A detailed analysis shows China GFW is blocking 90% of the published bridges in the https and smtp pools. The blocking is simply IP Address and TCP port combinations. Bridge relays that have been seeded into various social networks in China as well as new bridge addresses continue to work well.
- In late June, we started receiving many reports that Nigerian internet providers are blocking many circumvention tools, Tor included. Data about the blocking methods implemented are sparse right now, but we’re continuing to work with a few smart Nigerians to reverse-engineer the blocking regime. More details about this block at [https://blog.torproject.org/blog/dear-nigerians-help-us-help-you](https://blog.torproject.org/blog/dear-nigerians-help-us-help-you "https://blog.torproject.org/blog/dear-nigerians-help-us-help-you").

**Measures of the Tor Network**  
 [https://blog.torproject.org/files/exit-2010-06.png](https://blog.torproject.org/files/exit-2010-06.png "https://blog.torproject.org/files/exit-2010-06.png")  
This graph shows the total quantity of relays and quantity of exit relays in june 2010. Exit relay capacity is one of the potential bottlenecks that aﬀects the overall performance of Tor. The more exit relays we have, the faster it seems to browse the open Internet. As seen in late June, a researcher using PlanetLab hooked up 512 relays to the Tor network for their research into cloud computing and scaling eﬀects on the Tor Network. Before contacting PlanetLab, we removed all 512 nodes from the network consensus so users couldn’t use the suspect relays. We contacted the researcher and the relays were subsequently disabled.

[https://blog.torproject.org/files/networksize-2010-06.png](https://blog.torproject.org/files/networksize-2010-06.png "https://blog.torproject.org/files/networksize-2010-06.png")  
This graph shows the total quantity of relays and the total quantity of bridges in June 2010. The quantity of bridges is stable throughout the month. As seen in late June, a researcher using PlanetLab hooked up 512 relays to the Tor network for their research into cloud computing and scaling eﬀects on the Tor Network. Before contacting PlanetLab, we removed all 512 nodes from the network consensus so users couldn’t use the suspect relays. We contacted the researcher and the relays were subsequently disabled.

[https://blog.torproject.org/files/torperf-50kb-torperf-6m.png](https://blog.torproject.org/files/torperf-50kb-torperf-6m.png "https://blog.torproject.org/files/torperf-50kb-torperf-6m.png")  
This graphs shows how many seconds it took to complete a 50KB download from a standard Tor client. This measurement is from the server torperf, located in Chicago, Illinois. As you can see, latency dropped dramatically over the month for the second month in a row. We believe this is due to the ﬁxes for relays in 0.2.1.26 allow relays to handle older clients ﬂooding circuit requests to relays. As some relays were overloaded and dropped out of the network, the remaining relays had to handle an increasing load of users. Also, we have a budding competition between individuals looking to run the highest bandwidth relays. TorServersdotNet, [http://www.torservers.net/](http://www.torservers.net/ "http://www.torservers.net/"), starting running some very high bandwidth relays to increase performance and provide a way for non-technical users to support tor through combined ﬁnancial donations in exchange for Tor servers. We’re also looking to run this measurement software on a linux client connected to a standard dial-up modem to see how Tor fares in extremely low-bandwidth environments.

**Outreach and Advocacy**

- Andrew met with the Wesleyan University Humantarian Free and Open Source Software (HFOSS) team working on Tor for their summer project. They are ﬁxing up the Tor Weather application to allow for more features as requested by relay operators and attempting a start a Tor Status re-write, design, and update. [http://hfoss.wesleyan.edu/](http://hfoss.wesleyan.edu/ "http://hfoss.wesleyan.edu/").
- Jacob attended FooCamp 2010.
- Mike, along with Peter Eckersley from EFF, met with the Mozilla team to talk about web ﬁngerprinting, privacy, and Torbutton. Mike’s summary of their discussion is at [https://blog.torproject.org/blog/firefox-private-browsing-mode-torbutton...](https://blog.torproject.org/blog/firefox-private-browsing-mode-torbutton-and-fingerprinting "https://blog.torproject.org/blog/firefox-private-browsing-mode-torbutton-and-fingerprinting").
- Sebastian and Linus gave a Tor talk to the Netherlands Privacy group, PvIB ( [https://www.pvib.nl/home](https://www.pvib.nl/home "https://www.pvib.nl/home")). Their presentation is at [https://svn.torproject.org/svn/projects/presentations/pvib-2.pdf](https://svn.torproject.org/svn/projects/presentations/pvib-2.pdf "https://svn.torproject.org/svn/projects/presentations/pvib-2.pdf").
- Runa gave a Tor talk to Electronic Frontier Norway, [http://www.efn.no/](http://www.efn.no/ "http://www.efn.no/").
- We added an eigth directory authority called “maatuska“ hosted in Sweden.

**Preconﬁgured privacy (circumvention) bundles for USB or LiveCD.**  
Erinn continues to work on a Tor Browser Bundle for Apple’s OS X. Erinn continues to improve Tor Browser Bundle for Linux with feedback from initial users and other volunteer developers.

**Bridge relay and bridge authority work.**  
Andrew published a template conﬁguration ﬁle for tor relays to be a bridge automatically. It seems some relay operators are confused as to conﬁguring their relay as a bridge. The conﬁguration template is at [https://gitweb.torproject.org/tor.git/blob\_plain/HEAD:/src/config/torrc....](https://gitweb.torproject.org/tor.git/blob_plain/HEAD:/src/config/torrc.bridge.in "https://gitweb.torproject.org/tor.git/blob\_plain/HEAD:/src/config/torrc.bridge.in") and will be included in future Tor releases.

Andrew created some experimental “bridge by default“ bundles for Microsoft Windows. The idea is to use existing technology and see if we can get users to be bridges by default without any additional conﬁguration. Intitial testing shows it works well if the upstream router or NAT device has Universal Plug and Play (UPNP) enabled. The largest obstacle is still the manual conﬁguration of ﬁrewalls, routers, and NAT devices if UPNP is not enabled by default. More details about this experiment are at [https://blog.torproject.org/blog/technology-preview-bridge-default-micro...](https://blog.torproject.org/blog/technology-preview-bridge-default-microsoft-windows-clients "https://blog.torproject.org/blog/technology-preview-bridge-default-microsoft-windows-clients").

**Scalability, load balancing, directory overhead, eﬃciency.**  
Mike spent a lot of eﬀort and research into optimizing the circuit based timing (CBT) codebase. CBT is how clients measure the performance of their tor circuits to better optimize performance.  
The changelog of the ﬁxes is:  
• Major bugﬁxes:  
– Ignore negative and large timeout values that can happen during a suspend or hibernate. These values caused various asserts to ﬁre in the circuit build times code, crashing Tor. Bug 1245, bugﬁx on 0.2.2.2-alpha.  
– Alter calculation of Pareto distribution parameter ’Xm’ for Circuit Build Timeout learning to use the weighted average of the top N=3 modes. This should improve the timeout calculation in some cases, and prevent extremely high timeout values. Bug 1335, bugﬁx on 0.2.2.2-alpha.  
– Implement a ﬁltering step to recompute synthetic build times every time the timeoutchanges. Additionally, place a lower cap on synthetic build times, and allow this cap tobe controlled by the consensus. This should also improve the build time calculations,and should eliminate a case where Tor was allocating an excessive amount of temporary memory during timeout calculation. Bugs 1335 and 1245, bugﬁx on 0.2.2.2-alpha.

• Minor bugﬁxes:  
– Eliminate a case where a circuit build time warning was displayed after network connectivity resumed.

• Minor features:  
– Add a TIMEOUT\_RATE keyword to the BUILDTIMEOUT\_SET control port event, to give information on the current rate of circuit timeouts over our stored history.  
– Add ability to disable circuit build time learning via consensus parameter and via a  
LearnCircuitBuildTimeout conﬁg option. Also automatically disable circuit build time  
calculation if we are either a AuthoritativeDirectory, or if we fail to write our state ﬁle.  
Bug 1296.

Karsten web-enabled his ExoneraTor tool on the metrics website at [http://metrics](http://metrics "http://metrics").  
torproject.org/exonerator.html. ExoneraTor tells you whether there was a Tor relay running on a given IP address at a given time. Many legal advisors, lawyers, and law enforcement ask us for data regarding if a certain IP address hosted a Tor relay at a point in time. Now this data is easily available to all.

Karsten ﬁxed stats on estimated user numbers after we broke the calculations of users from directory request sampling at select relays. We found that we can use entry-stats for better user number estimates.

Karsten compared descriptor tarballs collected by ernie with directory-archive script and found that we’re ﬁne using ernie’s data. Ernie is the code that provides the data processing and backend for the metrics.torproject.org website.

**Footprints from Tor Browser Bundle.**

Erinn continues work on footprints of the Tor Browser Bundle for Linux and Apple OS X.

**Translation work, ultimately a browser-based approach.**

- A new translator, pierre, translated the entire website, torbutton, and gettor email autoresponder into French.
- Added pashto (Pakistani) to the portal by request.
- Updated translations for the website, torbutton, orbot, tor, and tor manual pages for French, Spanish, Russian, Mandarin Chinese, Farsi, Italian, Arabic, Dutch, Serbian, Portugese, Danish, Japanese, Polish, and Turkish.

<thead><tr>
<th>Attachment</th>
<th>Size</th> </tr></thead><tbody>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/exit-2010-06.png">exit-2010-06.png</a></td>
<td>15.94 KB</td> </tr>
 <tr class="even">
<td><a href="https://blog.torproject.org/files/networksize-2010-06.png">networksize-2010-06.png</a></td>
<td>16.06 KB</td> </tr>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/torperf-50kb-torperf-6m.png">torperf-50kb-torperf-6m.png</a></td>
<td>24.83 KB</td> </tr>
</tbody>

