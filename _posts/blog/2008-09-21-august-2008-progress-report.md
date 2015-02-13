---
layout: post
title: "August 2008 Progress Report"
permalink: august-2008-progress-report
date: 2008-09-21 18:05:39
author: phobos
category: blog
status: closed
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
 [https://svn.torproject.org/svn/torbrowser/trunk/README](https://svn.torproject.org/svn/torbrowser/trunk/README "https://svn.torproject.org/svn/torbrowser/trunk/README") [**read more »**](https://blog.torproject.org/blog/august-2008-progress-report)
