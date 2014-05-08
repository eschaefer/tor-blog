---
layout: post
title: "OS X Vidalia Bundle Thoughts"
permalink: os-x-vidalia-bundle-thoughts
date: 10/30/2008
author: phobos
category: blog
tags: ["apple os x", "installation", "vidalia bundle"]
---

A few weeks ago, I watched some non-technical OS X users attempt to install the Vidalia-Tor Bundle. Many of them tried to drag the installation package to Applications. A few were surprised it required an installation at all.

In [Vidalia trunk](http://trac.vidalia-project.net/browser/vidalia/trunk/pkg/osx) I committed a different way to install Vidalia, Tor, and Polipo. In this new dmg, you just open it up and drag the Vidalia icon into Applications. You now have Tor, Vidalia, and Polipo pre-configured and running completely out of Applications. While this works well for users that never installed Tor/Vidalia before, it doesn't work so well for existing installations.

Is it smart to think users will un-install their existing Vidalia/Tor bundle before using the drag and drop installation method? My inclination is that it isn't smart. This installation method also removes the ability to automatically install Torbutton for Firefox.

In comparison, the current method is to ship a dmg which contains a metapackage. This metapackage contains a few scripts to run pre and post-installation, which do smart things to save current configurations, upgrade existing software binaries, and try to install Torbutton for Firefox. In general, this method has worked well for most users. I've heard from enough people to know they tried to drag and drop the metapackage into Applications at first, and when that didn't work, double-clicked the metapackage to start the installer.

I'm now leaning towards creating a [Tor Browser Bundle](https://www.torproject.org/torbrowser/) for OS X; which can run out of the dmg or be installed via drag and drop. Much like the current Tor Browser Bundle (also, we should stop naming everything Tor), it would be self-contained and leave zero trace on the machine after closing.

Thoughts on ways to make the OS X install easier, ostensibly via drag and drop install? Or is the effort to create a TBB for OS X a better use of resources?

