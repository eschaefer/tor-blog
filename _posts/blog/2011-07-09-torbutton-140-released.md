---
layout: post
title: "Torbutton 1.4.0 Released"
permalink: torbutton-140-released
date: 2011-07-09 17:39:06
author: phobos
category: blog
status: closed
tags: ["anonymity", "firefox extensions", "firefox plugins", "firefox privacy", "torbutton"]
---

Torbutton 1.4.0 has been released at:  
 [https://www.torproject.org/torbutton/](https://www.torproject.org/torbutton/ "https://www.torproject.org/torbutton/")

The addon has been disabled on addons.mozilla.org. Our URL is now  
 canonical.

This release features support for Firefox 5.0, and has been tested  
 against the vanilla release for basic functionality. However, it has  
 not been audited for Network Isolation, State Separation, Tor  
 Undiscoverability or Interoperability issues[1] due to toggling under  
 Firefox 5.

If you desire Torbutton functionality with Firefox 4/5, we recommend  
 you download the Tor Browser Bundle 2.2.x alphas from  
 [https://www.torproject.org/dist/torbrowser/](https://www.torproject.org/dist/torbrowser/ "https://www.torproject.org/dist/torbrowser/") or run Torbutton in its  
 own separate Firefox profile.

The reasons for this shift are explained here:  
 [https://blog.torproject.org/blog/toggle-or-not-toggle-end-torbutton](https://blog.torproject.org/blog/toggle-or-not-toggle-end-torbutton "https://blog.torproject.org/blog/toggle-or-not-toggle-end-torbutton")

If you find bugs specific to Firefox 5, toggling, and/or extension  
 conflicts, file them under the component "Torbutton":  
 [https://trac.torproject.org/projects/tor/report/14](https://trac.torproject.org/projects/tor/report/14 "https://trac.torproject.org/projects/tor/report/14")

Bugs that still apply to Tor Browser should be filed under component  
 "TorBrowserButton":  
 [https://trac.torproject.org/projects/tor/report/39](https://trac.torproject.org/projects/tor/report/39 "https://trac.torproject.org/projects/tor/report/39")

Bugs in the "Torbutton" component currently have no maintainer  
 available to fix them. Feel free to step up.

(No, simply mis-filing your Torbutton toggle bugs under  
 TorBrowserButton won't cause them to get fixed accidentally. It will  
 just annoy me slightly as I relocate them to the correct component).

Here is the complete changelog:  
 \* bug 3101: Disable WebGL. Too many unknowns for now.  
 \* bug 3345: Make Google Captcha redirect work again.  
 \* bug 3399: Fix a reversed exception check found by arno.  
 \* bug 3177: Update torbutton to use new TorBrowser prefs.  
 \* bug 2843: Update proxy preferences window to support env var.  
 \* bug 2338: Force toggle at startup if tor is enabled  
 \* bug 3554: Make Cookie protections obey disk settings  
 \* bug 3441: Enable cookie protection UI by default.  
 \* bug 3446: We're Firefox 5.0, we swear.  
 \* bug 3506: Remove window resize event listener.  
 \* bug 1282: Set fixed window size for each new window.  
 \* bug 3508: Apply Stanford SafeCache patch (thanks Edward, Collin et al).  
 \* bug 2361: Make about window work again on FF4+.  
 \* bug 3436: T(A)ILS was renamed to Tails.  
 \* bugfix: Fix a transparent context menu issue on Linux FF4+.  
 \* misc: Squelch exception from app launcher in error console.  
 \* misc: Make DuckDuckGo the default Google Captcha redirect destination.  
 \* misc: Make it harder to accidentally toggle torbutton.

1. [https://www.torproject.org/torbutton/en/design/\#requirements](https://www.torproject.org/torbutton/en/design/#requirements "https://www.torproject.org/torbutton/en/design/#requirements")
