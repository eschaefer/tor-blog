---
layout: post
title: "March 2010 Progress Report"
permalink: blog/march-2010-progress-report
date: 2010-04-18
author: phobos
category: blog
tags: ["advocacy", "progress report", "proposals", "releases", "scalability", "translations"]
---

 **New Releases**
On March 7th, we released the latest in the -alpha series, Tor 0.2.2.10-alpha. Tor 0.2.2.10-alpha fixes a regression introduced in 0.2.2.9-alpha that could prevent relays from guessing their IP address correctly. It also starts the groundwork for another client-side performance boost, since currently we're not making efficient use of relays that have both the Guard flag and the Exit flag.

o Major bugfixes:
 - Fix a regression from our patch for bug 1244 that caused relays
 to guess their IP address incorrectly if they didn't set Address
 in their torrc and/or their address fails to resolve. Bugfix on
 0.2.2.9-alpha; fixes bug 1269.

o Major features (performance):
 - Directory authorities now compute consensus weightings that instruct
 clients how to weight relays flagged as Guard, Exit, Guard+Exit,
 and no flag. Clients that use these weightings will distribute
 network load more evenly across these different relay types. The
 weightings are in the consensus so we can change them globally in
 the future. Extra thanks to "outofwords" for finding some nasty
 security bugs in the first implementation of this feature.

o Minor features (performance):
 - Always perform router selections using weighted relay bandwidth,
 even if we don't need a high capacity circuit at the time. Non-fast
 circuits now only differ from fast ones in that they can use relays
 not marked with the Fast flag. This "feature" could turn out to
 be a horrible bug; we should investigate more before it goes into
 a stable release.

o Minor features:
 - Allow disabling building of the manpages. Skipping the manpage
 speeds up the build considerably.

o Minor bugfixes (on 0.2.2.x):
 - Fix a memleak in the EXTENDCIRCUIT logic. Spotted by coverity.
 Bugfix on 0.2.2.9-alpha.
 - Disallow values larger than INT32\_MAX for PerConnBWRate|Burst
 config option. Bugfix on 0.2.2.7-alpha.
 - Ship the asciidoc-helper file in the tarball, so that people can
 build from source if they want to, and touching the .1.txt files
 doesn't break the build. Bugfix on 0.2.2.9-alpha.

o Minor bugfixes (on 0.2.1.x or earlier):
 - Fix a dereference-then-NULL-check sequence when publishing
 descriptors. Bugfix on 0.2.1.5-alpha. Discovered by ekir; fixes
 bug 1255.
 - Fix another dereference-then-NULL-check sequence. Bugfix on
 0.2.1.14-rc. Discovered by ekir; fixes bug 1256.
 - Make sure we treat potentially not NUL-terminated strings correctly.
 Bugfix on 0.1.1.13-alpha. Discovered by rieo; fixes bug 1257.

o Code simplifications and refactoring:
 - Fix some urls in the exit notice file and make it XHTML1.1 strict
 compliant. Based on a patch from Christian Kujau.
 - Don't use sed in asciidoc-helper anymore.
 - Make the build process fail if asciidoc cannot be found and
 building with asciidoc isn't disabled.

On March 15, we released the latest in the -stable series, Tor 0.2.1.25-stable.

o Major bugfixes:
 - Fix a regression from our patch for bug 1244 that caused relays
 to guess their IP address incorrectly if they didn't set Address
 in their torrc and/or their address fails to resolve. Bugfix on
 0.2.1.23; fixes bug 1269.
 - When freeing a session key, zero it out completely. We only zeroed
 the first ptrsize bytes. Bugfix on 0.0.2pre8. Discovered and
 patched by ekir. Fixes bug 1254.

o Minor bugfixes:
 - Fix a dereference-then-NULL-check sequence when publishing
 descriptors. Bugfix on 0.2.1.5-alpha. Discovered by ekir; fixes
 bug 1255.
 - Fix another dereference-then-NULL-check sequence. Bugfix on
 0.2.1.14-rc. Discovered by ekir; fixes bug 1256.
 - Make sure we treat potentially not NUL-terminated strings correctly.
 Bugfix on 0.1.1.13-alpha. Discovered by rieo; fixes bug 1257.

On March 26 we released the first beta of a Tor Browser Bundle for GNU/Linux operating systems. It is now available for x86 and x86\_64 architectures in 12 languages.

The bundle comes with the following software:
 \* Tor 0.2.2.10-alpha
 \* Vidalia 0.2.7 -- cross-platform controller GUI for the Tor software
 \* Polipo 1.0.4.1 -- caching web proxy
 \* Firefox 3.5.8 -- web browser
 \* Torbutton 1.2.4 -- Firefox extension to enable or disable the browser's use of Tor
 \* NoScript 1.9.9.57 -- Firefox extension to only allow scripts from trusted sites
 \* BetterPrivacy 1.4.7 -- Firefox extension to protect against supercookies

Orbot 0.0.4 is the first public release. Orbot includes:

\* Tor 0.2.2.9-alpha
\* A native Android control graphical interface
\* Privoxy compiled for Android

March 11 we released Orbot 0.0.5 for Android phones. It fixes a number of bugs in the graphical control interface and updated Tor to 0.2.2.10-alpha.

**Design, develop, and implement enhancements that make Tor a better tool for users in censored countries.**

We worked with activists in Iran and China to determine what relays were blocked, if any, by national firewall apparatus. Iran is not blocking Tor relays at all. China is blocking most public relays, and appears to have crawled the bridge address website in order to block those bridges. There were 4121 requests in a 6 hour period from seemingly unique gmail accounts for bridge addresses via email. However, we cannot attribute this to anything other than users requesting bridges. It is possible this was an attempt to enumerate all bridges available via email. Our twitter and qq distribution methods remain under utilized.

Implemented graphs of packages served by our get-tor email autoresponder. You can see them at [http://metrics.torproject.org/gettor-graphs.html](http://metrics.torproject.org/gettor-graphs.html "http://metrics.torproject.org/gettor-graphs.html")

**Outreach and Advocacy**

- On March 1, Roger met with Sina from Access. He answered many questions about Tor, learned more about the situation in Iran now, and helped brainstorm about further collaborations.
- On March 2, Karen was a panelist at the University of Maryland Digital Media Conference.
- On March 12, Jacob spoke at Digital Security and Tactics for (and by) anti-authoritarians. https://www.noisebridge.net/wiki/Digital\_Security\_and\_Tactics\_For\_(and\_By)\_Anti\_Authoritarians
- On March 20, Andrew, Erinn, and Runa attended LibrePlanet 2010. Erinn was a panelist at a session about "Women in Technology and Free Software". Andrew spoke about Tor, Free Software, and running a non-profit business with free software. [http://libreplanet.org/2010](http://libreplanet.org/2010 "http://libreplanet.org/2010")
- A Tor fan created a very quick advocacy video about using Tor for circumvention at [http://media.torproject.org/video/TorQatarCensor15secs2b.ogv](http://media.torproject.org/video/TorQatarCensor15secs2b.ogv "http://media.torproject.org/video/TorQatarCensor15secs2b.ogv").
- Andrew was interviewed by ABC Australia's Future Tense program about the "DarkWeb". You can listen to the radio interview at [http://media.torproject.org/video/2010-03-11-ABC-Australia-FutureTense-I...](http://media.torproject.org/video/2010-03-11-ABC-Australia-FutureTense-Interview.mp3 "http://media.torproject.org/video/2010-03-11-ABC-Australia-FutureTense-Interview.mp3") or read the transcript at [http://www.abc.net.au/rn/futuretense/stories/2010/2837736.htm](http://www.abc.net.au/rn/futuretense/stories/2010/2837736.htm "http://www.abc.net.au/rn/futuretense/stories/2010/2837736.htm").
- Steven Murdoch was interviewed by PC Pro UK magazine about "The Dark Side of the Web", [http://www.pcpro.co.uk/features/356254/the-dark-side-of-the-web](http://www.pcpro.co.uk/features/356254/the-dark-side-of-the-web "http://www.pcpro.co.uk/features/356254/the-dark-side-of-the-web").
- On March 25, we announced The Tor Store to allow users to support Tor from around the world with t-shirts, mugs, and other merchandise. [https://www.torproject.org/press/2010-03-25-tor-store-press-release.html...](https://www.torproject.org/press/2010-03-25-tor-store-press-release.html.en "https://www.torproject.org/press/2010-03-25-tor-store-press-release.html.en").
- Tor and EFF were accepted into the Google Summer of Code for the fourth year in a row. [https://blog.torproject.org/blog/tor-google-summer-code-2010](https://blog.torproject.org/blog/tor-google-summer-code-2010 "https://blog.torproject.org/blog/tor-google-summer-code-2010").
- Jacob gave a Tor talk to Twitter engineers about circumvention, anonymity, and the positive uses of both technologies.
- Erinn, Jacob, and Mike talked to Google engineers about Tor on Android and better integration with the Chrome browser.
- Christian rewrote the Tor Weather web application, [https://weather.torproject.org/](https://weather.torproject.org/ "https://weather.torproject.org/"), to increase stability, fix a number of bugs, and add some requested features. Tor Weather is a tool for relay operators to get a reminder when their relay appears to be offline.

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**
A beta-test of Tor Browser Bundle for GNU/Linux was released for general testing. It is released in both native 32-bit and 64-bit versions. See release notes above.

**Bridge relay and bridge authority work.**
Steven started work on a proposal to turn all clients into bridges by default. This proposal describes how Tor clients could determine when they have sufficient bandwidth capacity and are sufficiently reliable to become either bridges or Tor relays. When they meet this criteria, they will automatically promote themselves, based on user preferences. The proposal also defines the new controller messages and options which will control this process.

Note that for the moment, only transitions between client and bridge are being considered. Transitions to public relay will be considered at a future date, but will use the same infrastructure for measuring capacity and reliability.

The full proposal, and subsequent discussion, can be read at [http://archives.seul.org/or/dev/Mar-2010/msg00028.html](http://archives.seul.org/or/dev/Mar-2010/msg00028.html "http://archives.seul.org/or/dev/Mar-2010/msg00028.html").

**Scalability, load balancing, directory overhead, efficiency.**
Karsten continued to improve the Tor Metrics Portal, [http://metrics.torproject.org/](http://metrics.torproject.org/ "http://metrics.torproject.org/"). More reports were automated. The entire setup and process of how we analyze the data was documented. We could use volunteer help with portal and data visualization technologies and implementation experience.

We added proposal 170, "Configuration options regarding circuit building". Tor's treatment of the various configuration \*Nodes options was surprising to many users, and quite a few conspiracy theories have crept up. We should update our specification and code to better describe and to communicate what is going during circuit building, and how we're honoring configuration. So far, we've been tracking a bugreport about this behaviour ( [https://bugs.torproject.org/flyspray/index.php?do=details&id=1090](https://bugs.torproject.org/flyspray/index.php?do=details&id=1090 "https://bugs.torproject.org/flyspray/index.php?do=details&id=1090")) and Nick replied in a thread on or-talk ( [http://archives.seul.org/or/talk/Feb-2010/msg00117.html](http://archives.seul.org/or/talk/Feb-2010/msg00117.html "http://archives.seul.org/or/talk/Feb-2010/msg00117.html")). This proposal tries to document our intention for those configuration options.

**Translation work, ultimately a browser-based approach.**

- Language updates to the website in French, Chinese, German, Spanish, Polish, Russian, Estonian, Norwegian, Greek
- Language updates to the get-tor email autoresponder in Vietnamese, Dutch,
- Language updates to torbutton in Arabic, German, Danish, Slovakian, Swedish, Vietnamese, Russian
- Runa fixed a large amount of broken html and translated files. This enabled us to push nearly all projects and languages into the codebases.

