---
layout: post
title: "Vidalia bundle, OSX and Qt bugs"
permalink: vidalia-bundle-osx-and-qt-bugs
date: 2008-01-20 13:50:53
author: phobos
category: blog
status: closed
tags: ["bugs", "crashes", "osx", "qt", "vidalia", "vidalia bundle"]
---

It appears Qt-4.3.3 has [a bug](http://trolltech.com/developer/task-tracker/index_html?method=entry&id=155700) that is causing Vidalia to crash when the list of Tor nodes refreshes and is sorted. The current 0.1.2.19-stable and 0.2.0.17-alpha bundles for OSX are built against Qt-4.3.3.

I've downgraded the build hosts to Qt-4.3.2. The rebuilt OSX vidalia-bundle packages for both 0.1.2.19-stable and 0.2.0.17-alpha are available as:

-   [Bundle with 0.1.2.19-stable and Vidalia 16a](http://www.torproject.org/dist/vidalia-bundles/vidalia-bundle-0.1.2.19-0.0.16a-tiger.dmg)
-   [Bundle with 0.2.0.17-alpha and Vidalia 16a](http://www.torproject.org/dist/vidalia-bundles/vidalia-bundle-0.2.0.17-alpha-0.0.16a-tiger.dmg)

These bundles contain Vidalia compiled with Qt-4.3.2. This makes Vidalia happy again.
