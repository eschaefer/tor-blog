---
layout: post
title: "June 2008 Progress Report"
permalink: june-2008-progress-report
date: 2008-07-22 22:25:34
author: phobos
category: blog
status: closed
tags: ["bridges", "openssl", "progress report", "tor", "tor browser bundle", "translations", "vidalia"]
---

Torbutton 1.2.0rc1 (released June 1), the first release candidate for the next stable series of the security-enhanced Torbutton Firefox extension, features functional support for Firefox 3. However, this support has not been extensively tested. In particular, timezone masking does not work at all. The workaround is to manually set the environment variable 'TZ' to 'UTC' before starting Firefox. This works on both Linux and Windows:  
 [http://archives.seul.org/or/talk/Jun-2008/msg00044.html](http://archives.seul.org/or/talk/Jun-2008/msg00044.html "http://archives.seul.org/or/talk/Jun-2008/msg00044.html")

Tor 0.2.0.27-rc (released June 3) adds a few features we left out of the earlier release candidates. In particular, we now include an IP-to-country GeoIP database, so controllers can easily look up what country a given relay is in, and so bridge relays can give us some sanitized summaries about which countries are making use of bridges. (See proposal 126-geoip-fetching.txt for details.)  
 [http://archives.seul.org/or/talk/Jun-2008/msg00055.html](http://archives.seul.org/or/talk/Jun-2008/msg00055.html "http://archives.seul.org/or/talk/Jun-2008/msg00055.html")

Torbutton 1.2.0rc2 (released June 8) features a fix for an annoying bug on MacOS, and adds much clamored for options to start Firefox in a specific Tor state:  
 [http://archives.seul.org/or/talk/Jun-2008/msg00103.html](http://archives.seul.org/or/talk/Jun-2008/msg00103.html "http://archives.seul.org/or/talk/Jun-2008/msg00103.html")

Tor 0.2.0.28-rc (released June 13) fixes an anonymity-related bug, fixes a hidden-service performance bug, and fixes a bunch of smaller bugs.  
 [http://archives.seul.org/or/talk/Jun-2008/msg00165.html](http://archives.seul.org/or/talk/Jun-2008/msg00165.html "http://archives.seul.org/or/talk/Jun-2008/msg00165.html")

Tor 0.2.1.1-alpha (released June 13) fixes a lot of memory fragmentation problems that were making the Tor process bloat especially on Linux; makes our TLS handshake blend in better; sends "bootstrap phase" status events to the controller, so it can keep the user informed of progress (and problems) fetching directory information and establishing circuits; and adds a variety of smaller features. [http://archives.seul.org/or/talk/Jun-2008/msg00185.html](http://archives.seul.org/or/talk/Jun-2008/msg00185.html "http://archives.seul.org/or/talk/Jun-2008/msg00185.html")

Vidalia 0.1.4 (released June 13) adds a bootstrap progress bar, UPnP support, a new set of freely licensed GUI icons, and fixes a few bugs. [**read more »**](https://blog.torproject.org/blog/june-2008-progress-report)
