---
layout: post
title: "Technology Preview:  Bridge by default for Microsoft Windows clients"
permalink: blog/technology-preview-bridge-default-microsoft-windows-clients
date: 2010-06-06
author: phobos
category: blog
tags: ["bridge by default", "bridges", "everyone as a bridge", "microsoft windows"]
---

We keep hearing from people around the world that clicking the 3 buttons to turn yourself into a bridge is too difficult todo for most users. These people have repeatedly asked for a "bridge by default" configuration in a package. Here it is: [http://archive.torproject.org/tor-package-archive/technology-preview/](http://archive.torproject.org/tor-package-archive/technology-preview/ "http://archive.torproject.org/tor-package-archive/technology-preview/")

When you install and run this package, you are a bridge relay helping censored users around the world access Tor and the uncensored Internet.
To understand more about bridges, read [https://www.torproject.org/bridges](https://www.torproject.org/bridges "https://www.torproject.org/bridges").

This is the installable Vidalia bundle configured to be a bridge by default. This is Tor 0.2.2.13-alpha, Vidalia 0.2.9, Polipo 1.0.4.1. The only difference between this bridge-bundle and the vidalia-bundle is the bridge configuration.

When started, Vidalia attempts to use UPnP to reconfigure any NAT/router device to open port 9001 for tor and 9030 for a directory mirror. The bandwidth is set to consume greater than 1.5 Mbps. It works just like the vidalia-bundle (because it is the vidalia-bundle) where if UPnP fails, it prompts you to open the correct ports on your NAT/router.

None of this is final configuration. It is merely a "does it work for you?" test package. So far, it's worked on the 4 different networks I've tried. Apologies to the 300 Chinese users who used my bridge on one of the test networks, only to have it go away a day later.

_Update 2010-06-11: Fixed a vidalia.conf issue which wasn't a problem, but looked like the controlport was open and un-authenticated. uploaded new binaries and removed the old ones. The bridge-bundle nsi file that creates this bundle is [in Vidalia svn](https://trac.vidalia-project.net/browser/vidalia/trunk/pkg/win32/bridge-bundle.nsi.in). Just replace vidalia-bundle.nsi.in with the bridge-bundle.nsi.in and create your bundle._

