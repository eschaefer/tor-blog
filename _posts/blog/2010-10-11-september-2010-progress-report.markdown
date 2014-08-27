---
layout: post
title: "September 2010 Progress Report"
permalink: september-2010-progress-report
date: 2010-10-11
author: phobos
category: blog
tags: ["new hires", "progress report", "releases", "translation"]
---

 **New Hires**

- Tom Heydt-Benjamin is contracted full-time to work on NSF-related research through December 2010.
- Erinn Clark is contracted full-time to work on improving packaging, secure updater, tor browser bundles, and continuous integration systems through December 2010. Previously, Erinn was part-time.

**New Releases**

- Tor Browser Bundle for Mac OS X is now available for the i386 architecture in 11 languages. This is an alpha release to let the community test functionality. Read more at [https://blog.torproject.org/blog/tor-browser-bundle-mac-os-x](https://blog.torproject.org/blog/tor-browser-bundle-mac-os-x "https://blog.torproject.org/blog/tor-browser-bundle-mac-os-x")
- Orbot, Tor for Android, was released into the Android Market. Android users can now officially download and install Orbot on their devices. [https://guardianproject.info/apps/orbot/](https://guardianproject.info/apps/orbot/ "https://guardianproject.info/apps/orbot/")
- Version 0.2.10 of the graphical controller for tor, Vidalia, is now available. The main change is the use of Tor's native geoip database to map relay IP addresses to country. This removes the remote geoip resolution that occurred over Tor in previous versions of Vidalia. Read more at [https://blog.torproject.org/blog/vidalia-0210-released](https://blog.torproject.org/blog/vidalia-0210-released "https://blog.torproject.org/blog/vidalia-0210-released")
- Tor 0.2.2.16-alpha was released, Tor 0.2.2.16-alpha fixes a variety of old stream fairness bugs (most evident at exit relays), and also continues to resolve all the little  
bugs that have been filling up trac lately. [https://blog.torproject.org/blog/tor-02216-alpha-released](https://blog.torproject.org/blog/tor-02216-alpha-released "https://blog.torproject.org/blog/tor-02216-alpha-released")
- We released Torbutton 1.3.0-alpha. Torbutton 1.3.0-alpha is the first release of Torbutton where most of the code has come from our community members! The full announcement is available at [http://archives.seul.org/or/talk/Sep-2010/msg00140.html](http://archives.seul.org/or/talk/Sep-2010/msg00140.html "http://archives.seul.org/or/talk/Sep-2010/msg00140.html"). 
- Tor 0.2.2.17-alpha introduces a feature to make it harder for clients to use one-hop circuits (which can put the exit relays at higher risk, plus unbalance the network); fixes a big bug in bandwidth accounting for relays that want to limit their monthly bandwidth use; fixes a big pile of bugs in how clients tolerate temporary network failure; and makes our adaptive circuit build timeout feature (which improves client performance if your network is fast while not breaking things if your network is slow) better handle bad networks. [https://blog.torproject.org/blog/tor-02217-alpha-out](https://blog.torproject.org/blog/tor-02217-alpha-out "https://blog.torproject.org/blog/tor-02217-alpha-out")

**Design, develop, and implement enhancements that make Tor a better tool for users in censored countries.**  
Mike wrote up the current state of progress on a torbutton extension for Google's Chrome web browser, [https://blog.torproject.org/blog/google-chrome-incognito-mode-tor-and-fi...](https://blog.torproject.org/blog/google-chrome-incognito-mode-tor-and-fingerprinting "https://blog.torproject.org/blog/google-chrome-incognito-mode-tor-and-fingerprinting").

**Architecture and technical design docs for Tor enhancements related to blocking-resistance.**  
Steven submitted a proposal to automatically promote nodes to bridges. This proposal describes how Tor clients could determine when they have sufficient bandwidth capacity and are sufficiently reliable to become either bridges or Tor relays. When they meet this criteria, they will automatically promote themselves, based on user preferences. The proposal also defines the new controller messages and options which will control this process. [https://gitweb.torproject.org/tor.git/blob\_plain/HEAD:/doc/spec/proposal...](https://gitweb.torproject.org/tor.git/blob_plain/HEAD:/doc/spec/proposals/175-automatic-node-promotion.txt "https://gitweb.torproject.org/tor.git/blob\_plain/HEAD:/doc/spec/proposals/175-automatic-node-promotion.txt").

**Outreach and Advocacy**

- We released an article about the ``Ten Things to Look for in a Circumvention Tool''. As more countries crack down on Internet use, people around the world are turning to anti-censorship software that lets them reach blocked websites. Many types of software, also known as circumvention tools, have been created to answer the threat to freedom online. These tools provide different features and levels of security, and it's important for users to understand the tradeoffs. This article lays out ten features you should consider when evaluating a circumvention tool. The goal isn't to advocate for any specific tool, but to point out what kind of tools are useful for different situations. Full details at [https://www.torproject.org/press/2010-09-16-ten-things-circumvention-too...](https://www.torproject.org/press/2010-09-16-ten-things-circumvention-tools.html.en "https://www.torproject.org/press/2010-09-16-ten-things-circumvention-tools.html.en")
- Karen attended a meeting of the United Nations Internet Governance Forum in Vilnius, Lithuania. [http://igf2010.lt/](http://igf2010.lt/ "http://igf2010.lt/")
- Karen attended Ars Electronica in Linz, Austria. Tor received an Honorable Mention for Digital Communities. [http://aec.at](http://aec.at "http://aec.at")
- Karen attended Internet@Liberty in Budapest, Hungary. [https://sites.google.com/a/pressatgoogle.com/internet-at-liberty-2010/](https://sites.google.com/a/pressatgoogle.com/internet-at-liberty-2010/ "https://sites.google.com/a/pressatgoogle.com/internet-at-liberty-2010/") and [http://jilliancyork.com/tag/ial2010/](http://jilliancyork.com/tag/ial2010/ "http://jilliancyork.com/tag/ial2010/") for Jillian's summary.
- Sebastian gave a talk at SourceBarcelona about Anonymity, Privacy, and the real world. [http://www.sourceconference.com/index.php/barcelona-2010/bcn2010-schedul...](http://www.sourceconference.com/index.php/barcelona-2010/bcn2010-schedule#Jacob "http://www.sourceconference.com/index.php/barcelona-2010/bcn2010-schedule#Jacob")
- Nick and Andrew held a Boston Hackfest to explain Tor's internals, hack on some Tor simulator code, and generally be available for questions and help on topics relating to Tor. [https://blog.torproject.org/blog/boston-tor-hackers-join-us-sunday-septe...](https://blog.torproject.org/blog/boston-tor-hackers-join-us-sunday-september-19th "https://blog.torproject.org/blog/boston-tor-hackers-join-us-sunday-september-19th").

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**

- Erinn synchronized the Windows, OS X, and Linux tor browser bundles to use the same configurations and included software. 
- The TAILS team continues to improve and update their LiveCD available at [https://amnesia.boum.org](https://amnesia.boum.org "https://amnesia.boum.org").
- Jacob began an audit of the TAILS LiveCD to help assess the safety and security of the software for users in highly-volatile situations.

**Scalability, load balancing, directory overhead, efficiency.**  
Created Tor 0.2.3 branch and started work on integrated bufferevents and microdescriptors. Bufferevents are the proper way to manage heavy network i/o in Microsoft Windows. Microdescriptors are a way to let clients on extremely low-bandwidth connections bootstrap into the Tor network. Proposal 158, [https://gitweb.torproject.org/tor.git/blob\_plain/HEAD:/doc/spec/proposal...](https://gitweb.torproject.org/tor.git/blob_plain/HEAD:/doc/spec/proposals/158-microdescriptors.txt "https://gitweb.torproject.org/tor.git/blob\_plain/HEAD:/doc/spec/proposals/158-microdescriptors.txt"), defines microdescriptors.

**Translation work**

- We began the migration from our Pootle-based translation portal to Transifex after a discussion with their developers. Transifex provides free hosting of their translation software for free software projects and access to thousands of translators shared between hosted projects. All of our translations will be completed through Transifex going forward. [https://www.transifex.net/projects/p/torproject/](https://www.transifex.net/projects/p/torproject/ "https://www.transifex.net/projects/p/torproject/").
- Updated translations for Russian, Arabic, Persian, Greek, Burmese, French, Italian, Swedish, Dutch, German, Spanish, Polish, and Simplified Chinese.

