---
layout: post
title: "Tor Weekly News — November 6th, 2013"
permalink: tor-weekly-news-%E2%80%94-november-6th-2013
date: 2013-11-06
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the nineteenth issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/tor-news) that covers what is happening in the up-to-date Tor community.

# Tails 0.21 is out

The [Tails developers anounced the 34th release](https://tails.boum.org/news/version_0.21/) of the live system based on Debian and Tor that preserves the privacy and anonymity of its users.

The new version fixes two holes that gave too much power to the POSIX user running the desktop: Tor control port cannot be directly accessed anymore to disallow configuration changes and IP address retrieval, and the persistence settings now requires privileged access. On top of these specific changes, the release include [security fixes](https://tails.boum.org/security/Numerous_security_holes_in_0.20.1/) from the Firefox 17.0.10esr release and for a few other Debian packages.

More visible improvements include the ability to persist printer settings, support for running from more SD card reader types, and a panel launcher for the password manager. For the curious, more details can be found in the [full changelog](https://git-tails.immerda.ch/tails/plain/debian/changelog).

As with every releases: be sure to upgrade!

# New Tor Browser Bundles based on Firefox 17.0.10esr

Erinn Clark released [new versions of the Tor Browser Bundle](https://blog.torproject.org/blog/new-tor-browser-bundles-firefox-17010esr) on November 1st. The previously “beta” bundles have moved to the “release candidate” stage and are almost identical to the stable ones, except for the version of the tor daemon. A couple of days later, David Fifield also released [updated “pluggable transport“ bundles](https://blog.torproject.org/blog/pluggable-transports-bundles-2417-rc-1-pt1-firefox-17010esr).

The new bundles include all [security fixes from Firefox 17.0.10esr](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox17.0.10), and updated versions of libpng, NoScript and HTTPS Everywhere. It also contains a handful of improvements and fixes to the Tor Browser patches.

Users of older version of the Tor Browser bundles should already have been reminded to upgrade by the notification system. Don't forget about it!

This should be the last bundles based on the 17 branch of Firefox as it is going to be superseded by the 24 branch as the new long-term supported version in 6 weeks. Major progress has already been made by Mike Perry and Pearl Crescent to [update the Tor Browser changes and review the new code base](https://trac.torproject.org/projects/tor/query?keywords=~ff24-esr).

# Monthly status reports for October 2013

The wave of regular monthly reports from Tor project members for the  
month of October has begun early this time to reach the tor-reports  
mailing-list: [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2013-October/000367.html), [Linus Nordberg](https://lists.torproject.org/pipermail/tor-reports/2013-October/000369.html), [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2013-October/000370.html), [Philipp Winter](https://lists.torproject.org/pipermail/tor-reports/2013-November/000371.html), [Ximin Luo](https://lists.torproject.org/pipermail/tor-reports/2013-November/000372.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2012-November/000373.html), [Kelley Misata](https://lists.torproject.org/pipermail/tor-reports/2013-November/000374.html), [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2013-November/000375.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2013-November/000376.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2013-November/000377.html), [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2013-November/000378.html), [George Kadianakis](https://lists.torproject.org/pipermail/tor-reports/2013-November/000379.html), [Colin Childs](https://lists.torproject.org/pipermail/tor-reports/2013-November/000380.html), [Arlo Breault](https://lists.torproject.org/pipermail/tor-reports/2013-November/000381.html), and [Sukhbir Singh](https://lists.torproject.org/pipermail/tor-reports/2013-November/000382.html).

# Tor Help Desk Roundup

One person asked why the lock icon on the Tor Project's website was not outlined in green. Sites that use HTTPS can purchase different types of SSL certificates. Some certificate issuers offer certificates that supply ownership information, such as the physical address of the website operator, for a higher price. Sites that use these certificates get the lock icon by their URL outlined in green. The Tor Project adds protection to the validity of our SSL certificate a different way, by supplying our [SSL certificate fingerprint on our FAQ page](https://www.torproject.org/docs/faq.html#SSLcertfingerprint). You can double check that fingerprint on any of the [Tor Project's mirror pages](https://torproject.org/getinvolved/mirrors.html) as well.

One person wanted to known why a website they were visiting over Firefox was telling them that they were not using Tor, even though Vidalia told them that Tor was running. By default, the Tor Browser Bundle does not anonymize all the traffic on your computer. Only the traffic you send through the Tor Browser Bundle will be anonymized. If you have Firefox and the Tor Browser open at the same time, the traffic you send through Firefox will not be anonymous. Using Firefox and Tor Browser Bundle at the same time is not a great idea because the two interfaces are almost identical, and it is easy to get the two browsers mixed up, even if you know what you are doing.

# Miscellaneous news

The [third beta release of TorBirdy has been released](https://blog.torproject.org/blog/torbirdy-012-our-third-beta-release) as version 0.1.2. Among several other fixes and improvements it restores proper usage of Tor when used with Thunderbird 24. Be sure to [upgrade](https://www.torproject.org/dist/torbirdy/torbirdy-0.1.2.xpi)!

starlight [reported](https://lists.torproject.org/pipermail/tor-relays/2013-October/003187.html) on running a Tor relays with the daemon compiled with the AddressSanitizer memory error detector available since GCC 4.8.

Isis Lovecruft [has sent two proposals](https://lists.torproject.org/pipermail/tor-dev/2013-November/005713.html) for improvements to BridgeDB. One is finished and addresses the switch to a “Distributed Database System and RDBMS”. The second is still in draft stage and “specifies a system for social distribution of the centrally-stored bridges within BridgeDB”.

Karsten Loesing [announced](https://lists.torproject.org/pipermail/tor-dev/2013-October/005700.html) the availability of a new tech report he wrote with Steven J. Murdoch, and Rob Jansen: [Evaluation of a libutp-based Tor Datagram Implementation](https://research.torproject.org/techreports/libutp-2013-10-30.pdf). Be sure to have a look if you are interested in one of the “promising approach to overcome Tor’s performance-related problems”.

SiNA Rabbani [has been asking](https://lists.torproject.org/pipermail/tor-dev/2013-October/005703.html) for comments on two documents he wrote about how use cases and design of a “point-and-click” hidden service blogging tool, as part of the [Cute Otter project](https://trac.torproject.org/projects/tor/attachment/wiki/org/sponsors/Otter/Cute).

David Goulet [released third rc of Torsocks 2.0.0](https://lists.torproject.org/pipermail/tor-dev/2013-November/005728.html) with a lot of fixes and improvements. Available to download from GitHub and also as Debian [package from the experimental distribution](http://packages.debian.org/experimental/torsocks).

Christian is working on a [new round of improvements for Globe](https://lists.torproject.org/pipermail/tor-dev/2013-November/005725.html), a web application to learn about relays and bridges of the Tor network. The project seems close to be mature enough to replace Atlas [according to some](https://lists.torproject.org/pipermail/tor-dev/2013-November/005735.html).

A discussion on the tor-relays mailing list prompted Roger Dingledine to ask about [changing the current default exit policy](https://lists.torproject.org/pipermail/tor-relays/2013-November/003240.html) of the tor daemon. The current “restricted exit node” policy has been in place since 2003. As this has surprised some operators, switching the default policy to “middle node” is under consideration.

* * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, Matt Pagan, and Philipp Winter.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

