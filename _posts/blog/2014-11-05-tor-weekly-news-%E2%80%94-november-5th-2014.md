---
layout: post
title: "Tor Weekly News — November 5th, 2014"
permalink: tor-weekly-news-—-november-5th-2014
date: 2014-11-05 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the forty-fourth issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Tor 0.2.6.1-alpha is out
========================

Following last week’s stabilization of Tor 0.2.5.x, Nick Mathewson [announced](https://lists.torproject.org/pipermail/tor-talk/2014-October/035390.html) the first alpha release in the Tor 0.2.6.x series. Quoting the changelog, this version “includes numerous code cleanups and new tests, and fixes a large number of annoying bugs. Out-of-memory conditions are handled better than in 0.2.5, pluggable transports have improved proxy support, and clients now use optimistic data for contacting hidden services.” Support for some very old compilers that do not understand the C99 programming standard, systems without threading support, and the Windows CE operating system has also been dropped.

“This is the first alpha release in a new series, so expect there to be bugs.” If you want to test it out, you can find the source code in the [distribution directory](https://dist.torproject.org/).

Tor Browser 4.0.1 is out
========================

Mike Perry [announced](https://blog.torproject.org/blog/tor-browser-401-released) a bugfix release by the Tor Browser team. This version disables [DirectShow](https://en.wikipedia.org/wiki/DirectShow), which was causing the Windows build of Tor Browser to [crash](https://bugs.torproject.org/13443) when visiting many websites. This is not a security release, but Windows users who have experienced this issue should upgrade.

Please see Mike’s post for the changelog, and download your copy from the [project page](https://www.torproject.org/projects/torbrowser.html).

Facebook, hidden services, and HTTPS certificates
=================================================

Facebook, one of the world’s most popular websites, [surprised the Internet](https://www.facebook.com/notes/protect-the-graph/making-connections-to-facebook-more-secure/1526085754298237) by becoming the most prominent group so far to set up a Tor hidden service. Rather than connecting through an exit relay, Facebook users can now interact with the social network without their traffic leaving the Tor network at all until it reaches its destination.

Soon after the service was announced, some in the Tor community expressed concern over the implications of its [unusually memorable .onion address](https://lists.torproject.org/pipermail/tor-talk/2014-October/035403.html). Had Facebook somehow mustered the computing power to brute-force hidden service keys at will? Alec Muffett, one of the lead engineers behind the project, [clarified](https://lists.torproject.org/pipermail/tor-talk/2014-October/035413.html) that in fact “we just did the same thing as everyone else: generated a bunch of keys with a fixed lead prefix (‘facebook’) and then went fishing looking for good ones”, getting “tremendous lucky” in the process. Those concerned by how easy this seems, [added](https://lists.torproject.org/pipermail/tor-talk/2014-October/035416.html) Nick Mathewson, “might want to jump in on reviewing and improving [proposal 224](https://gitweb.torproject.org/torspec.git/blob_plain/HEAD:/proposals/224-rend-spec-ng.txt), which includes a brand-new, even less usable, but far more secure, name format”.

“Why would you want to use Facebook over Tor?” remains a frequently-asked (and -misunderstood) question, so Roger Dingledine took to the [Tor blog](https://blog.torproject.org/blog/facebook-hidden-services-and-https-certs) to address this and related issues. “The key point here is that anonymity isn’t just about hiding from your destination. There’s no reason to let your ISP know when or whether you’re visiting Facebook. There’s no reason for Facebook’s upstream ISP, or some agency that surveils the Internet, to learn when and whether you use Facebook. And if you do choose to tell Facebook something about you, there’s still no reason to let them automatically discover what city you’re in today while you do it.” Not only that, but Facebook is now taking advantage of the special security properties that hidden services provide, including strong authentication (letting users be confident that they are talking to the right server, and not to an impostor) and end-to-end encryption of their data.

This last point generated some confusion, since Facebook have also acquired an HTTPS certificate for their hidden service, which might seem like an unnecessary belt-and-suspenders approach to security. This has been the subject of “feisty discussions” in the Internet security community, with many points for and against: on the one hand, users have been taught that “https is necessary and http is scary, so it makes sense that users want to see the string “https” in front of” URLs, while on the other, “by encouraging people to pay Digicert we’re reinforcing the certificate authority business model when maybe we should be continuing to demonstrate an alternative.”

Please see Roger’s post for a fuller discussion of all these points and more, and feel free to contribute your own thoughts on the [tor-talk mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-talk). If you experience problems with the service, please contact Facebook support rather than the Tor help desk; as Alec wrote in the announcement, “we expect the service to be of an evolutionary and slightly flaky nature”, as it is an “experiment” — hopefully an experiment that will, as Roger suggested, “help to continue opening people’s minds about why they might want to offer a hidden service, and help other people think of further novel uses for hidden services.”

Monthly status reports for October 2014
=======================================

The wave of regular monthly reports from Tor project members for the month of October has begun. [Juha Nurmi](https://lists.torproject.org/pipermail/tor-reports/2014-October/000677.html) released his report first, followed by reports from [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2014-October/000678.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-October/000679.html), [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2014-October/000680.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2014-November/000682.html), [Harmony](https://lists.torproject.org/pipermail/tor-reports/2014-November/000683.html), [Sukhbir Singh](https://lists.torproject.org/pipermail/tor-reports/2014-November/000684.html), [Colin C.](https://lists.torproject.org/pipermail/tor-reports/2014-November/000685.html), [Leiah Jansen](https://lists.torproject.org/pipermail/tor-reports/2014-November/000687.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-November/000688.html), [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2014-November/000689.html), [Noel Torres](https://lists.torproject.org/pipermail/tor-reports/2014-November/000690.html), and [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2014-November/000691.html).

Lunar reported on behalf of the [help desk](https://lists.torproject.org/pipermail/tor-reports/2014-November/000681.html), Arturo Filastò for the [OONI team](https://lists.torproject.org/pipermail/tor-reports/2014-November/000686.html), and Mike Perry for the [Tor Browser team](https://lists.torproject.org/pipermail/tor-reports/2014-November/000692.html).

Miscellaneous news
==================

Mike Perry [updated](https://lists.torproject.org/pipermail/tbb-dev/2014-October/000148.html) the [Tor Browser design document](https://www.torproject.org/projects/torbrowser/design/) to cover Tor Browser version 4.0 — “Feedback welcome! Patches are even more welcomer!”

Israel Leiva sent out an [update](https://lists.torproject.org/pipermail/tor-dev/2014-October/007700.html) on the progress of the GetTor redevelopment project.

David Fifield [distributed](https://lists.torproject.org/pipermail/tor-dev/2014-October/007697.html) a [graph](https://people.torproject.org/~dcf/graphs/relays-all.pdf) of “the number of simultaneous relay users for every country, one country per row”.

David also sent out a [summary](https://lists.torproject.org/pipermail/tor-dev/2014-November/007716.html) of the costs incurred by the meek pluggable transport, which have increased significantly following its incorporation into the latest stable Tor Browser and the consequent “explosion” in use.

Esfandiar Mohammadi [announced](https://lists.torproject.org/pipermail/tor-dev/2014-October/007692.html) the [MATor](http://www.infsec.cs.uni-saarland.de/projects/anonymity-guarantees/mator.html) project and accompanying paper. MATor is a tool that “assesses the influence of Tor’s path selection on a user’s anonymity”; “since MATor is an ongoing project, we would appreciate your opinion about the approach in general.”

Tor help desk roundup
=====================

The help desk has been asked if Tor Browser acts as a relay by default. Tor Browser’s Tor by default acts only as a client, and not as a bridge relay, exit relay, or relay. Additionally, this is [unlikely to change](https://www.torproject.org/docs/faq#EverybodyARelay) in the future.

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, Matt Pagan, Karsten Loesing, and Harmony.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
