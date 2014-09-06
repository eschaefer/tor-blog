---
layout: post
title: "Tor on the Nokia N900 (Maemo) GSM telephone"
permalink: blog/tor-nokia-n900-maemo-gsm-telephone
date: 2010-02-19
author: ioerror
category: blog
tags: ["mobile nokia n900 phone linux"]
---

We're always working on expanding the number of different devices and platforms where Tor runs. Today we've published an [installation document](https://www.torproject.org/docs/N900.html) that should help users of the Nokia N900 telephone to use the Tor network.

Tor is configured as a client by default. The Tor status applet will also run privoxy and configure the system wide preferences appropriately while Tor is enabled. Transparent proxying is not possible with the default N900 kernels at this time.

Please note that this is an experimental configuration. The web browser on the N900 does not have the protections that [Torbutton](https://www.torproject.org/torbutton/) provides.

For basic circumvention needs this configuration should be usable out of the box. At the moment, we're not seriously investigating Torbutton support for the N900 mobile web browser. If there is significant user demand for a mobile Torbutton this may change.

Many thanks to the fine folks at [synthesize.us](https://synthesize.us/home) for their help in the production of the N900 documentation.

