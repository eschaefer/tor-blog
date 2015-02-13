---
layout: post
title: "Torbutton 1.4.1 Released"
permalink: torbutton-141-released
date: 2011-08-28 21:41:51
author: mikeperry
category: blog
status: closed
tags: ["firefox", "hotmail fixes", "new identity", "safecache", "tor browser", "tor browser bundle", "torbutton"]
---

Torbutton 1.4.1 has been released at: [https://www.torproject.org/torbutton/](https://www.torproject.org/torbutton/ "https://www.torproject.org/torbutton/")

This release features a "New Identity" menu option that clears browser state, closes tabs, and obtains a fresh Tor circuit for future requests. It also features a fix for breakage with Hotmail, and further isolates browser state and identifiers to the url bar domain (see [https://blog.torproject.org/blog/improving-private-browsing-modes-do-not...](https://blog.torproject.org/blog/improving-private-browsing-modes-do-not-track-vs-real-privacy-design "https://blog.torproject.org/blog/improving-private-browsing-modes-do-not-track-vs-real-privacy-design")).

However, the New Identity button and the Hotmail fix are only available to Tor Browser Bundle users. If you are still using Torbutton with a vanilla Mozilla Firefox, we strongly recommend you download the Tor Browser Bundle 2.2.x alphas from [https://www.torproject.org/dist/torbrowser/](https://www.torproject.org/dist/torbrowser/ "https://www.torproject.org/dist/torbrowser/") and report problems you experience, as we will be declaring them stable within the next release or two.

Stay tuned for a new Tor Browser release that contains Torbutton 1.4.1 tomorrow.

Here is the complete changelog:  
 \* bug 523: Implement New Identity (for TBB only)  
 \* bug 3580: Fix hotmail/live breakage (for TBB only)  
 \* bug 3748: Disable 3rd party HTTP auth  
 \* bug 3665: Fix several corner cases SafeCache isolation  
 \* bug 3739: Fix https-\>http CORS failure for SafeCache  
 \* bug 3414: Isolate window.name based on referrer policy  
 \* bug 3809: Disable referer spoofing (fixes navigation issues)  
 \* bug 3819: Fix API issue with cookie protections  
 \* bug 3820: Fix warning w/ session store filter
