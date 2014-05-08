---
layout: post
title: "Experimental OS X Drag and Drop Vidalia Bundle Installer"
permalink: experimental-os-x-drag-and-drop-vidalia-bundle-installer
date: 01/13/2009
author: phobos
category: blog
tags: ["alpha release", "apple os x", "experimental", "polipo", "vidalia bundle"]
---

I asked for community feedback in [this post](https://blog.torproject.org/blog/os-x-vidalia-bundle-thoughts) about drag and drop installation of the Vidalia bundle for Apple's OS X. In working with the Vidalia team, we now have a drag and drop installer. This is **experimental** . It's designed for a clean install. It won't migrate your settings, nor will it configure anything for you. Upon installing, your milk may sour and your salt may run off with your pepper. Now that the disclaimers are over, here's what it contains and does do for you.

It includes Universal binaries for:

- Vidalia version 0.2.0-svn r3425
- Polipo 1.0.4 configured to use Tor as a socksproxy
- Tor 0.2.1.10-alpha compiled with prefix and bindir set to /Applications/Vidalia.app

You can [download them](http://interloper.org/tmp/vidalia/vidalia-bundle-0.2.1.11-alpha-0.2.0-svn-r3467-universal.dmg) along with [the pgp signature](http://interloper.org/tmp/vidalia/vidalia-bundle-0.2.1.11-alpha-0.2.0-svn-r3467-universal.dmg.asc) and [the SHA-1 hash](http://interloper.org/tmp/vidalia/vidalia-bundle-0.2.1.11-alpha-0.2.0-svn-r3467-universal.dmg.sha1). **\*\*Update 2009-01-22 changed packages to r3467 of Vidalia and updated Tor to 0.2.1.11-alpha.**

It's a self-contained disk image that has 3 items. The Vidalia.app package, a README.txt, and a folder full of licenses. There is a pretty background for the disk image courtesy of dr|z3d, and a link to the /Applications folder. And while everything is in a simple dmg file, this is not a Tor Browser Bundle for OS X. Running the applications out of the dmg may work, but OS X writes to plist files, caches, and other things all over the installed system. Please wait until we can properly create a TBB for OS X; for this is not it. However, if you are interested in helping out with a TBB for OS X, we're happy to have you help.

Installation is literally this: "Drag the Vidalia icon to the Applications folder". Boom. Done. Vidalia, Tor, and Polipo are installed. Go to your Applications folder and double-click the Vidalia icon. Everything should work out of the box. All bets are off if you have a pre-configured Tor, Vidalia, Polipo, or Privoxy.

Here is a running [CHANGELOG](http://trac.vidalia-project.net/browser/vidalia/trunk/CHANGELOG) of what's new in Vidalia 0.2.0-svn. One of the changes is that your Vidalia data directory is no longer ~/.vidalia/ but ~/Library/Vidalia. If you don't have a vidalia.conf in ~/Library/Vidalia, there is a sample vidalia.conf in /Applications/Vidalia.app/Contents/Resources that is copied to ~/Library/Vidalia to make this bundle work.

The changes to Polipo are [documented](https://svn.torproject.org/svn/tor/trunk/contrib/polipo/). See the [README](https://svn.torproject.org/svn/tor/trunk/contrib/polipo/README) file for some details.

The only change to Tor are the parameters passed to configure:  
"CFLAGS="-O -g -mmacosx-version-min=10.4 -isysroot /Developer/SDKs/MacOSX10.4u.sdk -arch i386 -arch ppc" LDFLAGS="-Wl,-syslibroot,/Developer/SDKs/MacOSX10.4u.sdk"  
CONFDIR=/Applications/Vidalia.app  
./configure --prefix=/Applications/Vidalia.app --bindir=/Applications/Vidalia.app  
--sysconfdir=/Library --disable-dependency-tracking". And edit the Makefile to remove the tests for /Library/Tor.

The goal is to make it easier for users to install the Vidalia Bundle and get Tor working. Using Vidalia to configure Tor is recommended. I don't know if this is the final direction, but enough people have trouble installing and configuring our packages in OS X, this is worth a test.

I look forward to your feedback. Thanks!

