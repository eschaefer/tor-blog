---
layout: post
title: "Tor Weekly News — November 27th, 2013"
permalink: tor-weekly-news-%E2%80%94-november-27th-2013
date: 2013-11-27
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the twenty-second issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Round of updated Tor Browser Bundles

Mozilla put out an [urgent security release](https://www.mozilla.org/en-US/firefox/17.0.11/releasenotes/) of the stable Firefox branch with version 17.0.11esr. The [stable version of the Tor Browser Bundle has been updated](https://blog.torproject.org/blog/new-tor-browser-bundles-firefox-17011esr-and-tor-02418-rc) accordingly. The 2.4 release candidate also received an update, together with the latest incarnation of tor 0.2.4.18-rc. Both were then given [a further update](https://blog.torproject.org/blog/64-bit-gnulinux-tor-browser-bundles-updated) due to an issue on 64 bit GNU/Linux systems.

The 3.0 branch saw the [release of 3.0rc1](https://blog.torproject.org/blog/tor-browser-bundle-30rc1-released) which — on top of updating its base software — fixed a build reproducibility issue on Windows, and a few other small fixes.

An [updated version of Tails](https://mailman.boum.org/pipermail/tails-dev/2013-November/004152.html) and the pluggable transport bundle are still in the making at the time of writing.

# Tor is looking for a Browser Hacker and an Extension Developer!

Mike Perry [wrote a blog post](https://blog.torproject.org/blog/tor-looking-browser-hacker-and-extension-developer) to announce two new positions available at the Tor Project: “We are looking for a [C++ browser developer](https://www.torproject.org/about/jobs-browserhacker.html) to work on our Firefox-based browser, and a [Firefox extension developer](https://www.torproject.org/about/jobs-extdev.html.en) to work on our growing number of Firefox extensions. Our ideal candidates would be comfortable in both roles, but we are also interested in hearing from people with either skillset.”

Look at the job descriptions for more details and how to apply for these exciting opportunities to make Tor software even better.

# “Safeplug”

Roman Mamedov [reported](https://lists.torproject.org/pipermail/tor-talk/2013-November/031199.html) that the Californian company Cloud Engines is now shipping a device called the “Safeplug”. Exactly how the device works is unclear, but according to their FAQ, it looks like a router which transparently directs its client connections through Tor.

Such an approach is known to be flawed. [Sean Alexandre](https://lists.torproject.org/pipermail/tor-talk/2013-November/031200.html) was prompt in reminding everyone that “application protocols can still reveal your identity”, and quoted the [warning on Tor’s download page](https://www.torproject.org/download/download-easy.html#warning): “To avoid problems with Tor configuration, we strongly recommend you use the Tor Browser Bundle. It is pre-configured to protect your privacy and anonymity on the web as long as you’re browsing with the Tor Browser itself. Almost any other web browser configuration is likely to be unsafe to use with Tor.”

Aaron Gibson [detailed other concerns](https://lists.torproject.org/pipermail/tor-talk/2013-November/031215.html), namely the absence of source code or design documents, the mandatory router registration procedure, issues with the automatic update system, and the terms of service. He also criticized the “torified everything” approach and outlined an alternative which he had discussed with Roger Dingledine: “providing a captive portal that would instruct a user to download a copy of TBB and use the local router device as a first hop into the Tor network, perhaps by configuring the device as a bridge.”

On the upside, Andrew Lewman [views the product](https://lists.torproject.org/pipermail/tor-talk/2013-November/031204.html) as “a fine test case for consumer-level torouter market analysis. It would be great to learn 6 months from now how many they sold and a summary of customer feedback.” Despite having “ [lots of concerns](https://lists.torproject.org/pipermail/tor-talk/2013-November/031235.html)”, Andrew is “trying to discuss them with Cloud Engines” and praised the community for “doing a fine job of raising questions”.

# Miscellaneous news

Nick Mathewson [gave the number 223](https://lists.torproject.org/pipermail/tor-dev/2013-November/005836.html) to Esfandiar Mohammadi’s proposal titled “ [Ace: Improved circuit-creation key exchange](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/223-ace-handshake.txt)”.

Matt Pagan [reported](https://lists.torproject.org/pipermail/tor-reports/2013-November/000385.html) on his trip to Washington, D.C., USA for the Rally Against Mass Surveillance. He gave an account of his talk during the cryptoparty and the march that happened the next day.

Arturo Filastò sent his [report](https://lists.torproject.org/pipermail/tor-reports/2013-November/000386.html) about his activities in October.

Nathan Freitas reported on his [efforts to use GeckoView on Android 4.4](https://lists.torproject.org/pipermail/tor-dev/2013-November/005857.html), which can be seen as the “first step towards Tor Browser on Android”.

Kevin Dyer [announced](https://lists.torproject.org/pipermail/tor-dev/2013-November/005861.html) a new release of a [pluggable transport powered by Format-Transforming Encryption](https://fteproxy.org/). Cross-platform builds of the pluggable transport Tor Browser Bundle are available for download for the adventurous.

# Tor help desk roundup

Echoing the tor-talk thread summarized above, multiple people asked whether or not the Tor Project could recommend the Safeplug device.

An OS X user asked if it was always necessary to open the Tor Browser folder in order to start the Tor Browser Bundle. It is possible to create an alias in Mac OS or a shortcut in Windows to the “Start Tor Browser” script and place that alias or shortcut in a convenient place,  
such as the Desktop.

* * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, harmony, Philipp Winter, and dope457.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

