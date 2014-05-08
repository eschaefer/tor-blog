---
layout: post
title: "Tor Weekly News — July, 10th 2013"
permalink: tor-weekly-news-%E2%80%94-july-10th-2013
date: 07/10/2013
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the second issue of Tor Weekly News, the weekly newsletter meant to cover what is happening in the great Tor community.

# First release candidate for Tor 0.2.4.x series

On July 3rd, Roger Dingledine [announced the release of Tor 0.2.4.15-rc](https://lists.torproject.org/pipermail/tor-talk/2013-July/028776.html). As “rc” suggests, it is the first release candidate for the 0.2.4.x series. This version fixes a few smaller bugs over the latest alpha, but “generally appears stable,” Roger noted.

Some highlights of [changes from 0.2.3.x](https://gitweb.torproject.org/tor.git/blob/b13c6becc:/ChangeLog):

- bridges now report the pluggable transports they support to the bridge authority ( [#3589](https://bugs.torproject.org/3589)),
- 
- IPv6 support ( [#5534](https://bugs.torproject.org/5534), [#5535](https://bugs.torproject.org/5535), [#6362](https://bugs.torproject.org/6362), [#6363](https://bugs.torproject.org/6363)),
- automatically forward the TCP ports of pluggable transport proxies using tor-fw-helper if PortForwarding is enabled ( [#6522](https://bugs.torproject.org/6522)),
- switch to a nonrecursive Makefile structure. Where available, now use automake’s “silent” make rules by default ( [#4567](https://bugs.torproject.org/4567)),
- many, many more small improvements and fixes.

Please [download it and test widely and wildly](https://www.torproject.org/dist/).

# New vulnerability in Tor Browser Bundle 2.3.25-10?

An [anonymous reporter reported](https://bugs.torproject.org/9195) a potential leak when using the Tor Browser Bundle on Windows. If Microsoft Security Essentials or another cloud based anti-virus solution is configured, downloads will automatically be sent to these external providers — bypassing Tor — once complete.

The reporter suggested setting the `browser.download.manager.scanWhenDone` property to `false` to prevent anti-virus solutions from starting without user interaction.

# The Tor Project is hiring a Lead Automation Engineer

Do you have experience programming in multiple languages, including Java, Python/Ruby, shell scripting, and JavaScript?

The Tor Project [opened a new position](https://lists.torproject.org/pipermail/tor-dev/2013-July/005119.html) as Lead Automation Engineer. The project seeks to deploy nightly builds and continuous integration for as many of its key software components and platform combinations as possible. Mike Perry wrote, “Candidates are expected to be capable of taking the lead in selecting, deploying, and maintaining multiple automation systems in several different programming languages.”

For more details, including information on how to apply, see [the job posting](https://www.torproject.org/about/jobs-lead-automation.html.en).

# check.torproject.org outage

[As Andrew Lewman wrote on Thursday, July 4th](https://blog.torproject.org/blog/tor-check-outage-03-and-04-july-2013), “over the past 24 hours `https://check.torproject.org` has been unavailable due to excessive DNS queries to the exitlist service. It seems there are a number of individuals and companies with commercial products relying upon this volunteer service. We finally hit the point where we couldn’t keep up with the queries and simply disabled the service”.

At the time of writing, the service is again available, but the project might “take it down as needed without notice.”

‘check.torproject.org’ is no longer the homepage for Tails since [January of this year](https://tails.boum.org/news/version_0.16/). The Tor Browser Bundle will also [switch to a new homepage in version 3](https://bugs.torproject.org/7494), currently in alpha stage.

Other software or services that depend on check.torproject.org should either migrate away or run their own version using [the source code for the web page](https://svn.torproject.org/cgi-bin/viewvc.cgi/Tor/check/trunk/). It is supported by a [database of running exit nodes that can be queried through DNS](https://trac.torproject.org/projects/tor/wiki/doc/TorDNSExitList).

If you wish to help, one need is to make it easier for third parties to get their own “check” service running. This means [getting the service more modular](https://bugs.torproject.org/9204) and improving [TorDNSEL](https://gitweb.torproject.org/tordnsel.git) or finishing [TorBEL](https://gitweb.torproject.org/torbel.git). Someone must also write documentation that is easy to follow.

# An experimental transparent Tor proxy for Windows

[basil announced a new experimental transparent Tor proxy for using Tor on Windows](https://lists.torproject.org/pipermail/tor-talk/2013-July/028809.html): “1) It (transparently) reroutes all HTTP traffic through the Tor anonymity network; and 2) It blocks all non-Tor traffic (including DNS) to and from your computer.”

The project is currently dubbed TorWall but the name is likely to change as it is problematic regarding the [Tor trademark](https://www.torproject.org/docs/trademark-faq) and [Roger pointed out](https://lists.torproject.org/pipermail/tor-talk/2013-July/028833.html) that there is already a discontinued project called Torwall. Roger also pointed out that transparent proxying might not be the best solutions “on the theory that if the given application isn’t specifically configured to use Tor, it’s probably going to screw up privacy-wise.”

[basil answered](https://lists.torproject.org/pipermail/tor-talk/2013-July/028840.html) by stating that the project was “really for those who know and understand the risks (possibly a very limited market?).” Feel free to give it a try if you do!

# Theft of Tor relay private keys?

On Tuesday, July 2nd, [Thomas H. expressed concern](https://lists.torproject.org/pipermail/tor-talk/2013-July/028749.html) about a hypothetical attacker breaking into a large number of nodes and stealing their private keys, combined with gathering all the traffic possible. “Wouldn’t this increase the likelihood that data from complete circuits can be decrypted and traced back to the original sender?”

In [response to this question](https://lists.torproject.org/pipermail/tor-talk/2013-July/028751.html), Mike Perry admits that he shares Thomas’ concerns: “If their intercepts are passive, merely stealing relays’ private identity key won’t accomplish much because Tor uses [Forward Secrecy](https://en.wikipedia.org/wiki/Perfect_forward_secrecy) for both the relay TLS links and for circuit setup. However, if their intercepts are active (as in they can arbitrarily manipulate traffic in-flight), then stealing either Guard node keys or directory authority keys allows complete route capture and traffic discovery of targeted clients”.

To avoid this danger, Mike Perry has previously suggested “changes to Tor to make such key theft easier to detect, less damaging, and harder to make use of” (see [#7126](https://bugs.torproject.org/7126), [#5968](https://bugs.torproject.org/5968)).

Mike also supports the idea of [regular identity key rotation for relays](https://bugs.torproject.org/5563). He would like to see support for default key rotation in the future.

Mike pointed out that currently changing an identity key too frequently has several disadvantages for the Tor network: “First, it takes the bandwidth measurement servers a couple days to ramp up your capacity of your new identity key, so you will spend a lot of time below your max throughput. Second, you would also likely never get the Guard flag. Third, there are also load balancing issues with Guard nodes where as soon as you get the Guard flag, it will take 1-2 months before clients switch to your new Guard, so you will also likely spend that time at less than your full capacity.”

If you are operating a relay, please check the wiki page with [tips for enhancing the relay’s security](https://trac.torproject.org/projects/tor/wiki/doc/TorRelaySecurity).

# A new interface to explore the Tor network

On June 25th, [Christian (makepanic) announced](https://lists.torproject.org/pipermail/tor-dev/2013-June/005063.html) a new web application to explore the Tor network. Based on the [Ember.js framework](http://emberjs.com/), it uses data from [Onionoo](https://onionoo.torproject.org/) to display information about Tor relays and bridges.

As [Karsten pointed out](https://lists.torproject.org/pipermail/tor-dev/2013-July/005122.html), this tool already has the same set of features as [Atlas](https://atlas.torproject.org/) — the current recommended way to get details about relays — and even a few more: it can “list 10 fastest relays on start page” and “show bridge details”. As Onionoo was designed exactly to offer a backend for various visualization tools, Karsten thinks “it’s fine to have more than one website providing access to Onionoo data. Yay, diversity.”

Feel free to play with [Tor Onionoo search](http://makepanic.github.io/emberjs-tor-onionoo/) or have a look at [its source code](https://github.com/makepanic/emberjs-tor-onionoo).

# Miscellaneous development news

Karsten Loesing has [updated GeoIP databases for Tor and Onionoo to July MaxMind databases](https://gitweb.torproject.org/tor.git/commit/2a61b0dd6be) without their A1 Anonymous Proxy ranges. See [#6266](https://bugs.torproject.org/6266) for more details on why and how we need to fix the data released by MaxMind.

It looks like the ‘start-tor-browser’ shell script cannot be used to start the Tor Browser from the graphical file manager on Ubuntu 13.04. If you have any great ideas, [please chime in](https://bugs.torproject.org/9091).

If you can write C code, you could make the lives of many relay operators easier by making tor configuration accept “bit/s” on top of the current “byte/s” [43]. The former, being more commonly used by network operators to describe bandwidth, could reduce a common case of confusion. It looks like [a patch would be pretty simple](https://bugs.torproject.org/9214)!

Work has started on a pluggable transport that would [combine the traffic obfuscation properties of obfsproxy with the address diversity of Flashproxy](https://bugs.torproject.org/7167).

intrigeri has [announced two “low-hanging fruits” sessions for Tails](https://mailman.boum.org/pipermail/tails-dev/2013-July/003240.html). Feel free to join the #tails IRC channel on July 11th at 8:00 UTC or on July 13, 2013, at 7:00 UTC. “Everyone interested in contributing to Tails is warmly welcome to join! The idea is to spend a while together on many small tasks that take less than 2 hours each, and are waiting in our TODO list for too long.” He also gave a list of candidate tasks.

As [Erinn Clark pointed out](https://lists.torproject.org/pipermail/tor-qa/2013-July/000157.html), the 3.x branch of Tor Browser is currently missing a map of relays similar to the one shown in Vidalia. The latter can be kept as a separate application, but this specific bit of functionality might simply be implementable using web technologies. Care to give it a try?

# More monthly status reports for June 2013

Continuing from last week, more monthly reports are now available for June 2013: [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2013-July/000280.html), [Aaron G.](https://lists.torproject.org/pipermail/tor-reports/2013-July/000284.html), [Runa A. Sandvik](https://lists.torproject.org/pipermail/tor-reports/2013-July/000285.html), [Mike Perry](https://lists.torproject.org/pipermail/tor-reports/2013-July/000286.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2013-July/000287.html), [Tails folks](https://lists.torproject.org/pipermail/tor-reports/2013-July/000288.html), and the [Tor help desk](https://lists.torproject.org/pipermail/tor-reports/2013-July/000289.html).

* * *

This issue of Tor Weekly News has been assembled by Lunar, luttigdev, dope457, whabib, Karsten Loesing and Peter Palfrader.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteer writers to watch the Tor community and report important news. Please see [the project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews) and write down your name if you want to get involved!

