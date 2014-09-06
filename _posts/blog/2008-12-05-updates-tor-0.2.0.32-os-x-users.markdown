---
layout: post
title: "Updates on Tor 0.2.0.32 for OS X Users"
permalink: blog/updates-tor-0.2.0.32-os-x-users
date: 2008-12-05
author: phobos
category: blog
tags: ["apple os x", "packaging errors", "stable release"]
---

As detailed here, [http://archives.seul.org/or/talk/Dec-2008/msg00044.html](http://archives.seul.org/or/talk/Dec-2008/msg00044.html "http://archives.seul.org/or/talk/Dec-2008/msg00044.html"), there are some packaging fixes for OS X users in this 0.2.0.32 stable release.

> For OS X users, there is a packaging bugfix in 0.2.0.32 labelled as
> 0.2.0.32a in the available packages. It turns out for years we've been
> shipping a Info.plist with an incorrect key. The issue was discovered
> and reported as bug 876,
> [https://bugs.torproject.org/flyspray/index.php?id=876&do=details](https://bugs.torproject.org/flyspray/index.php?id=876&do=details "https://bugs.torproject.org/flyspray/index.php?id=876&do=details").
>
> The commit to fix the problem in the 0\_2\_0 branch is r17472:
> [http://archives.seul.org/or/cvs/Dec-2008/msg00037.html](http://archives.seul.org/or/cvs/Dec-2008/msg00037.html "http://archives.seul.org/or/cvs/Dec-2008/msg00037.html")
>
> The commit to fix the problem in the Vidalia 0.1 branch is r3361:
> [http://trac.vidalia-project.net/browser/vidalia/branches/vidalia-0.1/pkg...](http://trac.vidalia-project.net/browser/vidalia/branches/vidalia-0.1/pkg/osx?order=date&desc=1 "http://trac.vidalia-project.net/browser/vidalia/branches/vidalia-0.1/pkg/osx?order=date&desc=1")
>
> The bug is that the OS X Installer will prompt "The chosen volume
> contains software which is newer then [sic] the software you are
> installing."
>
> The problem is that the Installer looks in the file
> /Library/Receipts/Vidalia.pkg/Contents/Info.plist for
> CFBundleShortVersionString. We mistakenly called it
> CFBundleSortVersionString, which Apple inserts "1" as the value. The
> upgrade to Vidalia from 0.1.9 to 0.1.10 apparently triggered the issue.
>
> The fix is to put the correct value in place for the future. The
> simplest way to do this is to have the users click "Continue" when
> prompted. We could have spent a lot of time trying to fix it for the
> user to hide the issue, but well, that is fraught with problems and
> complexities. A simple click of "Continue" is far simpler and less
> error prone.
>
> The difference between the released 0.2.0.32 Tor code is the inclusion
> of r17472. It's not really 0.2.0.32a per se, but since we lack package
> versions, I had to distinguish it in some way.
