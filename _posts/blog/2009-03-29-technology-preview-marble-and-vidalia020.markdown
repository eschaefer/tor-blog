---
layout: post
title: "Technology Preview:  Marble and Vidalia-0.2.0"
permalink: blog/technology-preview-marble-and-vidalia020
date: 2009-03-29
author: phobos
category: blog
tags: ["drag and drop OS X install", "experimental", "kde marble", "msi installer", "Qt updates", "technology preview", "vidalia"]
---

One of the most requested upgrades to [Vidalia](https://www.torproject.org/vidalia/) is a better map of the world. We looked into a few different technologies and decided on [KDE's Marble](http://edu.kde.org/marble/) interface. Marble enables an accurate mapping of nodes according to their geolocation, allows for future enhancements such as "click a country to start or end your Tor circuit", and plugins for extra data views. This also gives us the ability to use Qt's Webkit browser to display custom information about nodes, circuits, or anything else in a pop-up window. An anonymous funder covered the costs involved in developing this feature. We thank them for their support.

I've attached some screenshots to this blog post. You can download the relevant packages from the [Vidalia website](https://www.torproject.org/vidalia/dist/). If you want marble-enabled Vidalia, look for -marble- in the file name. Please report bugs on [Vidalia's Bug Tracker](http://trac.vidalia-project.net/wiki/ReportingBugs).

As of this release, there are now two branches of Vidalia, stable and alpha. The first release of the alpha branch is [Vidalia 0.2.0](https://www.torproject.org/vidalia/dist/). The stable branch is at [Vidalia 0.1.12](https://www.torproject.org/vidalia/dist/).

One last big change for OS X users is the drag and drop installer. There is no migration of old settings to new, nor do we clean up the old installs in /Library/Tor, /Library/Vidalia, /Library/Torbutton, /Library/Privoxy, etc. Follow [these instructions](https://www.torproject.org/docs/tor-doc-osx#uninstall) for how to remove the old vidalia-tor bundles from your computer if you want to completely test this alpha branch of Vidalia. We will figure out a better way to do this in the near future.

Remember, this is a technology preview. However, OS X installs are migrating to drag and drop. I've solely used Vidalia 0.2.0 and drag-and-drop installer for 3 months now. I even [previously blogged](http://blog.torproject.org/blog/experimental-os-x-drag-and-drop-vidalia-bundle-installer) about it.

Additional changes in alpha Vidalia 0.2.0:

- Qt 4.5.0 is used for Win32 and OS X Universal packages.
- We've switched from the Nullsoft Installer to the Microsoft System Installer (msi) for better integration with Microsoft Windows.
- There are non-Marble and Marble-enabled packages for Win32 and OS X Universal. OS X PowerPC based on OS X 10.3.9 isn't supported by Qt 4.5.x, therefore Marble-enabled Vidalia is not available
- Add support for changing UI languages without having to restart Vidalia.
- Add preliminary support for using the KDE Marble widget for the network map. It's currently a compile-time option and is disabled by default.
- Add support for displaying Tor's plaintext port warnings. Also gives the user the option to disable future warnings.
- Add an interface for displaying the geographic distribution of clients who have recently used a bridge operator's relay.
- Add tooltips to tree items in the help browser's table of contents. Some of the help topic labels are a bit long.
- Switch to a simpler About dialog and move the license information to a separate HTML-formatted display.
- Switch to a simpler drag-and-drop installer in the OS X bundles.
- Switch to an MSI-based installer on Windows.
- Clear the list of default CA certificates used by QSslSocket before adding the only one we care about. Suggested by coderman.
- Support building with Visual Studio again.
- Add a Debian package structure from dererk.
- Updated Albanian, Czech, Finnish, Polish, Portuguese, Romanian, Swedish, Turkish and many other translations.

<thead><tr>
<th>Attachment</th>
<th>Size</th> </tr></thead><tbody>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/2009-03-28-vidalia-marble-snapshot-0.png">2009-03-28-vidalia-marble-snapshot-0.png</a></td>
<td>368.42 KB</td> </tr>
 <tr class="even">
<td><a href="https://blog.torproject.org/files/2009-03-28-vidalia-marble-snapshot-1.png">2009-03-28-vidalia-marble-snapshot-1.png</a></td>
<td>231.13 KB</td> </tr>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/2009-03-28-vidalia-marble-snapshot-2.png">2009-03-28-vidalia-marble-snapshot-2.png</a></td>
<td>723.02 KB</td> </tr>
</tbody>

