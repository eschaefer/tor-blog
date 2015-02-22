---
layout: post
title: "Tor 0.2.6.3-alpha is released"
permalink: tor-0263-alpha-released
date: 2015-02-19 17:32:29
author: nickm
category: blog
comments: open
tags: ["0263", "source-release", "tor-alpha", "tor-dev"]
---

Tor 0.2.6.3-alpha is the third (and hopefully final) alpha release in the 0.2.6.x series. It introduces support for more kinds of sockets, makes it harder to accidentally run an exit, improves our multithreading backend, incorporates several fixes for the AutomapHostsOnResolve option, and fixes numerous other bugs besides.

If no major regressions or security holes are found in this version, the next version will be a release candidate.

You can download the source from the usual place on the website. Packages should be up in a few days.

**NOTE**: This is an alpha release. Please expect bugs.

Changes in version 0.2.6.3-alpha - 2015-02-19

-   Deprecated versions:
    -   Tor relays older than 0.2.4.18-rc are no longer allowed to advertise themselves on the network. Closes ticket 13555.
-   Major features (security, unix domain sockets):
    -   Allow SocksPort to be an AF\_UNIX Unix Domain Socket. Now high risk applications can reach Tor without having to create AF\_INET or AF\_INET6 sockets, meaning they can completely disable their ability to make non-Tor network connections. To create a socket of this type, use "SocksPort unix:/path/to/socket". Implements ticket 12585.
    -   Support mapping hidden service virtual ports to AF\_UNIX sockets. The syntax is "HiddenServicePort 80 unix:/path/to/socket". Implements ticket 11485.

  [**read more »**](https://blog.torproject.org/blog/tor-0263-alpha-released)
