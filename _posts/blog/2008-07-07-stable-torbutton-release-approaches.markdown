---
layout: post
title: "Stable Torbutton Release Approaches"
permalink: blog/stable-torbutton-release-approaches
date: 2008-07-07
author: mikeperry
category: blog
tags: ["torbutton", "uglyrumors"]
---

For those of you just tuning in: Over the past year, I have been the maintainer of the [Torbutton Firefox extension](https://torbutton.torproject.org/dev/), adding a number of features and security enhancements to transform Torbutton from a simple proxy switcher into a secure way to [fully isolate all browser state](https://torbutton.torproject.org/dev/design/#requirements) from one proxy state to another and defend against all known [privacy and IP address leakage attacks](https://torbutton.torproject.org/dev/design/#adversary).

The release candidate phase of the extension started about a month ago, but with the release of Firefox 3 and Torbutton 1.2.0rc series occurring at the same time, we've hit a number of unexpected rough spots and snags. However, with the 1.2.0rc5 release of Torbutton, I'm pleased to report that the majority of those now seem to be [behind us](https://torbutton.torproject.org/dev/CHANGELOG) (a few annoying [Firefox bugs](https://torbutton.torproject.org/dev/design/#FirefoxBugs) notwithstanding).

Thanks to contributions from [arno](http://www.fdn.fr/~arenevier/), the Cookie Jar features now work with Firefox 3. They have even been improved to allow cookies to persist in memory-based jars across Tor toggle (as opposed to requiring Tor cookies to be written to disk to preserve them), which I personally already find very useful.

In addition, Torbutton is now much better about preserving users' custom Firefox preferences, including password and form fill preferences. Amusingly, the fact that we touch these preferences to protect users during Tor usage led to wild speculation on the [addons.mozilla.org page](https://addons.mozilla.org/en-US/firefox/addon/2275) that we were using them to steal passwords and send user details to Alexa. Of course, simply grepping the [source code](https://tor-svn.freehaven.net/svn/torbutton/trunk) for 'Alexa' and related IP addresses proves this to be false, but that didn't stop at least three people (or at least three sock puppets) from running with the rumor that Torbutton is a password stealer. Ignorance sure is contagious.

At any rate, after over a year since development began, it looks like we're finally getting really close to declaring Torbutton 1.2.0 'stable', which should coincide nicely with the upcoming Tor 0.2.0 stable release and bundles. It's been a long road!

