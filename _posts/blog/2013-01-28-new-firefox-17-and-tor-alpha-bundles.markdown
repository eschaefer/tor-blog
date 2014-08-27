---
layout: post
title: "New Firefox 17 and Tor alpha bundles"
permalink: new-firefox-17-and-tor-alpha-bundles
date: 2013-01-28
author: erinn
category: blog
tags: ["firefox updates", "tbb", "tor", "tor alpha", "tor browser", "tor browser bundle"]
---

We have some test Tor Browser Bundles available for testing! They contain Firefox 17.0.2esr which we're planning to switch to in February. Just as a reminder: **these are alpha bundles** . We're still testing them ourselves but we want to get them out for wider circulation so we can find out about any dealbreaker bugs before moving Firefox 17 into the stable bundles. For the more sophisticated users out there, we'd love it if you could run Wireshark with the bundles and let us know if you see anything untoward.

Alpha Tor Browser Bundles can be downloaded here:

[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en "https://www.torproject.org/projects/torbrowser.html.en")

All of the Tor packages have been updated with Tor 0.2.4.9-alpha as well.

[https://www.torproject.org/download/download-easy](https://www.torproject.org/download/download-easy "https://www.torproject.org/download/download-easy")

**Tor Browser Bundle (2.4.9-alpha-1)**

- Update Firefox to 17.0.2esr
- Update Tor to 0.2.4.9-alpha
- Update Torbutton to 1.5.0pre-alpha
- Update NoScript to 2.6.4.3
- Update HTTPS-Everywhere to 4.0development.5
- Add Mozilla's PDF.js extension to give people the ability to read PDFs in  
 TBB
- Prevent TBB from trying to access the X session manager (closes: #5261)

  - Firefox patch changes:
  - Isolate image cache to url bar domain (closes: #5742 and #6539)
  - Enable DOM storage and isolate it to url bar domain (closes: #6564)
  - Include nsIHttpChannel.redirectTo API for HTTPS-Everywhere (closes: #5477)
- Misc preference changes:

  - Disable DOM performance timers (dom.enable\_performance) (closes: #6204)
  - Disable HTTP connection retry timeout (network.http.connection-retry-timeout) (closes: #7656)
  - Disable full path information for plugins (plugin.expose\_full\_path) (closes: #6210)
  - Disable NoScript's block of remote WebFonts (noscript.forbidFonts) (closes: #7937)

