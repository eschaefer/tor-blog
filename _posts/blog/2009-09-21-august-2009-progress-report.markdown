---
layout: post
title: "August 2009 Progress Report"
permalink: blog/august-2009-progress-report
date: 2009-09-21
author: phobos
category: blog
tags: ["anonymity advocacy", "bug fixes", "progress report", "releases"]
---

 **New releases**

On August 4, we released Tor Browser Bundle 1.2.7. It is updated primarily due to Firefox 3.0.13 with its ssl fixes.

The full changelist is:
1.2.7: Released 2009-08-04

- update Firefox to 3.0.13
- add Polish translation
- update libevent to 1.4.12

On August 19, we released Tor Browser Bundle 1.2.8. The big changes are the inclusion of statically linked openssl dlls to resolve a few geoip lookup and functionality issues with Vidalia, and the upgrade to the new Vidalia 0.2.2.

The full list of updates and fixes:

- update Torbutton to 1.2.2
- update Vidalia to 0.2.2
- compile OpenSSL 0.9.8k with Visual C to make dlls
- update Pidgin to 2.6.1

On August 3rd, we release Vidalia 0.2.1. This is a major change in the way OS X and Windows bundles are installed, as well as many usability enhancements. This also sets the stage for a plugin-API being developed over the next few months.

The changes are:

- Add a "Find Bridges Now" button that will attempt to automatically
download a set of bridge addresses and add them to the list of bridges
in the Network settings page.
- Add support for building with Google's Breakpad crash reporting
library (currently disabled by default).
- Show or hide the "Who has used my bridge recently?" link along with
the other bridge-related widgets when the user toggles the relay mode
in the Network settings page. (Ticket #480)
- Tolerate bridge addresses that do not specify a port number, since Tor
now defaults to using port 443 in such cases.
- Add support for viewing the map as a full screen widget when built
with KDE Marble support.
- Compute the salted hash of the control password ourself when starting
Tor, rather than launching Tor once to hash the password, parsing the
output, and then again to actually start Tor.
- Add a signal handler that allows Vidalia to clean up and exit normally
when it catches a SIGINT or SIGTERM signal. (Ticket #481)
- If the user chooses to ignore further warnings for a particular port,
remove it from the WarnPlaintextPorts and RejectPlaintextPorts
settings immediately. Also remember their preferences and reapply them
later, even if Tor is unable to writes to its torrc.(Ticket #493)
- Don't display additional plaintext port warning message boxes until
the first visible message box is dismissed. (Ticket #493)
- Renamed the 'make win32-installer' CMake target to 'make dist-win32'
for consistency with our 'make dist-osx' target.
- Fix a couple bugs in the WiX-based Windows installer related to building
a Marble-enabled Vidalia installer.
- Write the list of source files containing translatable strings to a
.pro file and supply just the .pro file as an argument to lupdate, rather
than supplying all of the source file names themselves.

On August 14th, we release Vidalia 0.2.2. It addresses an issue with openssl which causes the geoip lookups to fail on various versions of Windows. It also switches from the Nullsoft Installer to the Microsoft System Installer for better compatibility with Microsoft Windows.
There are now separate Apple OS X builds, one for PowerPC architectures and one for i386 architectures. No more Universal binary bloat to download.
The changes are:

- When the user clicks "Browse" in the Advanced settings page to locate
a new torrc, set the initial directory shown in the file dialog to the
current location of the user's torrc. (Ticket #505)
- Use 'ditto' to strip the architectures we don't want from the Qt
frameworks installed into the app bundle with the dist-osx,
dist-osx-bundle and dist-osx-split-bundle build targets.
- Fix a bug in the CMakeLists.txt files for ts2po and po2ts that caused
build errors on Panther for those two tools.
- Include rebuilt OpenSSL libraries in the Windows packages that are
built with the static (/MT) version of the Microsoft Visual C++
Runtime. Otherwise, we would require users to install the MSVC
Redistributable, which doesn't work for portable installations such as
the Tor Browser Bundle.
- Remove the NSIS file for the Vidalia installer since we now ship
MSI-based installers on Windows.

On August 27th, we released Vidalia 0.2.3. This fixes some more bugs with "Who has used by bridge" functionality and switches to Qt signals for event handling.
The changes are:

- Create the data directory before trying to copy over the default
Vidalia configuration file from inside the application bundle on Mac
OS X. Affects only OS X drag-and-drop installer users without a
previous Vidalia installation.
- Change all Tor event handling to use Qt's signals and slots mechanism
instead of custom QEvent subclasses.
- Fix another bug that resulted in the "Who has used my bridge?" link
initially being visible when the user clicks "Setup Relaying" from
the control panel if they are running a non-bridge relay.
(Ticket #509, reported by "vrapp")
- Always hide the "Who has used my bridge?" link when Tor isn't running,
since clicking it won't return useful information until Tor actually
is running.

On August 9th, we released Torbutton 1.2.2.
The changes and enhancements are:

- bugfix: Workaround Firefox Bug 440892 to prevent external apps from
 being launched (and thus bypassing proxy settings) without user
 confirmation. Independently reported by Greg Fleischer and optimist.
- bugfix: Create a separate "No Proxy For" option and remove the
 string "localhost" from proxy exemptions. Prevents a theoretical
 proxy bypass condition discovered by optimist. Fix based on patch from
 optimist.
- bugfix: bug 970: Purge undo tab list on Tor toggle.
- bugfix: bug 1040: Scrub URLs from log level 4 and higher log messages.
 Mac OS writes Firefox console messages to disk by default.
- bugfix: bug 1033: Fix FoxyProxy conflict that caused some FoxyProxy
 strings to fail to display.
- misc: bug 1006: Pop up a more specific failure message for pref
 changing errors during Tor toggle.
- misc: Fix a couple of strict javascript warns on FF3.5
- misc: Add chrome url protection call to conceal other addons during
 non-Tor usage. Patch by Sebastian Lisken.
- misc: Remove torbutton log system init message that may have scared some
 paranoids.

**Architecture and technical design docs**

Update our secure updater, Thandy, to have optional BitTorrent support to distribute load spikes following new releases better. Currently, it uses the mainline BitTorrent libraries that can be installed along with Thandy, but there is also some groundwork to support other BitTorrent libraries later on.

**Advocacy and outreach.**

Andrew, Jacob, Karsten, Mike, Nick, and Roger attended the Privacy Enhancing Technologies Symposium in Seattle, WA. Details can be found at [http://petsymposium.org/2009/](http://petsymposium.org/2009/ "http://petsymposium.org/2009/"). Jacob, Karsten, Mike, and Roger each presented their work on Tor.

Jacob, Karsten, Mike, Roger, and Sebastian attended Hacking at Random 2009 in Vierhouten, Netherlands. Details of the conference can be found at [https://wiki.har2009.org/page/Main\_Page](https://wiki.har2009.org/page/Main_Page "https://wiki.har2009.org/page/Main\_Page"). Jacob and Roger presented about Tor.

Jacob attended FooCamp 2009. More details can be found at [http://foocamp09.wiki.oreilly.com/wiki/index.php/Main\_Page](http://foocamp09.wiki.oreilly.com/wiki/index.php/Main_Page "http://foocamp09.wiki.oreilly.com/wiki/index.php/Main\_Page"). Jacob presented about Tor.

Andrew contacted Tor relay operators that started running a relay between June 12, 2009 and July 13, 2009; ostensibly for the Iranian protest movement. Of the 37 new relays, 13 had gone offline. After contacting the relay operators, 7 of the 13 are back online.

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**

On August 4, we released Tor Browser Bundle 1.2.7. It is updated primarily due to Firefox 3.0.13 with its ssl fixes.

The full changelist is:
1.2.7: Released 2009-08-04

- update Firefox to 3.0.13
- add Polish translation
- update libevent to 1.4.12

On August 19, we released Tor Browser Bundle 1.2.8. The big changes are the inclusion of statically linked openssl dlls to resolve a few geoip lookup and functionality issues with Vidalia, and the upgrade to the new Vidalia 0.2.2.

The full list of updates and fixes:

- update Torbutton to 1.2.2
- update Vidalia to 0.2.2
- compile OpenSSL 0.9.8k with Visual C to make dlls
- update Pidgin to 2.6.1

Jacob and Steve Tyree started work on a portable Tor Browser Bundle for Apple OS X. Jacob started work on a portable Tor Browser Bundle for generic Linux. Both bundles are currently in developer testing, gearing up for an alpha release in September 2009.

Updated TorVM with current packages for torbutton, tor, qemu. Added geoip and pycrypto to TorVM.

**Scalability, load balancing, directory overhead, efficiency.**

Continued metrics work with torperf and directory request statistics. Update bufferstats report, [http://git.torproject.org/checkout/metrics/master/report/buffer/bufferst...](http://git.torproject.org/checkout/metrics/master/report/buffer/bufferstats-2009-08-25.pdf "http://git.torproject.org/checkout/metrics/master/report/buffer/bufferstats-2009-08-25.pdf")
Updated circuit window report, [http://git.torproject.org/checkout/metrics/master/report/circwindow/circ...](http://git.torproject.org/checkout/metrics/master/report/circwindow/circwindow-2009-08-19.pdf "http://git.torproject.org/checkout/metrics/master/report/circwindow/circwindow-2009-08-19.pdf")

updated statistics on directory requests, [http://git.torproject.org/checkout/metrics/master/report/dirarch/](http://git.torproject.org/checkout/metrics/master/report/dirarch/ "http://git.torproject.org/checkout/metrics/master/report/dirarch/")

And updated measurements on overall tor network performance, [http://git.torproject.org/checkout/metrics/master/report/performance/tor...](http://git.torproject.org/checkout/metrics/master/report/performance/torperf-2009-08-24.pdf "http://git.torproject.org/checkout/metrics/master/report/performance/torperf-2009-08-24.pdf")

Continued work on our bandwidth node scanner to provide better extra-info for clients to make better routing decisions.

Added a seventh directory authority run by Jacob Appelbaum.

**More reliable (e.g. split) download mechanism.**

Christian Fromme started work on our email auto-responder, get-tor, to better handle split downloads via email.

Jon, our mirror volunteer, continued to contact mirrors and update their status accordingly. The net change is zero, but we added a new mirror and removed a stale mirror.

**Translation work**

Runa, our Google Summer of Code student, finished the project to allow for website content to be translated via the Tor Translation Portal, [https://translation.torproject.org/](https://translation.torproject.org/ "https://translation.torproject.org/"). The conversion tools are now live and Danish and Farsi are the first languages enabled in the Tor Translation Portal for testing.

In August, there were:

8 Russian updates for the website
29 Polish updates for the website
15 Chinese updates for the website
Danish updates for Torbutton
Nederlandish updates for Torbutton

