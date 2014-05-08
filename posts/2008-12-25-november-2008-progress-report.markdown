---
layout: post
title: "November 2008 Progress Report"
permalink: november-2008-progress-report
date: 12/25/2008
author: phobos
category: blog
tags: ["alpha release", "bug fixes", "hidden services", "progress report", "translations"]
---

 **Bug Fixes**

Tor 0.2.1.7-alpha (released November 8) fixes a major security problem in Debian and Ubuntu packages (and maybe other packages) noticed by Theo de Raadt, fixes a smaller security flaw that might allow an attacker to access local services, adds better defense against DNS poisoning attacks on exit relays, further improves hidden service performance, and fixes a variety of other issues.  
 [http://archives.seul.org/or/talk/Nov-2008/msg00229.html](http://archives.seul.org/or/talk/Nov-2008/msg00229.html "http://archives.seul.org/or/talk/Nov-2008/msg00229.html")

Tor 0.2.0.32 (released November 20) fixes a major security problem in Debian and Ubuntu packages (and maybe other packages) noticed by Theo de Raadt, fixes a smaller security flaw that might allow an attacker to access local services, further improves hidden service performance, and fixes a variety of other issues.  
 [http://archives.seul.org/or/announce/Dec-2008/msg00000.html](http://archives.seul.org/or/announce/Dec-2008/msg00000.html "http://archives.seul.org/or/announce/Dec-2008/msg00000.html")

Vidalia 0.1.10 (released November 2) fixes some presentation bugs and some bugs in the Windows installer.  
 [http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.10/CHAN...](http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.10/CHANGELOG "http://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.1.10/CHANGELOG")

In the Vidalia 0.1.10 stable release:  
 - Add a prettier dialog for prompting people for their control port password that also includes a checkbox for whether the user wants Vidalia to remember the entered password, a Help button, and a Reset button (Windows only).  
 - Fix a crash bug that occurred when the user clicks 'Clear' in the message log toolbar followed by 'Save All'.  
 - Uncheck the Torbutton options by default in the Windows bundle installer if Firefox is not installed.  
 - Add a Windows bundle installer page that warns the user that they should install Firefox, if it looks like they haven't already done so.

Security fixes in the Tor 0.2.1.7-alpha release:  
 - The "ClientDNSRejectInternalAddresses" config option wasn't being consistently obeyed: if an exit relay refuses a stream because its exit policy doesn't allow it, we would remember what IP address the relay said the destination address resolves to, even if it's an internal IP address. Bugfix on 0.2.0.7-alpha; patch by rovv.  
 - The "User" and "Group" config options did not clear the supplementary group entries for the Tor process. The "User" option is now more robust, and we now set the groups to the specified user's primary group. The "Group" option is now ignored. For more detailed logging on credential switching, set CREDENTIAL\_LOG\_LEVEL in common/compat.c to LOG\_NOTICE or higher. Patch by Jacob Appelbaum and Steven Murdoch. Bugfix on 0.0.2pre14. Fixes bug 848.

**Design Work**  
We have a preliminary proposal that suggests we use only one destination port per circuit. This came out of a discussion between Roger and Robert Hogan about how making an AIM connection through your circuit, and then also web browsing through it, can link the web browsing to your AIM login and you may not want that.  
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/ideas/xxx-se...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/ideas/xxx-separate-streams-by-port.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/ideas/xxx-separate-streams-by-port.txt")

We picked up the "proposal 141, clients do less directory downloading" design discussion again:  
 [http://archives.seul.org/or/dev/Nov-2008/msg00000.html](http://archives.seul.org/or/dev/Nov-2008/msg00000.html "http://archives.seul.org/or/dev/Nov-2008/msg00000.html")  
 [http://archives.seul.org/or/dev/Nov-2008/msg00001.html](http://archives.seul.org/or/dev/Nov-2008/msg00001.html "http://archives.seul.org/or/dev/Nov-2008/msg00001.html")  
 [http://archives.seul.org/or/dev/Nov-2008/msg00007.html](http://archives.seul.org/or/dev/Nov-2008/msg00007.html "http://archives.seul.org/or/dev/Nov-2008/msg00007.html")  
It looks like we have a plausible new direction to go, but nobody to write up the design proposal or implement it. I'm going to do the first go at the next design proposal in January, and hopefully somebody will have time to build it from there.

We continued extensive work on Thandy this month.

We have a Thandy repository up at  
 [http://updates.torproject.org/thandy/](http://updates.torproject.org/thandy/ "http://updates.torproject.org/thandy/")  
and its keys and location ship with the thandy client.

(The current repository is still for testing only, and we'll discard the keys and generate new ones when we want to put it up for real. We'll also get an ssl cert for it.)

The client-side of Thandy (teaching it how to decide which packages and bundles are out of date, and teaching it to download new files and check all the right signatures) exists now too. It supports download resuming, doing the download over Tor, etc.

The big picture is that thandy will remember what versions of each package and bundle are installed. Vidalia will periodically launch thandy-client so it can check for updates. When there are new packages, thandy will tell Vidalia (via stdout currently, since Vidalia launched it). Then when the time is right, Vidalia will launch thandy-client with a --install option, and thandy will know how to run the installers for each type of package (currently "rpm", "win32", and "none" are supported):  
 [https://svn.torproject.org/svn/updater/trunk/doc/interface.txt](https://svn.torproject.org/svn/updater/trunk/doc/interface.txt "https://svn.torproject.org/svn/updater/trunk/doc/interface.txt")

The long-term plan is to have every platform have a package system that is capable of answering "What version of the software is installed?" On Windows, that would either be the new MSI installer file we're working on:  
 [https://svn.vidalia-project.net/svn/vidalia/trunk/pkg/win32/vidalia.wxs....](https://svn.vidalia-project.net/svn/vidalia/trunk/pkg/win32/vidalia.wxs.in "https://svn.vidalia-project.net/svn/vidalia/trunk/pkg/win32/vidalia.wxs.in")  
or our current NSI installer, with a new registry key patch we're working on.

If an upgrade attempt fails (due to a broken package, broken system, sudden power loss, etc), thandy will try again the next time you tell it to install. With luck, it will work later, or an upgraded version of the package that \_does\_ work will come to be, and thandy will fetch and install that one instead.

We're working on patching our current Windows installer so it knows how to answer what version is installed. Then it will be easier for all the components to work together.

In short: many more components of our auto updater are coming together, but they aren't all together yet.

We've started to think about moving the Tor Browser Bundle from Firefox 2 to Firefox 3. This will mean we should measure new traces. We'll do it once Torbutton is known to be more stable on Firefox 3, which should happen in early 2009

**Translation**  
We have our translation server up and online:  
 [https://translation.torproject.org/](https://translation.torproject.org/ "https://translation.torproject.org/")  
 [https://www.torproject.org/translation-portal](https://www.torproject.org/translation-portal "https://www.torproject.org/translation-portal")

We now have a Romanian translation.

We continued enhancements to the Chinese and Russian Tor website translations. Our Farsi translation from this summer is slowly becoming obsolete; we should solve that at some point.

