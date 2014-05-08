---
layout: post
title: "Announcing Tor Browser Bundle 3.0alpha1"
permalink: announcing-tor-browser-bundle-30alpha1
date: 06/17/2013
author: mikeperry
category: blog
tags: ["gitian", "security", "tbb", "tbb-3.0", "tor browser", "tor browser bundle", "tor-browser-bundle", "usability"]
---

 **Update 2013/6/28:** Describe workaround for the Windows d2d1.dll crash.

After almost 6 months of solid development, the Tor Project is proud to announce the first alpha in the [3.0 series](https://blog.torproject.org/category/tags/tbb-30) of the Tor Browser Bundle!

The 3.0alpha1 bundles are downloadable from the [Tor Package Archive](https://archive.torproject.org/tor-package-archive/torbrowser/3.0a1/).

# Release Highlights

Here are the major highlights of the 3.0 series:

1. **Usability, usability, usability!**

We've attempted to solve several major usability issues in this series, including:

  1. **No more Vidalia**

The Tor process management is handled by the new Tor Launcher Firefox extension. If you want the Vidalia map and other features, you can point an existing Vidalia binary at control port 9151 after Tor Browser has launched, and it should still work (and even allow you to reconfigure the TBB Tor as a bridge or a relay).

  2. **Local homepage with search box**

The browser now uses a local about:tor homepage instead of [https://check.torproject.org](https://check.torproject.org "https://check.torproject.org"). A local verification against the Tor control port is still performed, to ensure Tor is working, and a link to [https://check.torproject.org](https://check.torproject.org "https://check.torproject.org") is provided from the about:tor homepage for manual verification as well.

  3. **Guided Extraction for Windows**

For Windows users, an NSIS-based extractor now guides you through the TBB extraction and ensures the extracted bundle ends up on your Desktop, or in a known location chosen by you (but make sure you have permissions on that location). Hopefully this will mean no more losing track of the extracted bundle files!

2. **Email-sized bundles**

The bundles are all under the 25M gmail attachment size limit, so direct email and gettor attachments are once again possible.

3. **Improved build security and integrity verification**  
We now use [Gitian](https://gitian.org/) to build the bundles. The idea behind Gitian is to allow independent people to take our source code and produce exactly identical binaries on their own. We're not quite at the point where you always get a matching build, but the remaining differences are minor, and within a couple more releases we should have it fully reproducible. For now, we are [posting all of the builds](https://people.torproject.org/~mikeperry/tbb-3.0alpha1-builds/) for comparison, and you can of course [build and compare your own](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/README.build).

# Known issues

Of course, being an alpha release (in fact, the first alpha release of this series), we expect these bundles to have some issues. Here's the major user-facing issues that we know about so far:

1. **Crash Issue: Windows Permissions**

On Windows, if you install the bundle to anywhere other than the Desktop, permissions issues can cause the bundles to crash at startup.

2. **Crash Issue: Windows Software Conflict(s)**

There appears to be an issue with direct2d rendering acceleration that affects some video cards, and has a crash report with a module d2d1.dll. The simplest workaround is to right click on 'Start Tor Browser' and select "Properties->Compatibility->Run in Windows XP Compatibility mode".

3. **Extraction: Delete or rename your old TBB directory first!**

These bundles are significantly different than the previous alphas or stable releases. You must not extract this bundle on top of a previous TBB directory, or multiple things will break. If you want to preserve your bookmarks and history, you can do so by copying only the **places.sqlite** file from your old bundle directory into the new one. The good news is that the elimination of Vidalia should make it much simpler for us to finally deploy an autoupdater, but please bear with us until we can finally complete that important usability work.

4. **Misc: Missing Translations**

Some of the translations strings for the Tor Launcher startup got munged by Transifex. In particular, the Farsi and the German builds both have missing button labels and strings.

If you experience any other issues, please let us know and/or [file a bug!](https://trac.torproject.org/projects/tor/newticket)

