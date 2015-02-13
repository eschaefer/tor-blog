---
layout: post
title: "OS X Vidalia Bundle Thoughts"
permalink: os-x-vidalia-bundle-thoughts
date: 2008-10-29 21:43:41
author: phobos
category: blog
status: closed
tags: ["apple os x", "installation", "vidalia bundle"]
---

A few weeks ago, I watched some non-technical OS X users attempt to install the Vidalia-Tor Bundle. Many of them tried to drag the installation package to Applications. A few were surprised it required an installation at all.

In [Vidalia trunk](http://trac.vidalia-project.net/browser/vidalia/trunk/pkg/osx) I committed a different way to install Vidalia, Tor, and Polipo. In this new dmg, you just open it up and drag the Vidalia icon into Applications. You now have Tor, Vidalia, and Polipo pre-configured and running completely out of Applications. While this works well for users that never installed Tor/Vidalia before, it doesn't work so well for existing installations.

Is it smart to think users will un-install their existing Vidalia/Tor bundle before using the drag and drop installation method? My inclination is that it isn't smart. This installation method also removes the ability to automatically install Torbutton for Firefox. [**read more »**](https://blog.torproject.org/blog/os-x-vidalia-bundle-thoughts)
