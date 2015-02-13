---
layout: post
title: "New Tor Browser Bundles"
permalink: new-tor-browser-bundles-4
date: 2011-08-31 21:55:03
author: erinn
category: blog
status: closed
tags: ["ohdiginotaryoudidnt", "package updates", "security fixes", "tbb torbrowser"]
---

We have updated the stable Tor Browser Bundles to Firefox 6.

**There are no longer any stable Tor Browser Bundles with the 3.6.x series of Firefox.** We were using pre-built binaries on some platforms and owing to the recent [DigiNotar debacle](https://blog.torproject.org/blog/diginotar-debacle-and-what-you-should-do-about-it), we no longer felt comfortable shipping versions of Firefox that we were unable to patch. We build all Firefox 6 binaries from source, with our own [set of patches](https://gitweb.torproject.org/torbrowser.git/tree/refs/heads/maint-2.2:/src/current-patches), including some [specific to the DigiNotar issue](https://gitweb.torproject.org/torbrowser.git/commit/0be3b043afa0e54d207f603a3bf3716f6165caa1).

We'd originally planned to drop support for Firefox 3.6 bundles on September 10th, but this moved up the date a bit. The new Tor Browser Bundles are much more feature-rich than the previous bundles, but users may still experience unexpected behavior. Please report all bugs to [https://trac.torproject.org/](https://trac.torproject.org/ "https://trac.torproject.org/").

Windows users will see the biggest difference between the old stable bundle and the new stable bundle. In addition to upgrading Firefox, it includes the latest stable release of [Tor 0.2.2.32](http://blog.torproject.org/blog/tor-02232-released),[Vidalia 0.2.14](http://blog.torproject.org/blog/vidalia-0214-out) and [Torbutton 1.4.1](http://blog.torproject.org/blog/torbutton-141-released). These three upgrades together allow you to run the Tor Browser Bundle at the same time as a system Tor, or even multiple copies of the Tor Browser Bundle in different directories, by [dynamically choosing available ports](https://trac.torproject.org/projects/tor/ticket/2264).

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Tor Browser Bundle (2.2.32-2)**

-   Update Firefox to 6.0.1, with an additional patch to exclude DigiNotar completely
    -   [https://gitweb.torproject.org/torbrowser.git/commit/0be3b043afa0e54d207f...](https://gitweb.torproject.org/torbrowser.git/commit/0be3b043afa0e54d207f603a3bf3716f6165caa1 "https://gitweb.torproject.org/torbrowser.git/commit/0be3b043afa0e54d207f603a3bf3716f6165caa1")
    -   [http://blog.mozilla.com/security/2011/08/29/fraudulent-google-com-certif...](http://blog.mozilla.com/security/2011/08/29/fraudulent-google-com-certificate/ "http://blog.mozilla.com/security/2011/08/29/fraudulent-google-com-certificate/")
    -   [http://googleonlinesecurity.blogspot.com/2011/08/update-on-attempted-man...](http://googleonlinesecurity.blogspot.com/2011/08/update-on-attempted-man-in-middle.html "http://googleonlinesecurity.blogspot.com/2011/08/update-on-attempted-man-in-middle.html")
-   **OS X specific:** Rebuild 32-bit binaries with backwards compatibility options so TBB works on OSX 10.5 (closes: \#3671)
-   Update Libevent to 2.0.14-stable
-   Update torbrowser.version string in prefs.js to have more information (see \#3504)
-   Enable internationalized bundles by adding and changing the  
     general.useragent.locale pref in prefs.js

