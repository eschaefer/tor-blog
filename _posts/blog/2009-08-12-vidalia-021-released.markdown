---
layout: post
title: "Vidalia 0.2.1 released"
permalink: vidalia-021-released
date: 2009-08-12
author: phobos
category: blog
tags: ["usability enhancements", "vidalia release"]
---

Vidalia 0.2.1 is now available. This is a test release of the 0.2.x branch, which we hope to soon make the mainline version; replacing the 0.1.x branch.

Vidalia can be downloaded at [https://www.torproject.org/vidalia/](https://www.torproject.org/vidalia/ "https://www.torproject.org/vidalia/").

Changelog:

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

