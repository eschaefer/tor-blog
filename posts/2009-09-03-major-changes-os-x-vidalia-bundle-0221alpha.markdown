---
layout: post
title: "Major changes to OS X Vidalia Bundle with 0.2.2.1-alpha"
permalink: major-changes-os-x-vidalia-bundle-0221alpha
date: 09/03/2009
author: phobos
category: blog
tags: ["drag and drop OS X install", "updated packages", "vidalia bundle"]
---

As highlighted in the [0.2.2.1-alpha release notes](http://blog.torproject.org/blog/tor-0221alpha-released), the Vidalia Bundle for OS X includes some major changes. Many of these are for ease of use and user experience improvements. The release of OS X 10.6 (Snow Leopard) gave me a fine excuse to release the improvements.

It's best to [un-install Tor/Vidalia](https://www.torproject.org/docs/tor-doc-osx.html.en#uninstall) and then install this new bundle; rather than upgrade. If you want to upgrade, you'll need to update the paths for Tor and Polipo in the Vidalia Settings window.

There has been a lot of testing since this [test release](http://blog.torproject.org/blog/experimental-os-x-drag-and-drop-vidalia-bundle-installer) of the drag and drop installer for OS X in January. The main goal was to make installation far easier, less error prone, and keep all of the bundle in a single directory for easier configuration and un-installation.

The changes are:

> - Upgrade Vidalia from 0.1.15 to 0.2.3 in the Windows and OS X installer bundles. See [https://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.2.3/CHAN...](https://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.2.3/CHANGELOG "https://trac.vidalia-project.net/browser/vidalia/tags/vidalia-0.2.3/CHANGELOG") for details of what's new in Vidalia 0.2.3.  
> - OS X Vidalia Bundle: move to Polipo 1.0.4 with Tor specific configuration file, rather than the old Privoxy.  
> - OS X Vidalia Bundle: Vidalia, Tor, and Polipo are compiled as x86-only for better compatibility with OS X 10.6, aka Snow Leopard.  
> - OS X Vidalia Bundle: The multi-package installer is now replaced by a simple drag and drop to the /Applications folder. This change occurred with the upgrade to Vidalia 0.2.3.
