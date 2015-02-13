---
layout: post
title: "Vidalia 0.2.1 released"
permalink: vidalia-021-released
date: 2009-08-11 22:48:59
author: phobos
category: blog
status: closed
tags: ["usability enhancements", "vidalia release"]
---

Vidalia 0.2.1 is now available. This is a test release of the 0.2.x branch, which we hope to soon make the mainline version; replacing the 0.1.x branch.

Vidalia can be downloaded at [https://www.torproject.org/vidalia/](https://www.torproject.org/vidalia/ "https://www.torproject.org/vidalia/").

Changelog: [**read more »**](https://blog.torproject.org/blog/vidalia-021-released)

Add a "Find Bridges Now" button that will attempt to automatically  
 download a set of bridge addresses and add them to the list of bridges  
 in the Network settings page.

Add support for building with Google's Breakpad crash reporting  
 library (currently disabled by default).

Show or hide the "Who has used my bridge recently?" link along with  
 the other bridge-related widgets when the user toggles the relay mode  
 in the Network settings page. (Ticket \#480)

Tolerate bridge addresses that do not specify a port number, since Tor  
 now defaults to using port 443 in such cases.

Add support for viewing the map as a full screen widget when built  
 with KDE Marble support.
