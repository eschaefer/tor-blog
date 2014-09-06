---
layout: post
title: "Google Chrome Incognito Mode, Tor, and Fingerprinting"
permalink: blog/google-chrome-incognito-mode-tor-and-fingerprinting
date: 2010-09-14
author: mikeperry
category: blog
tags: ["chrome", "EFF", "firefox", "google", "panopticlick", "privacy", "private browsing", "threat models", "torbutton"]
---

A few months back, I posted that [we have been in discussion](https://blog.torproject.org/blog/firefox-private-browsing-mode-torbutton-and-fingerprinting) with Mozilla about improving their Private Browsing mode to resist [fingerprinting](https://wiki.mozilla.org/Fingerprinting) and the [network adversary](https://wiki.mozilla.org/Security/Anonymous_Browsing). As I mentioned there, we have also been doing the same thing with Google for Google Chrome. Google has taken the same approach as Firefox for their Incognito mode, which means that it provides little to no protections against a network adversary.

This means that Chrome Incognito mode is not safe to use with Tor.

# The Story So Far

In general, Incognito's major shortcomings are plugins, fingerprinting, DNS leaks, SSL state leaks, auto-formfill and site-specific zoom. The Applied Crypto research group at Stanford recently published a [comparison of the four major browser's private browsing modes](http://crypto.stanford.edu/~dabo/pubs/abstracts/privatebrowsing.html) against a dedicated local and remote adversary which details some of these issues. The added poison for Tor is that plugins and DNS leaks can also reveal your IP address and complete web activity to the network adversary.

So, starting almost a year ago, we began providing feedback on Google Chrome's extension system APIs to ensure that Google is aware of the APIs that we and others need to write defenses against a network adversary.

We drew up [a wish list of API categories](https://groups.google.com/group/chromium-extensions/browse_thread/thread/ceba26ca9e2f6a78/e83920020719a6b2) that would be useful for privacy enhancing extensions. Many of the items on that first list were a bit far-reaching, and not all were strictly required to produce a Tor Mode for Google Chrome.

Over the past year, a rather astonishing amount of progress has been made on the Google Chrome Extension API set and also on many items of that list. In fact, work is now in progress on all the major API sets that we need to build a Tor Mode for Google Chrome, to port [HTTPS Everywhere](https://blog.torproject.org/blog/https-everywhere-firefox-addon-helps-you-encrypt-web-traffic), and also write a separate extension to provide defenses against fingerprinting and a network adversary, all using much simpler mechanisms that we had to use for the equivalent functionality in Firefox. It should also soon be possible for many similar privacy and security enhancing extensions to follow suit.

# Key Security and Privacy Enhancing APIs

The three API sets that will make this possible are [Web Request](http://www.chromium.org/developers/design-documents/extensions/notifications-of-web-request-and-navigation), [Content Scripts](https://code.google.com/chrome/extensions/dev/content_scripts.html), and the [Proxy APIs](http://dev.chromium.org/developers/design-documents/extensions/proxy%20proposal). Our prolific Tor volunteer [Robert Hogan](http://roberthogan.net/) has also been doing some work on [SSL related issues](https://code.google.com/p/chromium/issues/detail?id=30877) that will prove crucial, as well.

Each of these API sets, however, has its own shortcomings, rough edges, and missing pieces that need to be taken care of before it becomes suitable for us to use. I've been spending my time over the past couple months looking over these rough spots, documenting them, and informing Google. I'm also lucky enough to have my brother on the inside: he's one of the Google Chrome engineers who is working on these very APIs.

With his help, I've identified three major stumbling blocks to us and anyone else who is interested in writing security and privacy enhancing extensions on their platform.

# Three Major Stumbling Blocks

The first major stumbling block is that not only do we need to convince Google that these APIs are useful and needed, but there also has to be a way for them to implement the APIs easily, cleanly, and with very little overhead. Google Chrome is a very fine-tuned high performance browser, and keeping it this way is priority #1 for Google. At the present time, all of the extension APIs are asynchronous, and delivery is optimized so that increasing the number of installed extensions listening for events has negligible to absolutely zero effect on page load time.

However, security and privacy enhancing extensions will need the ability to actually block and modify requests with certainty. This means that fully asynchronous notification and response is not a viable option for some events.

Therefore, last month, I wrote up a [review of the Web Request APIs](https://groups.google.com/a/chromium.org/group/chromium-extensions/browse_thread/thread/17ea6efa15bfea0a), describing a method that could allow for blocking versions of three of the APIs to function with minimal performance impact, which is the key factor in Google's decision to provide them.

The second major stumbling block is the fact that none of the Google Extension APIs have yet been used to provide any real added security against any threat model, let alone one as [advanced as the one Torbutton employs](https://www.torproject.org/torbutton/design/#adversary). Extensions such as [KB SSL Enforcer](https://chrome.google.com/extensions/detail/flcpelgcagfhfoegekianiofphddckof?hl=en) and [Adblock Plus for Chrome](http://www.chromeextensions.org/appearance-functioning/adblock/) do not actually have any security guarantees beyond that which they can get through asynchronous DOM manipulation. There are also magical "special" urls and types of requests that currently are exempt from extension notification or control.

This is a real potential danger for us, and one that we only narrowly dodged with Firefox due only to the significantly more flexibility we have on that platform to reimplement arbitrary browser components, and to use different APIs and observers at different levels of notification. We have learned the hard way over the years that any URLs that go through special codepaths can leave the browser vulnerable to plugin injection, fingerprinting, unmasking, and exploitation.

Because of this, I took the time to write up [what extensions using the Chrome APIs for security will expect](https://groups.google.com/a/chromium.org/group/chromium-extensions/browse_thread/thread/f5a73572eb040bea). This includes things like uniform applicability, no functional surprises, and no unilateral exemptions.

The third stumbling block is how Google initially approached Incognito mode and privacy, and extension development in general. The entire extension system is built upon least privilege to ensure security rather than code reviews and audits. Extensions must request permissions to perform classes of actions, and Google is wary of creating permissions that are attractive to (semi-)malicious extensions that want control over everything.

Therefore, it was first believed that no extension should be allowed in Incognito mode, because no assurances could be made about its willingness or ability not to record usage information. This June, my brother finally [flipped the switch](http://blog.chromium.org/2010/06/extensions-in-incognito.html) to allow extensions to be run in Incognito mode, but only with with manual and explicit user approval, after installation.

As such, the behavior of an Incognito-specific extension still has not received a lot of attention at Google. This caused me to write a third post to describe [how Incognito-specific extensions might function](https://groups.google.com/a/chromium.org/group/chromium-extensions/browse_thread/thread/8a46d570807c9a72). My hope is that this will help provide another perspective towards extension developers in terms of adding privacy and security to Incognito mode, and to encourage discussions about how to best allow it.

# The Road Ahead

We're still many more months away from being able to write a full and working version of Tor Mode, HTTPS Everywhere, or the fingerprint resistance addon, but we're at least much closer than before, and everything seems to be heading in the right direction, so far.

For those who want to track our progress, as well as Google's, you can see the [entire list of remaining/important issues](https://trac.torproject.org/projects/tor/ticket/1925) on our bugtracker.

