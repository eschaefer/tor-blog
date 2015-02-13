---
layout: post
title: "TorCheck rewritten and relaunched!"
permalink: torcheck-rewritten-and-relaunched
date: 2008-05-01 04:26:30
author: ioerror
category: blog
status: closed
tags: ["i18n", "l10n", "TorCheck"]
---

Nick encouraged me to rewrite TorCheck in Python. Roger encouraged me to automatically translate TorCheck messages into a given locale when specifically requested. This is finished, reasonably stable and live right now.

As usual, TorCheck queries the [TorDNSEL](http://exitlist.torproject.org/) to determine if the visitor is possibly using a proper Tor exit node.

As an added bonus, TorCheck is now localized with useful information in [Brazilian Portuguese](//check.torproject.org/?lang=pt_BR), [Chinese](https://check.torproject.org/?lang=zh_CN), [English](//check.torproject.org/?lang=en_US), [German](//check.torproject.org/?lang=de), [Farsi](//check.torproject.org/?lang=fa_IR), [Japanese](//check.torproject.org/?lang=ja), [Polish](https://check.torproject.org/?lang=pl) and [Spanish](https://check.torproject.org/?lang=es_ES).

Users of the [TorBrowser](https://www.torproject.org/torbrowser/) will now automatically have a fully translated browsing experience. Any other user can simply select the proper ISO 3166 Code for their country and make a GET request with a properly set LANG query string as linked above. There's a good chance that your locale will be supported in the future if it isn't already.

If you'd like to pitch in and translate TorCheck into your locale, we'd love the help! Feel free to [check the translations directory for current translations](https://tor-svn.freehaven.net/svn/check/trunk/i18n/) and see if your locale has been translated. If you'd like to add a locale we haven't translated, download a copy of [the PO template file](https://tor-svn.freehaven.net/svn/check/trunk/i18n/TorCheck.pot) and translate away!

Give the new [TorCheck](https://check.torproject.org) a try today!
