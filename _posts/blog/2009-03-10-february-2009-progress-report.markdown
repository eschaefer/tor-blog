---
layout: post
title: "February 2009 Progress Report"
permalink: february-2009-progress-report
date: 2009-03-10
author: phobos
category: blog
tags: ["anonymity advocacy", "progress report", "translation"]
---

 **New releases, new hires, new funding**  
On February 8, we released versions 0.2.0.34-stable and 0.2.1.12-alpha.

Tor 0.2.0.34 features several more security-related fixes. You should upgrade, especially if you run an exit relay (remote crash) or a directory authority (remote infinite loop), or you're on an older (pre-XP) or not-recently-patched Windows (remote exploit).

This release marks end-of-life for Tor 0.1.2.x. Those Tor versions have many known flaws, and nobody should be using them. You should upgrade. If you're using a Linux or BSD and its packages are obsolete, stop using those packages and upgrade anyway.

**Enhancements**  
In Tor 0.2.1.12-alpha, if we're using bridges and our network goes away, be more willing to forgive our bridges and try again when we get an application request. Bugfix on 0.2.0.x.

Continued to develop research and coding items for improving Tor's performance using a number of techniques. We're focusing on six main reasons for slow performance: congestion control, tcp backoff, wrong window sizes at start, lack of priority for circuit control cells, and user load from peer to peer bulk data transfers.

We've implemented KDE Marble as an alternate visualization of the world into Vidalia. The first phase is to get a better 3-D globe for clients. The next phase is to enable “click to exit” so users can choose their country of preference for exit nodes. More on this coming in a future blog post.

**Outreach**  
Andrew and Roger attended an Open Society Institute Forum on, “The Future of Freedom and Control in the Internet Age”, [http://www.soros.org/initiatives/fellowship/events/freedom\_20090210](http://www.soros.org/initiatives/fellowship/events/freedom_20090210 "http://www.soros.org/initiatives/fellowship/events/freedom\_20090210"). Rebecca MacKinnon and Evgeny Morozov both mentioned Tor and its positive uses multiple times during the talk and subsequent Q&A.

Andrew attended Mobile Activism 4 Change barcamp on February 21. This generated some citizen media press about security, privacy, and anonymity in reference to the mobile activist world. You can read more at [http://barcamp.org/MobileTechForSocialChangeNewYork](http://barcamp.org/MobileTechForSocialChangeNewYork "http://barcamp.org/MobileTechForSocialChangeNewYork").

Jacob attended the InfoActivism camp, [http://www.informationactivism.org/](http://www.informationactivism.org/ "http://www.informationactivism.org/"), in Bangalore, India. He gave 20 presentations, trainings, and lectures on Tor.

Produced a guide to Tor and circumvention with the Center for Human Rights and Democracy in Saudi Arabia, [http://cdhr.info](http://cdhr.info "http://cdhr.info").

Worked with Global Voices ( [http://globalvoicesonline.org/](http://globalvoicesonline.org/ "http://globalvoicesonline.org/")) to update their guide to anonymous blogging with Tor and Wordpress; [http://advocacy.globalvoicesonline.org/projects/guide/](http://advocacy.globalvoicesonline.org/projects/guide/ "http://advocacy.globalvoicesonline.org/projects/guide/"). We recommend the Tor Browser Bundle by default, and provide clearer instructions and more pictures to assist users in getting configured quickly and securely.

There was a talk at BlackHat from Xinwen Fu. Our official response and thoughts on the topic are available at [https://blog.torproject.org/blog/one-cell-enough](https://blog.torproject.org/blog/one-cell-enough "https://blog.torproject.org/blog/one-cell-enough")

From Feb 6-9, Roger, Nick, Wendy, and Andrew attended ShmooconV, [http://shmoocon.org/](http://shmoocon.org/ "http://shmoocon.org/"), in February. Discussed Tor present and futures with many of the attendees.

End of Feb, Steven and Roger went to Financial Crypto 2009. We talked more with economics and "economics of information security" professors and researchers to get a better intuition about how to balance usability and load on the network. Steven also did a lightning talk on the "TLS footprint" arms race question: should we wait to fix known flaws, to slow down the arms race, or should we fix everything asap to discourage the censors from even trying?

Feb 17, Roger did a guest lecture on Tor in Drexel's senior-level computer  
security class.

In Feb we also met with the Freedom House ( [http://www.freedomhouse.org/](http://www.freedomhouse.org/ "http://www.freedomhouse.org/")), to help them understand how Tor works and to try to help with the trainings they're organizing.

Jillian C. York continued her blogging for Tor at KnightPulse with “From Tunisia to Japan: Anonymity Everywhere”, [http://www.knightpulse.org/blog/09/02/25/tunisia-japan-anonymity-everywh...](http://www.knightpulse.org/blog/09/02/25/tunisia-japan-anonymity-everywhere "http://www.knightpulse.org/blog/09/02/25/tunisia-japan-anonymity-everywhere")

**Tor bundles for USB drives or LiveCDs**  
On February 18, we released Tor Browser Bundle 1.1.9 with an updated Tor version to 0.2.1.12-alpha, Vidalia updated to 0.1.11, and Firefox 3.0.6. Andrew has taken over building the bundle to reduce the time between tor releases and bundles which include it. This should make PETER from the blog happy.

Updated the Incognito LiveCD TODO list to provide some more direction and tasks for the near future, [http://archives.seul.org/or/cvs/Feb-2009/msg00056.html](http://archives.seul.org/or/cvs/Feb-2009/msg00056.html "http://archives.seul.org/or/cvs/Feb-2009/msg00056.html")

We continued development and enhancement of TorVM with software updates to libevent, openwrt, vidalia, openvpn, tor, and win pcap. Enhanced the self-extraction and build scripts for easier creation by less technical users.

**Scalability, load balancing, directory overhead, and efficiency**  
We wrote up a summary of directory overhead work here:  
 [https://blog.torproject.org/blog/overhead-directory-info%3A-past%2C-pres...](https://blog.torproject.org/blog/overhead-directory-info%3A-past%2C-present%2C-future "https://blog.torproject.org/blog/overhead-directory-info%3A-past%2C-present%2C-future")

Csaba Kiraly has been doing research on how to reduce the overall load on the Tor network, while also reducing latency for clients: [http://archives.seul.org/or/dev/Feb-2009/msg00000.html](http://archives.seul.org/or/dev/Feb-2009/msg00000.html "http://archives.seul.org/or/dev/Feb-2009/msg00000.html")

**Alternate acquisition methods**  
Updated our get-tor email auto-responder to include more languages, added in the English version of the tor browser bundle, tested gmail download and resuming interrupted downloads, and fleshed out the design for easier localization of the message text and commands.

**Translation**  
We had a combined 113 commits across Polish, Chinese, Italian, German, Spanish, Russian, Argentinian, Brazilian Portuguese, and Romanian languages. 41 of these commits were through our translation portal.

