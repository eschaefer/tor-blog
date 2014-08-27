---
layout: post
title: "Firefox Private Browsing Mode, Torbutton, and Fingerprinting"
permalink: firefox-private-browsing-mode-torbutton-and-fingerprinting
date: 2010-06-30
author: mikeperry
category: blog
tags: ["EFF", "firefox", "panopticlick", "privacy", "private browsing", "threat models", "torbutton"]
---

Last week, [Peter Eckersley](http://www.eff.org/about/staff/peter-eckersley) and I met with the Mozilla team in Mountain view to discuss web fingerprinting, privacy and Torbutton. I gave [an updated version of my Torbutton Design talk](https://www.torproject.org/torbutton/design/MozillaBrownBag.pdf), and Peter discussed [Panopticlick](http://panopticlick.eff.org/). Mozilla was primarily interested in hearing about these projects in the context of their [Private Browsing Mode](https://support.mozilla.com/en-us/kb/private+browsing), which they unveiled in Firefox 3.5.

The [primary goal](https://wiki.mozilla.org/PrivateBrowsing) of their Private Browsing Mode is to protect against a local after-the-fact attacker - an attacker that has local access to a user's filesystem after browsing has taken place. They offer some limited protections against a network adversary, but this was not their initial goal, and is primarily a side effect of trying to protect against "helpful" web services, such as Google Search History, which record your activity somewhere other than your PC.

This is a significantly weaker adversary model than [the one used in the Torbutton design.](https://www.torproject.org/torbutton/design/#adversary) As a result, from the point of view of Tor usage, Firefox Private Browsing mode suffers from a number of weaknesses that Torbutton does not.

In particular, Firefox does not presently concern itself with plugins, form and password autocompletion, SSL state, Live Bookmarks, external protocols and applications, or browser fingerprinting. The Applied Crypto research group at Stanford recently published a [comparison of the four major browser's private browsing modes](http://crypto.stanford.edu/~dabo/pubs/abstracts/privatebrowsing.html) against a dedicated local and remote adversary which details some of these issues.

It turns out there is some developer interest inside Mozilla in [improving resistance to fingerprinting](https://wiki.mozilla.org/Fingerprinting), [improving privacy against third party content](https://wiki.mozilla.org/Thirdparty), and hardening their Private Browsing Mode in general, despite most of these issues being outside of their original model. The current plan is to investigate what would be necessary to develop an [Anonymous Browsing Mode](https://wiki.mozilla.org/Security/Anonymous_Browsing) that would either take the form of a privacy setting, an enhancement to Private Browsing Mode, or an entirely independent browsing mode. The trick now is to transform this developer interest into something that motivates the Firefox Product Management team to get fully behind the proposed improvements.

As such, Peter and I have been spending some time updating the [Fingerprinting](https://wiki.mozilla.org/Fingerprinting) and [Anonymous Browsing](https://wiki.mozilla.org/Security/Anonymous_Browsing) wiki pages to describe [who would want such privacy features](https://wiki.mozilla.org/Security/Anonymous_Browsing#Use_Cases), and [how they would behave](https://wiki.mozilla.org/Security/Anonymous_Browsing#Behavior), as well as updating and adding relevant Mozilla Bugzilla entries. I've also updated the list of [Torbutton Firefox Bugs](https://www.torproject.org/torbutton/design/#FirefoxBugs) to reflect some of the more sophisticated unsolved fingerprinting issues that were brought up during our meeting.

This July, the two of us will be doing the same thing with the Google Chrome Privacy Team in Berlin while at the [Privacy Enhancing Technologies Symposium](https://blog.torproject.org/events/tor-privacy-enhancing-technologies-symposium-berlin-germany). This is primarily to follow up on a meeting we had with Google in December, where we discussed [the barriers to the development of a Torbutton for Google Chrome](https://groups.google.com/group/chromium-extensions/browse_thread/thread/ceba26ca9e2f6a78?hl=en), and to discuss relevant fingerprinting issues and similar shortcomings of the [Google Chrome Incognito Mode](http://www.google.com/support/chrome/bin/answer.py?answer=95464).

Look for a future blog post in August detailing the results of that discussion.

