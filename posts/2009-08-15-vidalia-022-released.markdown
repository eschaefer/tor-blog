---
layout: post
title: "Vidalia 0.2.2 Released"
permalink: vidalia-022-released
date: 08/15/2009
author: phobos
category: blog
tags: ["bug fixes", "openssl fixes", "usability enhancements", "vidalia releases"]
---

Vidalia 0.2.2 is released. It addresses an issue with openssl which causes the geoip lookups to fail on various versions of Windows. It also switches from the Nullsoft Installer to the Microsoft System Installer for better compatibility with Microsoft Windows.

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

