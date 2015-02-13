---
layout: post
title: "Testing Tor Browser Bundle 1.2.0-dev"
permalink: testing-tor-browser-bundle-120-dev
date: 2009-05-22 21:50:06
author: phobos
category: blog
status: closed
tags: ["geoip", "libevent", "tor browser bundle"]
---

This is an open call for testing of the soon to be released Tor Browser Bundle 1.2.0.

The major changes in this version are that you can now run multiple instances of Firefox. This means each Firefox browser is independent of the others. They won't leak urls, scripts, etc between instances.

It also includes Tor's geoip database. This will enable people to set ExitNodes by country code. You still have to manually edit the torrc file. We'd love it if someone wrote a way to do this into Vidalia (such as right click on a country in the network map and choose "exit here"). [**read more »**](https://blog.torproject.org/blog/testing-tor-browser-bundle-120-dev)

-   Switch to launching Firefox directly from Vidalia to allow multiple instances of Firefox
-   Update Firefox to 3.0.10
-   Update to Qt 4.5.1
-   Update Firefox prefs.js to stop scanning for plugins
-   Update libevent to 1.4.11
-   Include the Tor geoip database

