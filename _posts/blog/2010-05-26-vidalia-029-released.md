---
layout: post
title: "Vidalia 0.2.9 Released"
permalink: vidalia-029-released
date: 2010-05-26 22:05:19
author: phobos
category: blog
status: closed
tags: ["bug fixes", "stable release", "vidalia release"]
---

On May 20, we released Vidalia 0.2.9. Fixes include Qt 4.6.2 compatibility, new cert, and some new translations.

You can download it at [https://www.torproject.org/vidalia/](https://www.torproject.org/vidalia/ "https://www.torproject.org/vidalia/"). Packages are slowly being updated to include this version of Vidalia.

The full changelog is: [**read more »**](https://blog.torproject.org/blog/vidalia-029-released)

Remove the GoDaddy CA certificate bundle since we changed the certificate used to authenticate connections to geoips.vidalia-project.net for downloading GeoIP information from a commercial GoDaddy certificate to a free CACert certificate.

Define -D\_WIN32\_WINNT=0x0501 on Windows builds so that MiniUPnPc will build with the latest versions of MinGW.

Modify miniupnpc.c from MiniUPnPc's source so that it will build on Mac OS X 10.4.

Work around Qt's new behavior for the QT\_WA macro so that Vidalia will  
 work correctly again on Windows with Qt \>= 4.6.
