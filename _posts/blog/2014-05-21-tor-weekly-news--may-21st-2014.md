---
layout: post
title: "Tor Weekly News — May 21st, 2014"
permalink: tor-weekly-news--may-21st-2014
date: 2014-05-21 07:00:00
author: lunar
category: blog
status: closed
tags: ["tor weekly news"]
---

Welcome to the twentieth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

Tor 0.2.4.22 is out
===================

A [new version of the Tor stable branch was released](https://lists.torproject.org/pipermail/tor-talk/2014-May/032956.html) on May 16th: “Tor 0.2.4.22 backports numerous high-priority fixes from the Tor 0.2.5 alpha release series. These include blocking all authority signing keys that may have been affected by the OpenSSL ‘heartbleed’ bug, choosing a far more secure set of TLS ciphersuites by default, closing a couple of memory leaks that could be used to run a target relay out of RAM, and several others.”

For more details, look at the [full changelog](https://gitweb.torproject.org/tor.git/blob_plain/2ee56e4c2:/ChangeLog). The source is available at the [usual location](https://www.torproject.org/dist/). Packages should be coming shortly, if not [already available](http://packages.qa.debian.org/t/tor/news/20140517T102023Z.html).

Digital Restrictions Management and Firefox
===========================================

Mozilla’s decision to [support playing media with digital restrictions](https://hacks.mozilla.org/2014/05/reconciling-mozillas-mission-and-w3c-eme/) in Firefox by implementing the W3C EME specification has raised a fair amount of controversy. Paul Crable [wanted to know](https://lists.torproject.org/pipermail/tor-talk/2014-May/032947.html) what it meant for the Tor Browser.

Mike Perry [answered](https://lists.torproject.org/pipermail/tor-talk/2014-May/032985.html) that “simply removing the DRM will be trivial, and it will be high on our list of tasks”.

But he also explained his worries regarding a “per-device unique identifier” that Firefox would provide as part of the implementation: “it is likely that this identifier will soon be abused by all sorts of entities, […] quickly moving on to the advertising industry (why not play a short device-linked DRM video with your banner ad? You get a persistent, device-specific tracking identifier as part of the deal!). I think it is also quite likely that many arbitrary sites will actually deny access to users who do not provide them with such a device-id, if only due to ease of increased revenue generation from a fully identified userbase.”

Mike has [raised the issue](https://groups.google.com/forum/#!topic/mozilla.dev.privacy/3jA9zt1pXVo) on Mozilla’s dev-privacy mailing-list where Henri Sivonen replied that device-identifying information will be hashed together with a “per-origin browser-generated secret“ that “persists until the user asks the salt to be forgotten”. So it does not look as gloom as it initially appeared. As always, the devil is in the details.

Miscellaneous news
==================

David Goulet [reported](https://lists.torproject.org/pipermail/tor-dev/2014-May/006872.html) on the status of the development of Torsocks 2.0, the library for safely using applications with Tor.

Karsten Loesing [posted](https://blog.torproject.org/blog/10-years-collecting-tor-directory-data) on the Tor Blog to commemorate the tenth anniversary of the first archived Tor directory, and discussed the different ways in which the public archive of directory data is being used for research and development.

Karsten also [notified](https://lists.torproject.org/pipermail/tor-dev/2014-May/006884.html) the community of a change in the compression algorithm used for the tarballs of archived metrics data, which has reduced their total size from 212 gigabytes to 33 — an 85% gain!

[Knock](https://gnunet.org/knock) is a variant of port-knocking that might be useful in the future for pluggable transports. “As Knock uses two fields in the TCP header in order to hide information and we explicitly want to be compatible with machines sitting in typical home networks”, [writes](https://lists.torproject.org/pipermail/tor-dev/2014-May/006873.html) Julian Kirsch, “we thus created a program which tests if Knock would work in your environment.” Please [give it a try](https://gnunet.org/knock_nat_tester) to help the team figure out if Knock could be deployed in the wild.

Thanks to [Jesse Victors](https://lists.torproject.org/pipermail/tor-mirrors/2014-May/000581.html), [Andrea](https://lists.torproject.org/pipermail/tor-mirrors/2014-May/000589.html), [Nicholas Merrill](https://lists.torproject.org/pipermail/tor-mirrors/2014-May/000592.html), and [Martin A.](https://lists.torproject.org/pipermail/tor-mirrors/2014-May/000594.html) for running mirrors of the Tor Project website!

Michael Schloh von Bennewitz has been busy analyzing a [disk leak](https://bugs.torproject.org/9701) in Tor Browser: when one copies a significant chunk of text to the clipboard, a temporary file is created with its content. Michael found a possible fix and is [welcoming reviews](https://lists.torproject.org/pipermail/tor-dev/2014-May/006875.html).

Nicolas Vigier has been [investigating](https://lists.torproject.org/pipermail/tbb-dev/2014-May/000050.html) some extra connections made by the Tor Browser on startup to the local resolver and the default port or the SOCKS proxy.

Shawn Nock proved us once more that talking to ISP is key to run Tor relays on high-speed links. Shawn’s exit node was [abruptly shut down by its provider](https://lists.torproject.org/pipermail/tor-relays/2014-May/004553.html) on May 15th. After a well-crafted plea explaining why Tor is important, the provider [restored the service](https://lists.torproject.org/pipermail/tor-relays/2014-May/004555.html) on the very same day!

However, dope457 reported that their provider is now giving them [trouble for being the operator of a non-exit relay](https://lists.torproject.org/pipermail/tor-relays/2014-May/004562.html), due to a large amount of traffic on the DNS port (53), which is being used as the ORPort by a [recently-established Tor relay](https://atlas.torproject.org/#details/44EFAF942314F756FC7EA50292D5B383E568A9BD), as [pointed out](https://lists.torproject.org/pipermail/tor-relays/2014-May/004563.html) by Roman Mamedov.

Now that ICANN is “selling” top-level domain names, Anders Andersson [raised concerns](https://lists.torproject.org/pipermail/tor-talk/2014-May/032974.html) about the .onion extension used by Tor. Fortunately, [RFC6761](https://tools.ietf.org/html/rfc6761) defines a process regarding special-use domain names. Last November, Christian Grothoff, Matthias Wachs, Hellekin O. Wolf, and Jacob Appelbaum submitted a [request to reserve several TLDs used in peer-to-peer systems](https://tools.ietf.org/html/draft-grothoff-iesg-special-use-p2p-names-02). Hellekin [sent an update](https://lists.torproject.org/pipermail/tor-talk/2014-May/032983.html) about the procedure: “the current status quo from the IETF so far is that this issue is not a priority”.

Tor help desk roundup
=====================

Local antivirus or firewall applications can prevent Tor from connecting unless they are disabled. Firewall tools that have caused usability issues in the past include Webroot SecureAnywhere AV, Kaspersky Internet Security 2012, Sophos Antivirus for Mac, and Microsoft Security Essentials.

News from Tor StackExchange
===========================

The [Tor StackExchange site](https://tor.stackexchange.com/) now provides more than 1000 answers to user-supplied questions. However, there are still [\~130 questions](https://tor.stackexchange.com/unanswered) which need a good answer, so if you happen to know one then please visit the site and help out.

The majority of the questions are about the [Tor Browser Bundle](https://tor.stackexchange.com/questions/tagged/tor-browser-bundle), but [hidden services](https://tor.stackexchange.com/questions/tagged/hidden-services) also attract a large amount of attention. When it comes to operating systems, there are [42 Windows-related questions](https://tor.stackexchange.com/questions/tagged/windows), while [questions about Tails](https://tor.stackexchange.com/questions/tagged/tails) and [Whonix](https://tor.stackexchange.com/questions/tagged/whonix) number nearly 50. All your questions about Tor and related software are welcome.

Blue\_Pyro uses Orweb on a mobile phone and [wants to save images from websites](https://tor.stackexchange.com/q/1753/88). Abel of Guardian recommended two options: first, a user can use [Firefox mobile with privacy enhanced options](https://guardianproject.info/apps/firefoxprivacy/), or one can [try Orfox](https://guardianproject.info/builds/Orfox/latest/), a development version of a Firefox-based browser.

Easy development tasks to get involved with
===========================================

[Stem](https://stem.torproject.org/) is a Python controller library for Tor. It comes with tutorials and generally has pretty good test coverage. The newly-added example scripts, however, don’t yet have unit tests. Damian Johnson suggested ways to [add unit tests for example scripts](https://trac.torproject.org/projects/tor/ticket/11335); if you want to help out, [learn how to get started](https://gitweb.torproject.org/stem.git), start writing unit tests for the example scripts, and then comment on the ticket.

The traffic obfuscator [obfsproxy](https://www.torproject.org/projects/obfsproxy.html) should [validate command-line arguments appropriately](https://trac.torproject.org/projects/tor/ticket/9823). Right now, it’s printing an error and continuing, but it should really abort. This sounds like a trivial change, but maybe there’s more to fix in the nearby code. If you like Python and want to give it a try, there’s more information for you on the ticket.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, Karsten Loesing, qbi, and Georg Koppen.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
