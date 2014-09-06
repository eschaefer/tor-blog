---
layout: post
title: "Testing Tor Browser Bundle 1.2.0-dev"
permalink: blog/testing-tor-browser-bundle-120-dev
date: 2009-05-23
author: phobos
category: blog
tags: ["geoip", "libevent", "tor browser bundle"]
---

This is an open call for testing of the soon to be released Tor Browser Bundle 1.2.0.

The major changes in this version are that you can now run multiple instances of Firefox. This means each Firefox browser is independent of the others. They won't leak urls, scripts, etc between instances.

It also includes Tor's geoip database. This will enable people to set ExitNodes by country code. You still have to manually edit the torrc file. We'd love it if someone wrote a way to do this into Vidalia (such as right click on a country in the network map and choose "exit here").

- Switch to launching Firefox directly from Vidalia to allow multiple instances of Firefox
- Update Firefox to 3.0.10
- Update to Qt 4.5.1
- Update Firefox prefs.js to stop scanning for plugins
- Update libevent to 1.4.11
- Include the Tor geoip database

I'll be watching this post and comments for feedback. I only created the English version for testing. Thanks for testing!

Here is the [Tor IM Browser Bundle 1.2.0-dev](https://www.torproject.org/torbrowser/dist/tor-im-browser-1.2.0-dev_en-US.exe), [sig](https://www.torproject.org/torbrowser/dist/tor-im-browser-1.2.0-dev_en-US.exe.asc), and [sha1](https://www.torproject.org/torbrowser/dist/tor-im-browser-1.2.0-dev_en-US.exe.sha1) files.

