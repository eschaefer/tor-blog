---
layout: post
title: "New Tor Browser Bundle packages"
permalink: new-tor-browser-bundle-packages-0
date: 2010-12-15
author: erinn
category: blog
tags: ["bug fixes", "firefox updates", "https everywhere", "polipo", "tbb", "tor browser bundle"]
---

 **Linux Bundles**

**Important:** Polipo has been removed from the Linux Tor Browser Bundle. Please read the full changelog and [report bugs](https://trac.torproject.org) if you have any problems.

**1.1.0: Released 2010-12-13**

- Update Firefox to 3.6.13
- Update NoScript to 2.0.7
- Update HTTPS Everywhere to 0.9.9.development.1
  - This version of HTTPS-Everywhere is patched to include a fix for bug #2096 which  
 prevented globally installed versions of the extension from working. It also  
 includes better protection from Firesheep. See the changelog here:  
 [https://www.eff.org/files/Changelog.txt](https://www.eff.org/files/Changelog.txt "https://www.eff.org/files/Changelog.txt")

- Add Chris Davis's patch
  - This patch improves Firefox's SOCKS support and eliminates the need for Polipo, so  
 Torbutton has been reconfigured to just use a SOCKS proxy. Polipo has been removed  
 entirely from this release of the Tor Browser Bundle. If this causes you problems,  
 please file a bug: [https://trac.torproject.org/projects/tor](https://trac.torproject.org/projects/tor "https://trac.torproject.org/projects/tor")

- Rebuild all binaries against glibc 2.7 so they work for older distros again

**OS X bundle**

**1.0.7: Released 2010-12-14**

- Update Firefox to 3.6.13
- Update NoScript to 2.0.7
- Update HTTPS-Everywhere to 0.9.9.development.1
  - This version of HTTPS-Everywhere is patched to include a fix for bug #2096 which  
 prevented globally installed versions of the extension from working. It also  
 includes better protection from Firesheep. See the changelog here:  
 [https://www.eff.org/files/Changelog.txt](https://www.eff.org/files/Changelog.txt "https://www.eff.org/files/Changelog.txt")

**Windows bundles**

**1.3.14: Released 2010-12-13**

- Update Firefox to 3.6.13
- Update HTTPS-Everywhere to 0.9.9.development.1
  - This version of HTTPS-Everywhere is patched to include a fix for bug #2096 which  
 prevented globally installed versions of the extensions from working. It also  
 includes better protection from Firesheep. See the changelog here:  
 [https://www.eff.org/files/Changelog.txt](https://www.eff.org/files/Changelog.txt "https://www.eff.org/files/Changelog.txt")

