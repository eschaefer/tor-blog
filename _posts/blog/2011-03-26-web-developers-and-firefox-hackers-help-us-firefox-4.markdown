---
layout: post
title: "Web Developers and Firefox Hackers: Help us with Firefox 4"
permalink: blog/web-developers-and-firefox-hackers-help-us-firefox-4
date: 2011-03-26
author: mikeperry
category: blog
tags: ["firefox", "tor", "torbutton"]
---

We need some web-savvy people to help us audit the [Torbutton alpha series](https://www.torproject.org/torbutton/) for Firefox 4. I've performed a preliminary audit, and Torbutton 1.3.2-alpha should be safe from major issues, but a lot more testing is needed. In particular, we need people to test the [new Firefox 4 features](https://developer.mozilla.org/en/Firefox_4_for_developers).

The [notes from my preliminary audit](https://gitweb.torproject.org/torbutton.git/blob_plain/HEAD:/website/design/FF40_AUDIT) are available in the Torbutton git repository, but note that I have not tested everything that struck me as potentially troublesome, and there may be other things I missed too.

As a reminder, the types of things we are looking for are things that violate the [Torbutton Security Requirements](https://www.torproject.org/torbutton/en/design/#requirements), which may include new ways to bypass proxy settings, to fingerprint users, or to use novel identifiers to correlate Tor and Non-Tor activity.

In addition, we may have some funding to address [outstanding Torbutton-related bugs](https://www.torproject.org/torbutton/en/design/#FirefoxBugs) in Firefox. If you know C++ and/or Firefox internals, we should be able to pay you for your time to address these issues and shepherd the relevant patches through Mozilla's review process.

If you find issues, or if you are interested in working on fixing these bugs, please contact us at tor-assistants at torproject dot org. Torbutton bugs that you find can be added to the growing pile at the [Torbutton Bug Tracker](https://trac.torproject.org/projects/tor/report/14).

The sooner we get these issues taken care of, the sooner we can confidently release a stable Torbutton for Firefox 4.

