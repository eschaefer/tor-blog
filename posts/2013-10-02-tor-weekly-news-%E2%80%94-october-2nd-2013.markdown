---
layout: post
title: "Tor Weekly News — October 2nd, 2013"
permalink: tor-weekly-news-%E2%80%94-october-2nd-2013
date: 10/02/2013
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the fourteenth issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the much-discussed Tor community.

# Tor Browser Bundle 3.0alpha4 released

On September 28<sup>th</sup>, Mike Perry released the [fourth alpha of the new Tor Browser Bundle 3.0 series](https://blog.torproject.org/blog/tor-browser-bundle-30alpha4-released). The main highlights of this series are the important usability improvements that integrate Tor configuration and control into the browser itself, rather than relying on the unmaintained Vidalia interface.

The latest iteration is based on Firefox 17.0.9esr, which brings with it a lot of important security fixes. It also fixes a fingerprinting issue by randomizing the timestamp sent when establishing an HTTPS connection.

Two small but important usability improvements in the new Tor Launcher component were made: users can now directly copy and paste “bridge” lines from the [bridge database](https://bridges.torproject.org/), while clock-skews that would prevent Tor from functioning properly are now reported to users.

Download your copy, test it, and report any problems you find. If you're feeling adventurous, you can also try out the crucial new security process by [independently reproducing the binaries](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/README.build) from the publicly-reviewable source code.

# Tor mini-hackathon at GNU 30<sup>th</sup> anniversary

The Tor mini-hackathon at the [GNU 30th anniversary event](https://www.gnu.org/gnu30/) took place over the weekend, and Nick Mathewson [sent out a brief report](https://lists.torproject.org/pipermail/tor-talk/2013-September/030238.html) on how things went. As well as working on proposal 220, which involves improvements to Tor server identity keys, Nick merged some small patches into the Tor mainline branch, and collected promises of several more to come. He also directed a few enquiring minds towards Tor's online community, saying “I hope we’ll be seeing more of some of the folks I talked to on our mailing lists and IRC channels soon”.

# Tor Stack Exchange page in private beta

The [Tor Stack Exchange page](http://tor.stackexchange.com), which [reached 100% commitment](http://area51.stackexchange.com/proposals/56447/tor-online-anonymity-privacy-and-security) last week, has now been moved into the ‘private beta’ stage. Runa Sandvik [clarified](https://lists.torproject.org/pipermail/tor-talk/2013-September/030187.html) that “the purpose behind it is to ensure that users who committed to the site’s proposal have a chance to start asking and answering questions, as well as help with the initial community building activities that will define and shape the site”. She added that “the more experts who participate in the private beta, the more certain it is that our page will move on to the next stage (i.e. the public beta).”

Fruitful discussions are already taking place: Karsten Loesing wrote to the wider community on the question of [what to do about contact information for bridge operators](https://lists.torproject.org/pipermail/tor-relays/2013-September/002936.html) after it was posed on Stack Exchange.

Roger Dingledine [put out a call](https://lists.torproject.org/pipermail/tor-dev/2013-September/005519.html) for Tor developers and anonymity researchers to participate in answering questions on the site, adding “Steven, Philipp, Jens, and I can't do it by ourselves.” If you have expert knowledge to contribute, please send an email to [help@rt.torproject.org](mailto:help@rt.torproject.org) to get an invitation!

# liballium: Pluggable Transports utility library in C

Yawning Angel announced a new library to ease the task of writing [pluggable transports](https://www.torproject.org/docs/pluggable-transports.html). liballium is a “simple library that handles the Tor Pluggable Transport Configuration protocol. The idea is for this library to be the C/C++ equivalent to [pyptlib](https://gitweb.torproject.org/pluggable-transports/pyptlib.git) (and maybe more, depending on how much time I have to work on it).”

The [code is available](https://github.com/Yawning/liballium) for review featuring “a reasonably well commented example.”

Feel free to follow up with “questions, comments, feedback”!

# Tor Help Desk Roundup

Multiple users wrote to the help desk asking for guidance setting up hidden service sites. The most straightforward documentation for hidden services is in the [torrc file](https://www.torproject.org/docs/faq.html.en#torrc) itself. A [more in-depth guide](https://www.torproject.org/docs/tor-hidden-service.html.en) can be found on the Tor Project website. The website also documents how [hidden services work](https://www.torproject.org/docs/hidden-services.html.en). Technical details can be found in the [Rendezvous Specification document](https://gitweb.torproject.org/torspec.git?a=blob_plain;hb=HEAD;f=rend-spec.txt).

# Monthly status reports for September 2013

The wave of regular monthly reports from Tor project members for the month of September has begun. [Runa Sandvik](https://lists.torproject.org/pipermail/tor-reports/2013-September/000341.html) released her report first, followed by reports from [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2013-September/000342.html), [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2013-October/000343.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2013-October/000344.html), and [Noel David Torres Taño](https://lists.torproject.org/pipermail/tor-reports/2013-October/000345.html).

# Miscellaneous news

Mike Perry published his [new GPG public key](http://pgp.mit.edu:11371/pks/lookup?op=get&search=0x29846B3C683686CC), [adding](https://lists.torproject.org/pipermail/tor-dev/2013-September/005518.html): “this new key will be used to sign email from me going forward, and will be used to sign software releases until such time as I get around to creating a second set of keys on a hardware token for that purpose”.

David Fifield [updated the Pluggable Transports bundles using the latest Tor Browser Bundle](https://blog.torproject.org/blog/pluggable-transports-bundles-2417-beta-2-pt3-firefox-1709esr). In order to benefit from the improvements and security fixes, please update!

intrigeri sent a [release schedule for Tails 0.21](https://mailman.boum.org/pipermail/tails-dev/2013-September/003719.html). The first release candidate should be out on October 20th.

Roger Dingledine sent out “a list of criteria to consider when evaluating pluggable transports for readiness of deployment to users”, asking for comments on [his initial draft](https://lists.torproject.org/pipermail/tor-dev/2013-September/005528.html).

If you have the necessary hardware and want to help Tails out, please test two upcoming features: [persistent printer settings](https://mailman.boum.org/pipermail/tails-dev/2013-September/003744.html) and [support for more SD card readers](https://mailman.boum.org/pipermail/tails-dev/2013-September/003757.html) (the “sdio” type).

* * *

This issue of Tor Weekly News has been assembled by harmony, Lunar, dope457, and Matt Pagan.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

