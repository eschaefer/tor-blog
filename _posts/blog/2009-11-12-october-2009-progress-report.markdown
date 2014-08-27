---
layout: post
title: "October 2009 Progress Report"
permalink: october-2009-progress-report
date: 2009-11-12
author: phobos
category: blog
tags: ["bug fixes", "enhancements", "progress report", "tor releases", "vidalia releases"]
---

 **New releases, new hires, new funding**  
Christian Fromme joins Tor to work on development and maintenance of the growing number of tools we’ve created over the past year. Christian is a great python hacker with a strong security mindset. He’s going to enhance and maintain the tools such as tor weather, get-tor, bridge database, tor control, tor flow, check.torproject.org, etc. Christian has been a volunteer developer for the past year helping to enhance get-tor, tor weather, and generally helping out with our python coding needs.

On October 10, we released Tor version 0.2.2.4-alpha. The release notes can be read at [https://blog.torproject.org/blog/tor-0224-alpha-released](https://blog.torproject.org/blog/tor-0224-alpha-released "https://blog.torproject.org/blog/tor-0224-alpha-released") or below:  
**Major bugfixes:**

- Fix several more asserts in the circuit build times code, for example one that causes Tor to fail to start once we have accumulated 5000 build times in the state file. Bugfixes on 0.2.2.2-alpha; fixes bug 1108.

**New directory authorities:**

- Move moria1 and Tonga to alternate IP addresses.

**Minor features:**

- Log SSL state transitions at debug level during handshake, and include SSL states in error messages. This may help debug future SSL handshake issues.
- Add a new ”Handshake” log domain for activities that happen during the TLS handshake.
- Revert to the ”June 3 2009” ip-to-country file. The September one seems to have removed most US IP addresses.
- Directory authorities now reject Tor relays with versions less than 0.1.2.14. This step cuts out four relays from the current network, none of which are very big.

**Minor bugfixes:**

- Fix a couple of smaller issues with gathering statistics. Bugfixes on 0.2.2.1-alpha.
- Fix two memory leaks in the error case of circuit build times parse state. Bugfix on 0.2.2.2-alpha.
- Don’t count one-hop circuits when we’re estimating how long it takes circuits to build on average. Otherwise we’ll set our circuit build timeout lower than we should. Bugfix on 0.2.2.2-alpha.
- Directory authorities no longer change their opinion of, or vote on, whether a router is Running, unless they have themselves been online long enough to have some idea. Bugfix on 0.2.0.6-alpha. Fixes bug 1023.

**Code simplifications and refactoring:**

- Revise our unit tests to use the ”tinytest” framework, so we can run tests in their own processes, have smarter setup/teardown code, and so on. The unit test code has moved to its own subdirectory, and has been split into multiple modules.

On October 11, we released Tor 0.2.2.5-alpha. The release notes can be read at [https://blog.torproject.org/blog/tor-0225-alpha-released](https://blog.torproject.org/blog/tor-0225-alpha-released "https://blog.torproject.org/blog/tor-0225-alpha-released") or below:  
**Major bugfixes:**

- Make the tarball compile again. Oops. Bugfix on 0.2.2.4-alpha.

**New directory authorities:**

- Move dizum to an alternate IP address.
- Code simplifications and refactorings
- Numerous changes, bugfixes, and workarounds from Nathan Freitas to help Tor build correctly for Android phones.

On October 14th we released Vidalia 0.2.5. The release notes can be read at [https://blog.torproject.org/blog/vidalia-025-released](https://blog.torproject.org/blog/vidalia-025-released "https://blog.torproject.org/blog/vidalia-025-released") or below:

- Add support in the Network settings page for configuring the Socks4Proxy and Socks5Proxy\* options that were added in Tor 0.2.2.1-alpha. Patch from Christopher Davis.
- Add a ”Automatically distribute my bridge address” checkbox (enabled by default) to the bridge relay settings options. (Ticket #524)
- Add ports 7000 and 7001 to the list of ports excluded by the IRC category in the exit policy configuration tab. (Ticket #517)
- Add a context menu for highlighted event items in the ”Basic” message log view that allows the user to copy the selected item text to the clipboard.
- Maybe fix a time conversion bug that could result in Vidalia displaying the wrong uptime for a relay in the network map. Stop trying to enforce proper quoting and escaping of arguments to be given to the proxy executable (e.g., Polipo). Now the user is on their own for properly formatting the command line used to start the proxy executable. (Ticket #523)

**Design, develop, and implement enhancements that make Tor a better tool for users in censored countries.**

Jacob and Nathan Frietas finished development of Orbot, a tor client and relay with a graphical control interface for the Android mobile operating system. More details can be found at [http://openideals.com/2009/10/22/orbot-proxy/](http://openideals.com/2009/10/22/orbot-proxy/ "http://openideals.com/2009/10/22/orbot-proxy/").

Karsten rewrote the directory archive script that evaluates whether an IP address was a relay at a given point in the past in Python.

Started comparing free and commercial GeoIP databases for their accuracy. It would be great if someone else (a student?) would pick up this work and move it forward.

**Grow the Tor network and user base. Outreach.**

- Andrew attended the Salzburg Global Seminar SIM Initiative 2020 Vision: Setting a Long-Term Agenda for Global Media Development from October 3 - 8. [http://www.salzburgglobal.org/2009/sim.cfm?nav=news&IDMedia=1](http://www.salzburgglobal.org/2009/sim.cfm?nav=news&IDMedia=1 "http://www.salzburgglobal.org/2009/sim.cfm?nav=news&IDMedia=1"). A quick writeup of the seminar was posted at [https://blog.torproject.org/blog/seminar-salzburg-global](https://blog.torproject.org/blog/seminar-salzburg-global "https://blog.torproject.org/blog/seminar-salzburg-global").
- Roger gave a talk at Drexel University, [https://www.cs.drexel.edu/research/colloquia](https://www.cs.drexel.edu/research/colloquia "https://www.cs.drexel.edu/research/colloquia").
- Andrew gave a talk about Freedom of Speech, Online Censorship, and Tor at the US Agency for International Development. It was attended by members of US AID, State Department, and National Security Staff from The White House.
- Roger, Jacob, Karsten, and Mike attended the 2009 Google Summer of Code Mentors Summit at Google HQ.
- Andrew gave a talk about Tor and its Privacy by Design at the 2009 Access and Privacy Workshop in Toronto, Canada. [http://www.verney.ca/onap2009/agenda\_dynamic.php](http://www.verney.ca/onap2009/agenda_dynamic.php "http://www.verney.ca/onap2009/agenda\_dynamic.php").
- Jacob gave a talk at the 25th NorduNet Conference, [http://www.nordu.net/conference/ndn2009web/welcome.html](http://www.nordu.net/conference/ndn2009web/welcome.html "http://www.nordu.net/conference/ndn2009web/welcome.html").
- Andrew, Wendy, and others were interviewed for a Tech Review article on Tor being blocked by the Chinese Government for the first time ever, [http://www.technologyreview.com/printer\_friendly\_article.aspx?id=23736](http://www.technologyreview.com/printer_friendly_article.aspx?id=23736 "http://www.technologyreview.com/printer\_friendly\_article.aspx?id=23736").
- Karsten attended EMANICS Workshop on Network Security in Bremen, Germany, and gave a 90-minute talk on Tor and my metrics work.
- Karsten and Sebastian attended PET-CON 2009.2 in Regensburg, Germany, and talked about measuring sensitive data in the Tor network.
- Finished paper on ”A Case Study on Measuring Statistical Data in the Tor Anonymity Network” together with Steven and Roger and submitted it to WECSR 2010.

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**  
Testing program updates to Tor Browser Bundle destined for the next release. The multi-protocol instant messaging client we use, Pidgin, includes voip and video chat functionality. Vidalia 0.2.5 inclusion to make the process of acquiring bridge addresses or becoming a bridge easier.

**Bridge relay and bridge authority work.**  
The bridge distribution backend is now far more reliable than it was, and the algorithm has been retuned with design from Nick and Roger. Now the bridgedb code is much more willing to hand out a user’s first few bridges, but it is much harder to get it to hand out a whole bunch of bridges.

**Scalability, load balancing, directory overhead, efficiency.**  
Nick rewrote the directory authority backend code to be able to provide multiple flavors of directory info: a new flavor that can be used for low-directory-bandwidth clients, and the existing flavor to support existing clients. This is the authority-side of proposals 158 and 162; once the authorities are migrated to this, we can start rolling out the client-side. Once it’s done, the directory overhead for clients should be dramatically reduced.

**More reliable (e.g. split) download mechanism.**  
Christian rolled out changes to the email auto-responder, get-tor, to better handle emails coming to us in various languages. 50% more emails are being answered correctly since the change.  
Thanks to some open internet activists in India, we have a fine new mirror of the Tor website in country at [http://www.torproject.org.in/](http://www.torproject.org.in/ "http://www.torproject.org.in/").  
4 new website mirrors joined, 4 existing mirrors left.

**Translation work**

- 6 German updates to the website.
- 114 Italian updates to Torbutton.
- 17 Italian updates to the website.
- Updated Arabic translation of Torbutton.
- Complete Burmese translation of Torbutton.
- Complete Burmese translation of Torcheck.
- Complete Danish translation of Torcheck.
- Brazilian translation of Torbutton.

