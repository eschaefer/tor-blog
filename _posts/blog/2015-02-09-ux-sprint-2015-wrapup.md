---
layout: post
title: "UX Sprint 2015 wrapup"
permalink: blog/ux-sprint-2015-wrapup
date: 2015-02-09 14:21:28
author: dcf
category: blog
comments: open
tags: ["usability"]
---

[Usability](https://en.wikipedia.org/wiki/Usability) is critical to [security](http://www.cc.gatech.edu/~keith/pubs/ieee-intro-usable-security.pdf). Additionally, there has been research on "[stopping points](https://www.petsymposium.org/2012/papers/hotpets12-1-usability.pdf)," common points where people would get frustrated with Tor enough that they would stop the installation process or stop using Tor. Usability issues also can degrade user experience, cause confusion, or even cause people to accidentally deanonymize themselves.

To address usability issues broadly, we brought together Tor developers, designers, users, and researchers to discuss usability problems and how to fix them. Last weekend, there was a [user experience (UX) sprint](https://trac.torproject.org/projects/tor/wiki/org/meetings/2015UXsprint) dedicated to improving the usability of Tor Browser.

A major part of the sprint was user testing the current [Tor Browser (4.0.3)](https://blog.torproject.org/blog/tor-browser-403-released). We asked users—some with prior Tor experience, some without—to perform some common tasks:

-   Search for, download, and install Tor Browser
-   Do a web search
-   Watch a video
-   Use "New Identity"
-   Interact with and describe the current browser toolbar buttons

The users performed this task in a "cognitive walkthrough" fashion, talking aloud while completing each of the tasks, explaining their understanding of the task and motivation for completing it in that specific way. With permission, we recorded the contents of the computer screen so developers could watch in another room. We hope to present the screen videos and other outcomes of the sprint at the upcoming [winter dev meeting](https://trac.torproject.org/projects/tor/wiki/org/meetings/2015WinterDevMeeting).

Because of the limited size of the study (there were five participants), it's not possible to state with confidence what fraction of users will encounter major usability obstacles. However, it was effective at discovering and demonstrating issues that are likely to cause problems for many users. We will use our observations to guide future experiments. A few aspects stood out as deserving of further attention:

-   While searching for Tor Browser, users encountered various sources for the browser other than our target ["Easy Download" page](https://www.torproject.org/download/download-easy.html), and also found some odd sources for documentation. Users who found a download page other than the "easy" version expressed varying degrees of confusion, depending on their landing page. Ticket [\#14685](https://trac.torproject.org/projects/tor/ticket/14686) is about finding a way to consolidate or drive users to our preferred download page.

-   [Gatekeeper](https://en.wikipedia.org/wiki/Gatekeeper_(OS_X)) on OS X makes it hard to install programs that aren't signed by an [Apple certificate](https://developer.apple.com/library/mac/documentation/Security/Conceptual/CodeSigningGuide/Introduction/Introduction.html) or don't come from the App Store. All users were at least temporarily delayed by this dialog:

    ![TorBrowser can't be opened because it is from an unidentified developer.](https://people.torproject.org/~dcf/graphs/blogfiles/gatekeeper-yosemite.png)

    Even though everyone was able to get past the dialog, it was a big obstacle to installation. (If it happens to you, the trick is to Ctrl-click on the Tor Browser icon and select "Open".) To solve this problem is not easy, but we can perhaps make it better by providing better documentation. Ticket [\#6540](https://trac.torproject.org/projects/tor/ticket/6540) tracks this issue.

-   If you try to run Tor Browser from a read-only filesystem, you get a misleading error message:

    ![A copy of Firefox is already open. Only one copy of Firefox can be open at a time.](https://people.torproject.org/~dcf/graphs/blogfiles/firefox-is-already-open.png)

    This is a known issue, tracked in ticket [\#4782](https://trac.torproject.org/projects/tor/ticket/4782), that affected some users. It happens on OS X if you run the Tor Browser app directly from the disk image (.dmg) instead of first copying it to the Applications folder.

Tickets created as a result of the sprint have the [\#uxsprint2015](https://trac.torproject.org/projects/tor/query?keywords=~uxsprint2015) tag. In addition, the new [\#tbb-usability-stoppoint](https://trac.torproject.org/projects/tor/query?keywords=~tbb-usability-stoppoint&status=!closed) tag marks stopping points, to help track usability issues like the above, which result in users being unable or unwilling to continue using the browser.

We hope that usability experiments and improvements will be ongoing. In the future, we'd like to test other aspects of Tor Browser, such as downloading files, updating, and managing Tor and non-Tor browsers, as well as expanding the tests to larger and diverse user groups. If you are interested in helping improve the usability of Tor Browser, [get in touch](https://www.torproject.org/about/contact) by email or IRC. We need help from a lot of different kinds of people: designers, translators, programmers, and usability experts to name a few.

We thank the Tor Project for supporting the sprint, the participants, those who helped us recruit on short notice, and those who helped us plan and set goals and everyone who attended as a developer or observer: Arlo, Arthur, Ashkan, David, Griffin, Isis, Krishna, Linda, Mike, and Nima. We also thank the Tor help desk, whose [\#tbb-helpdesk-frequent](https://trac.torproject.org/projects/tor/query?keywords=~tbb-helpdesk-frequent&status=!closed) tag helped us prioritize tickets. Special thanks go to Nima for suggesting the idea of a UX meeting in the first place.

Linda Lee and David Fifield
