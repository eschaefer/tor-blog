---
layout: post
title: "New Tor Browser Bundle packages"
permalink: new-tor-browser-bundle-packages
date: 11/26/2010
author: erinn
category: blog
tags: ["alpha releases", "bug fixes", "stable releases", "tbb", "tor browser bundle"]
---

There are new browser bundles out with the updated Tor versions (0.2.2.19-alpha and 0.2.1.27) that work with the latest OpenSSL.

**Windows Tor Browser Bundles**  
There were some controversial changes recently made to the Windows bundle, and for those I apologize. I have removed BetterPrivacy and NoScript from them pending further testing. The whole changelog:

**1.3.13: Released 2010-11-25**

- update Tor to 0.2.1.27
- update Pidgin to 2.7.5
- update OpenSSL to 0.9.8p
- fix Firefox extension install path so extensions show in the installed add-ons list
- disable Firefox's ability to search the Windows registry path for system-wide  
 plugins and extensions (closes: [#2118](https://trac.torproject.org/projects/tor/ticket/2118))
- remove NoScript and BetterPrivacy from stable bundle until they receive more  
 testing

**OS X and Linux bundles**

**OS X**  
**1.0.6: Released 2020-11-24**

- Update Tor to 0.2.2.19-alpha

**Linux**  
**1.0.17: Released 2010-11-24**

- Update Tor to 0.2.2.19-alpha

Please report bugs on [our bug tracker](https://trac.torproject.org/).

