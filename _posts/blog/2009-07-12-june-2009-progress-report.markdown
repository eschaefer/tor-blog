---
layout: post
title: "June 2009 Progress Report"
permalink: june-2009-progress-report
date: 2009-07-12
author: phobos
category: blog
tags: ["anonymity advocacy", "bugfixes", "censorship circumvention", "progress report", "releases"]
---

 **New releases**

On June 20th we released Tor 0.2.1.16-rc.  
On June 21st, we released Tor Browser Bundle 1.2.1.  
On June 23rd, we released Tor Browser Bundle 1.2.2.  
On June 24th, we released Tor 0.2.0.35-stable. We expect that this release is the last of the 0.2.0.x -stable series, soon to be replaced with the 0.2.1.x series.  
On June 30th, we released Vidalia 0.1.14.

**Censorship circumvention**

Packaged rpms for Red Flag Linux version 6. Red Flag Linux is reported to be the new operating system for all Internet cafe's in China. So far, no one has seen this conversion actually happen, but now we're ready if it does.

Our email autoresponder, gettor , received a number of patches to deal with dkim issues, including finding a dkim bug that prevented yahoo email users from fetching Tor. This bug has been fixed. Additionally, we've whitelisted some domains where we  
see we're having lots of use but dkim isn't always configured properly. We've had thousands of users from China using gettor.

**Outreach/Advocacy**

Andrew, Roger, and Wendy attended Computers, Freedom, and Privacy 2009 Conference ( [http://www.cfp2009.org](http://www.cfp2009.org "http://www.cfp2009.org")). Andrew presented a “quicktake” talk on “Who uses Tor?”. Andrew and Roger, along with Paul Syverson, and a North African blogger, hosted a panel on “It Takes A Village To Be Anonymous”. Due to the sensitive situation surrounding the blogger, this panel was not recorded.

Andrew talked with the Committee to Protect Journalists ( [http://cpj.org](http://cpj.org "http://cpj.org")) about online security and circumvention tools.

Jillian C. York blogged at KnightPulse about “Average citizens browse anonymously  
”, [http://www.knightpulse.org/blog/09/06/04/average-citizens-browse-anonymo...](http://www.knightpulse.org/blog/09/06/04/average-citizens-browse-anonymously "http://www.knightpulse.org/blog/09/06/04/average-citizens-browse-anonymously")

Due to Iranian's usage of Tor during the recent election, the general press/media conducted a few interviews with Andrew:

1. Computer World, [http://www.computerworld.com/action/article.do?command=viewArticleBasic&...](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9134471&intsrc=news_ts_head "http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9134471&intsrc=news\_ts\_head")
2. Cnet News, [http://news.cnet.com/8301-13578\_3-10267287-38.html](http://news.cnet.com/8301-13578_3-10267287-38.html "http://news.cnet.com/8301-13578\_3-10267287-38.html")
3. Deutche Welle, [http://www.dw-world.de/dw/article/0,,4400882,00.html](http://www.dw-world.de/dw/article/0,,4400882,00.html "http://www.dw-world.de/dw/article/0,,4400882,00.html")
4. Technology Review, [http://www.technologyreview.com/web/22893/](http://www.technologyreview.com/web/22893/ "http://www.technologyreview.com/web/22893/")
5. Origo, in Hungary, [http://www.origo.hu/techbazis/internet/20090618-a-kiberforradalmarok-feg...](http://www.origo.hu/techbazis/internet/20090618-a-kiberforradalmarok-fegyverei-eszkozok-anonim-netezeshez.html "http://www.origo.hu/techbazis/internet/20090618-a-kiberforradalmarok-fegyverei-eszkozok-anonim-netezeshez.html")
6. O'Reilly, [http://radar.oreilly.com/2009/06/tor-and-the-legality-of-runnin.html](http://radar.oreilly.com/2009/06/tor-and-the-legality-of-runnin.html "http://radar.oreilly.com/2009/06/tor-and-the-legality-of-runnin.html")
7. Washington Times, [http://www.washingtontimes.com/news/2009/jun/26/protesters-use-navy-tech...](http://www.washingtontimes.com/news/2009/jun/26/protesters-use-navy-technology-to-avoid-censorship/?feat=home_headlines "http://www.washingtontimes.com/news/2009/jun/26/protesters-use-navy-technology-to-avoid-censorship/?feat=home\_headlines")
8. Arte TV video interview, the 30-minute video interview can't be put online, but will be shown to their viewers in late June/early July 2009. [http://www.arte.tv](http://www.arte.tv "http://www.arte.tv")
9. EFF, [http://www.eff.org/deeplinks/2009/06/help-protesters-iran-run-tor-relays...](http://www.eff.org/deeplinks/2009/06/help-protesters-iran-run-tor-relays-bridges "http://www.eff.org/deeplinks/2009/06/help-protesters-iran-run-tor-relays-bridges")
10. A Houston Radio station did an on-air interview, but didn't put the interview online.
11. A Romanian newspaper did an interview, but didn't put the story online.
12. Public Rado International did a more in-depth interview. They expect it to be on PBS Radio and BBC Radio 4 in early July 2009.

A number of blogs and other media picked up these original interviews and spread the word even further:

1. Wall Street Journal, [http://blogs.wsj.com/digits/2009/06/18/iranians-using-tor-to-anonymize-w...](http://blogs.wsj.com/digits/2009/06/18/iranians-using-tor-to-anonymize-web-use/ "http://blogs.wsj.com/digits/2009/06/18/iranians-using-tor-to-anonymize-web-use/")
2. CBS News, [http://www.cbsnews.com/blogs/2009/06/17/politics/politicalhotsheet/entry...](http://www.cbsnews.com/blogs/2009/06/17/politics/politicalhotsheet/entry5094825.shtml "http://www.cbsnews.com/blogs/2009/06/17/politics/politicalhotsheet/entry5094825.shtml")
3. [http://curtisschweitzer.net/blog/?p=2995](http://curtisschweitzer.net/blog/?p=2995 "http://curtisschweitzer.net/blog/?p=2995")
4. [http://voices.allthingsd.com/20090618/iranians-using-tor-to-anonymize-we...](http://voices.allthingsd.com/20090618/iranians-using-tor-to-anonymize-web-use/ "http://voices.allthingsd.com/20090618/iranians-using-tor-to-anonymize-web-use/")
5. [http://www.dailyfinance.com/2009/06/24/nokia-and-siemens-in-iran-controv...](http://www.dailyfinance.com/2009/06/24/nokia-and-siemens-in-iran-controversy/ "http://www.dailyfinance.com/2009/06/24/nokia-and-siemens-in-iran-controversy/")
6. [http://www.muslimnews.co.uk/news/news.php?article=16360](http://www.muslimnews.co.uk/news/news.php?article=16360 "http://www.muslimnews.co.uk/news/news.php?article=16360")

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**

Tor Browser Bundle 1.2.1 and 1.2.2 released in June. Planning a migration of the base operating system for the Incognito LiveCD to switch from Gentoo to an Ubuntu variant. We can always use help in maintaining Incognito.

**Scalability, load balancing, directory overhead, efficiency.**

June was spent documenting, stabilizing, and streamlining the bandwidth authority scanner, which has been runningfor a while on the Directory Authority named ides.

It is good enough to start running on multiple authorities now to produce actual results for clients to use.

**More reliable (e.g. split) download mechanism.**

Our email autoresponder, gettor , received a number of patches to deal with dkim issues, including finding a dkim bug that prevented yahoo email users from fetching Tor. This bug  
has been fixed. Additionally, we've whitelisted some domains where we see we're having lots of use but dkim isn't always configured properly. We've had thousands of users from China using gettor.

The Tor Check website (check.torproject.org) had a few bugs and we've fixed all but two. We sometimes still have false negatives (because the Tor client doesn't know to fetch the consensus at any specific time) and we also still sometimes barf python exceptions because mod\_python has some weird exception from time to time. We also accepted a patch from Marcus Greip that extends the TorBulkExitList to allow arbitrary ports rather than just port 80.

**Footprints from Tor Browser Bundle.**

Reduced the scanning for plugins Portable Firefox can do on launch of the application. There is still an issue where Firefox displays other plugins to users, but they aren't actually valid plugins and won't run on command. Firefox acquires the names through queries to the Windows Registry.

**Translations**

16 Polish website updates  
8 Italian website updates  
3 German website updates

