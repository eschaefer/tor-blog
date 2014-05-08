---
layout: post
title: "March 2009 Progress Report"
permalink: march-2009-progress-report
date: 04/13/2009
author: phobos
category: blog
tags: ["alpha release", "bug fixes", "progress report"]
---

 **New releases, new hires, new funding**

On March 9, we released Tor 0.2.1.13-alpha. It includes the following fixes and enhancements:

o Major bugfixes:  
 - Correctly update the list of which countries we exclude as exits, when the GeoIP file is loaded or reloaded. Diagnosed by lark. Bugfix on 0.2.1.6-alpha.

o Minor bugfixes (on 0.2.0.x and earlier):  
 - Automatically detect MacOSX versions earlier than 10.4.0, and  
 disable kqueue from inside Tor when running with these versions.  
 We previously did this from the startup script, but that was no  
 help to people who didn't use the startup script. Resolves bug 863.  
 - When we had picked an exit node for a connection, but marked it as  
 "optional", and it turned out we had no onion key for the exit,  
 stop wanting that exit and try again. This situation may not  
 be possible now, but will probably become feasible with proposal  
 158. Spotted by rovv. Fixes another case of bug 752.  
 - Clients no longer cache certificates for authorities they do not  
 recognize. Bugfix on 0.2.0.9-alpha.  
 - When we can't transmit a DNS request due to a network error, retry  
 it after a while, and eventually transmit a failing response to  
 the RESOLVED cell. Bugfix on 0.1.2.5-alpha.  
 - If the controller claimed responsibility for a stream, but that  
 stream never finished making its connection, it would live  
 forever in circuit\_wait state. Now we close it after SocksTimeout  
 seconds. Bugfix on 0.1.2.7-alpha; reported by Mike Perry.  
 - Drop begin cells to a hidden service if they come from the middle  
 of a circuit. Patch from lark.  
 - When we erroneously receive two EXTEND cells for the same circuit  
 ID on the same connection, drop the second. Patch from lark.  
 - Fix a crash that occurs on exit nodes when a nameserver request  
 timed out. Bugfix on 0.1.2.1-alpha; our CLEAR debugging code had  
 been suppressing the bug since 0.1.2.10-alpha. Partial fix for  
 bug 929.  
 - Do not assume that a stack-allocated character array will be  
 64-bit aligned on platforms that demand that uint64\_t access is  
 aligned. Possible fix for bug 604.  
 - Parse dates and IPv4 addresses in a locale- and libc-independent  
 manner, to avoid platform-dependent behavior on malformed input.  
 - Build correctly when configured to build outside the main source  
 path. Patch from Michael Gold.  
 - We were already rejecting relay begin cells with destination port  
 of 0. Now also reject extend cells with destination port or address  
 of 0. Suggested by lark.

o Minor bugfixes (on 0.2.1.x):  
 - Don't re-extend introduction circuits if we ran out of RELAY\_EARLY  
 cells. Bugfix on 0.2.1.3-alpha. Fixes more of bug 878.  
 - If we're an exit node, scrub the IP address to which we are exiting  
 in the logs. Bugfix on 0.2.1.8-alpha.

o Minor features:  
 - On Linux, use the prctl call to re-enable core dumps when the user  
 is option is set.  
 - New controller event NEWCONSENSUS that lists the networkstatus  
 lines for every recommended relay. Now controllers like Torflow  
 can keep up-to-date on which relays they should be using.  
 - Update to the "February 26 2009" ip-to-country file.  
On March 10, we released Tor Browser Bundle 1.1.10. It includes:  
Update Tor to 0.2.1.13-alpha  
Update Firefox to 3.0.7  
Update Pidgin to 2.5.5

On March 31, we released Tor Browser Bundle 1.1.11. It includes:  
Update Firefox to 3.0.8  
Add Italian language bundles  
Update Torbutton to 1.2.1  
Update Vidalia to 0.1.12

On March 21, we released Torbutton 1.2.1, it includes:  
bugfix: bug 773: Fixed Noscript conflict issue.  
bugfix: bug 866: Fixed conflict with ZoTero  
bugfix: bug 908: Make UserAgentSwitcher's 'default' button restore Torbutton's spoofed user agent if Tor is enabled.  
bugfix: bug 909: Get Torbutton to "properly" react to users changing their Firefox cookie lifetime settings as opposed to using the Torbutton interface.  
bugfix: bug 834: Fix session saving and startup issues  
bugfix: bug 875: Removed docShell == null popup during toggle for some users  
bugfix: bug 910: fixed a locale spoofing issue in navigator.appVersion  
bugfix: bug 747: Attempt to fix 'fullscreen' resizing issues.  
bugfix: Stop-gap timezone spoofing fix for Linux and Mac for FF3. Requires a one-line patch to Firefox for Windows to work.  
bugfix: Clear SSL Session IDs on toggle. (See FF Bug 448747)  
misc: bug 931: Added a socks v4 vs v5 version choice to custom prefs.  
misc: bug 836: redesign startup preference window to make it more understandable  
misc: Torbutton now presents itself as Windows FF3.0.7.

On March 16, we released TorVM 0.0.1 as a testing release for user feedback and testing. More about TorVM can be read at [https://www.torproject.org/torvm/](https://www.torproject.org/torvm/ "https://www.torproject.org/torvm/")

Vidalia 0.1.12 16-Mar-2009  
 o Fix a bug in the hidden service settings configuration class that  
 could lead to compile errors in Visual Studio and on IRIX.  
 o Fix a build error that occurred on IRIX when using the MIPSPro  
 compiler. Patch from Matthew Saunier.  
 o Remove two duplicated strings in the Spanish translation of Qt's  
 internal strings (qt\_es.po). The duplicated strings caused build  
 errors when building with Qt 4.5. (Ticket #469)  
 o Remove the code that altered PublishServerDescriptor when becoming a  
 bridge, since Tor handles that itself now, and ensure that BridgeRelay  
 is reset when going from bridge to just-a-client mode.  
 o Remove an unnecessary #include from helpbrowser.cpp.  
 o Add an application icon based on Tor's logo to the vidalia.desktop  
 file.

Vidalia 0.2.0 19-Mar-2009  
 o Add support for changing UI languages without having to restart  
 Vidalia.  
 o Add preliminary support for using the KDE Marble widget for the  
 network map. It's currently a compile-time option and is disabled by  
 default.  
 o Add support for displaying Tor's plaintext port warnings. Also gives  
 the user the option to disable future warnings.  
 o Add an interface for displaying the geographic distribution of  
 clients who have recently used a bridge operator's relay.  
 o Add tooltips to tree items in the help browser's table of contents. Some  
 of the help topic labels are a bit long.  
 o Switch to a simpler About dialog and move the license information to a  
 separate HTML-formatted display.  
 o Switch to a simpler drag-and-drop installer in the OS X bundles.  
 o Switch to an MSI-based installer on Windows.  
 o Clear the list of default CA certificates used by QSslSocket before adding  
 the only one we care about. Suggested by coderman.  
 o Support building with Visual Studio again.  
 o Add a Debian package structure from dererk.  
 o Updated Albanian, Czech, Finnish, Polish, Portuguese, Romanian,  
 Swedish, Turkish and many other translations.

The Vidalia 0.2.0 release was also posted to the blog,  
 [https://blog.torproject.org/blog/technology-preview-marble-and-vidalia02...](https://blog.torproject.org/blog/technology-preview-marble-and-vidalia020 "https://blog.torproject.org/blog/technology-preview-marble-and-vidalia020")

**Design, develop, and implement enhancements  
**  
The Torbutton 1.2.1 update fixes a number of bugs that protect users in censored countries. Continued work on TorVM for easier and safer usage of Tor. Continued development of the secure updater client for Tor.

**Architecture and technical design docs for Tor enhancements  
related to blocking-resistance.  
**  
Nick wrote up a blog entry describing our current plans for making  
libevent (and ultimately) Tor work well on Windows:  
 [https://blog.torproject.org/blog/some-notes-progress-iocp-and-libevent](https://blog.torproject.org/blog/some-notes-progress-iocp-and-libevent "https://blog.torproject.org/blog/some-notes-progress-iocp-and-libevent")

**Grow the Tor network and user base. Outreach.  
**  
Andrew attended the LibrePlanet 2009 conference, [http://www.fsf.org/associate/meetings/2009/](http://www.fsf.org/associate/meetings/2009/ "http://www.fsf.org/associate/meetings/2009/"). Discussed Tor, free network services, and free software.

Karsten, Sebastian, and others helped organize and then attended Pet-Con 2009, [http://www.pet-con.org/index.php/PET\_Convention\_2009.1](http://www.pet-con.org/index.php/PET_Convention_2009.1 "http://www.pet-con.org/index.php/PET\_Convention\_2009.1").

Nick wrote a blog post about the secure updater for Tor, codenamed Thandy, for Google's Open Source blog: [http://google-opensource.blogspot.com/2009/03/thandy-secure-update-for-t...](http://google-opensource.blogspot.com/2009/03/thandy-secure-update-for-tor.html "http://google-opensource.blogspot.com/2009/03/thandy-secure-update-for-tor.html")

Finished analyzing directory archives from February 2006 to February  
2009. This analysis gives a slightly better picture of the Tor network  
than the analysis of the 2008 data. The analysis shows that there is a  
clear trend reversal in the number of German relays in 2008, , but for other countries the number of relays has continued to increase.

[http://freehaven.net/~karsten/metrics/dirarch-2009-03-31.pdf](http://freehaven.net/~karsten/metrics/dirarch-2009-03-31.pdf "http://freehaven.net/~karsten/metrics/dirarch-2009-03-31.pdf")

On March 17, Roger attended a hearing at the US Sentencing Commission,  
where Seth Schoen from EFF was testifying in opposition to a new "if  
you use a proxy when committing a crime, it's a sophisticated crime so  
you get more jail-time" clause they were considering. It turned out one  
of the commissioners is an avid Tor user, so they were sympathetic to  
his testimony.

On March 24-25, Roger and Andrew met with the Psiphon team in Toronto.  
We taught them about Tor's perspective on blocking-resistance, and about  
our bridges design. We also helped review their future design plans. We  
still have concerns that their closed design and implementation will  
ultimately mean they are less effective than they could be, but it's  
good to have alternate circumvention approaches available.

Tor (in combination with EFF) got accepted to Google Summer of Code  
2009. Google will be funding roughly 5 students to work on Tor-related  
development projects over this coming summer:  
 [https://blog.torproject.org/blog/eff-and-tor-google-summer-code-2009](https://blog.torproject.org/blog/eff-and-tor-google-summer-code-2009 "https://blog.torproject.org/blog/eff-and-tor-google-summer-code-2009")  
Our current thoughts are to focus on porting Polipo to Windows; improving  
usability and features for Torbutton; working harder to get WML support  
into Pootle, so people can translate our website with a browser; and  
further work on Thandy to make it scale better when 100000 users all  
try to upgrade in the same day.

Hal Roberts released his Berkman Center report on the "landscape of  
circumvention technologies" as of 2007, which recommends Tor and Psiphon:  
 [https://blog.torproject.org/blog/berkman-2007-circumvention-landscape-an...](https://blog.torproject.org/blog/berkman-2007-circumvention-landscape-and-progress "https://blog.torproject.org/blog/berkman-2007-circumvention-landscape-and-progress")

Roger and Nick participated in the Codecon program committee, and helped  
to choose a variety of good development projects to showcase in April. Two  
of these turned out to be libevent (including the new Windows work),  
and Torflow:  
 [http://www.codecon.org/2009/program.html](http://www.codecon.org/2009/program.html "http://www.codecon.org/2009/program.html")

Roger had lunch on March 4 with Micah Sherr, a PhD student at Penn who  
is working on a new path selection algorithm for Tor, that tries to  
minimize path latency rather than maximize bandwidth. Roger poked some  
holes in his design, and hopefully will help him over the next few months  
to fix them. You can read more about Micah's design in Section 4.3 of the  
"performance.pdf" document.

We worked with Global Voices to help them update their "guide to blogging  
anonymously":  
 [https://blog.torproject.org/blog/updated-guide-blogging-anonymously](https://blog.torproject.org/blog/updated-guide-blogging-anonymously "https://blog.torproject.org/blog/updated-guide-blogging-anonymously")  
In particular, we updated it to include recommendations for using Tor  
Browser Bundle, since TBB didn't exist when the guide was first written.

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.  
**  
On March 10, we released Tor Browser Bundle 1.1.10. It includes:  
Update Tor to 0.2.1.13-alpha  
Update Firefox to 3.0.7  
Update Pidgin to 2.5.5

On March 31, we released Tor Browser Bundle 1.1.11. It includes:  
Update Firefox to 3.0.8  
Add Italian language bundles  
Update Torbutton to 1.2.1  
Update Vidalia to 0.1.12

**Bridge relay and bridge authority work.  
**  
From the changelog item from Vidalia 0.1.12:  
 o Remove the code that altered PublishServerDescriptor when becoming a  
 bridge, since Tor handles that itself now, and ensure that BridgeRelay  
 is reset when going from bridge to just-a-client mode.

**Scalability, load balancing, directory overhead, efficiency.  
**  
Roger and Steven wrote the Performance Roadmap as published at [https://www.torproject.org/press/2009-03-12-performance-roadmap-press-re...](https://www.torproject.org/press/2009-03-12-performance-roadmap-press-release.html.en "https://www.torproject.org/press/2009-03-12-performance-roadmap-press-release.html.en")

**Footprints from Tor Browser Bundle.  
**  
March 17, updated research on traces left behind by the Tor Browser Bundle. The current document can be found at [https://svn.torproject.org/svn/torbrowser/trunk/docs/traces.txt](https://svn.torproject.org/svn/torbrowser/trunk/docs/traces.txt "https://svn.torproject.org/svn/torbrowser/trunk/docs/traces.txt").

**Translations**  
21 Polish website translations  
20 French website translations  
53 Italian website translations  
25 German website translations  
5 Chinese website translations  
5 Updates from the translation portal for torbutton, in French, Italian, and Bokmål (Norwegian)

