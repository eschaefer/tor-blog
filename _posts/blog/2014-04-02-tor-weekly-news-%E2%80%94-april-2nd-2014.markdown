---
layout: post
title: "Tor Weekly News — April 2nd, 2014"
permalink: tor-weekly-news-%E2%80%94-april-2nd-2014
date: 2014-04-02
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the thirteenth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tor Project website redesign takes two steps forward

Andrew Lewman put out two calls for help with the ongoing Tor Project  
website redesign: [one for the sponsor page](https://lists.torproject.org/pipermail/www-team/2014-March/000238.html), and [another for the download area](https://lists.torproject.org/pipermail/www-team/2014-March/000249.html). Both were immediately met with proposals and design suggestions from the www-team mailing list: Olssy produced [two mock-ups](http://tor.harrytuttle.net/) of the sponsorship page as possible models for further work, while William Papper and Lance Tuller have been [working on a repository](https://github.com/wpapper/tor-download-web) for the download page, with comments from other list members on topics such as the use of Javascript and possible layout decisions.

If you’d like to give the website redesign further momentum, please see the [dedicated project page on the wiki](https://trac.torproject.org/projects/tor/wiki/Website) for open tickets and advice on how to contribute, then come to the [www-team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/www-team) and join in!

# QR codes for bridge addresses

Since most pocket computers (sometimes called “phones”) and laptops began incorporating cameras, [QR codes](https://en.wikipedia.org/wiki/QR_code) have become a ubiquitous way to enter short sequences of data into our devices. URLs are the canonical example, but the process also works for Bitcoin addresses or [OpenPGP fingerprints](http://web.monkeysphere.info/monkeysign/).

Bridges are the standard tool for circumventing filters that prevent access to the Tor network. Users currently enter bridge addresses in Tor by copy/pasting from the [BridgeDB web page](https://bridges.torproject.org/) or auto-responder email. But manually giving IP addresses and fingerprints to Orbot on keyboard-less devices is an error-prone process.

QR codes might be a solution to this problem. They could also enable peer-to-peer exchange among friends, or circumvention strategies involving IPv6 addresses and paper. According to Isis Lovecruft, [adding QR codes to the BridgeDB web interface](https://bugs.torproject.org/11345) would be easy. Would any reader feel like [hacking Orbot](https://bugs.torproject.org/5096) or the [Tor Launcher](https://gitweb.torproject.org/tor-launcher.git) Firefox extension (see relevant [documentation](https://developer.mozilla.org/en-US/docs/WebRTC/taking_webcam_photos) and [API](https://developer.mozilla.org/en-US/docs/Web/API/Navigator.getUserMedia))?

# Client identification in hidden service applications

Applications behind hidden services currently cannot easily differentiate between client connections. Tor will make a different local TCP connection for each connections it receives, but the software is unable to tell if they are coming from the same circuit. Harry SeventyOne [felt](https://lists.torproject.org/pipermail/tor-dev/2014-March/006576.html) the latter would be useful to enable applications for diagnostic log analysis, identifying traffic trends, rate-limiting or temporarily blocking operations coming from the same client.

Harry sent a very rough patch to the Tor development mailing which enables circuit distinction by using a different source IP address from the IPv4 localhost pool (`127.0.0.0/8`) for each circuit. Nick Mathewson [liked the idea](https://lists.torproject.org/pipermail/tor-dev/2014-March/006610.html) and gave several comments about the preliminary patch. Hopefully this work will make the life of hidden service operators easier in the future.

# Monthly status reports for March 2014

The wave of regular monthly reports from Tor project members for the month of March has begun. [Georg Koppen](https://lists.torproject.org/pipermail/tor-reports/2014-March/000487.html) released his report first, followed by reports from [Pearl Crescent](https://lists.torproject.org/pipermail/tor-reports/2014-March/000488.html), [Damian Johnson](https://lists.torproject.org/pipermail/tor-reports/2014-March/000489.html), [Sherief Alaa](https://lists.torproject.org/pipermail/tor-reports/2014-April/000490.html), [Nick Mathewson](https://lists.torproject.org/pipermail/tor-reports/2014-April/000491.html), [Matt Pagan](https://lists.torproject.org/pipermail/tor-reports/2014-April/000492.html), [Lunar](https://lists.torproject.org/pipermail/tor-reports/2014-April/000494.html), and [Karsten Loesing](https://lists.torproject.org/pipermail/tor-reports/2014-April/000495.html).

Lunar also reported [help desk statistics](https://lists.torproject.org/pipermail/tor-reports/2014-April/000493.html).

# Miscellaneous news

An extensive guide to [hacking on Tor Browser](https://trac.torproject.org/projects/tor/wiki/doc/TorBrowser/Hacking) was posted to the Tor Project’s wiki by Mike Perry. Among other things, it covers the browser’s build instructions, design principles and testing procedures, as well as a summary of how browser team members organize and communicate. If you’d like to get involved in Tor Browser development, please take a look!

Nicholas Hopper [followed](https://lists.torproject.org/pipermail/tor-dev/2014-March/006563.html) [up](https://lists.torproject.org/pipermail/tor-dev/2014-March/006575.html) on George Kadianakis’ research on switching to a single guard. He used Aaron Johnson’s TorPS simulator to find out the “typical” bandwidth for a client. The conclusions match George’s: a single guard and a bandwidth cutoff of 2 Mbit/s would improve over the current situation. George subsequently sent an [initial draft proposal](https://lists.torproject.org/pipermail/tor-dev/2014-March/006570.html) to start the formal process.

BridgeDB version 1.6 was [deployed on March 26th](https://gitweb.torproject.org/bridgedb.git/commit/f266f32). Thanks to Isis Lovecruft, users should now be able to [solve the CAPTCHA again](https://bugs.torproject.org/10809). A custom solution is now used instead of Google’s reCAPTCHA services which will give more flexibility in the future.

John Brooks [presented](https://lists.torproject.org/pipermail/tor-talk/2014-March/032476.html) Torsion, “a ready-to-use hidden service instant messaging client”. “I’m looking for people to try it out, validate my ideas and implementation, and help plan the future”, wrote John. You can consult the design documentation and build instructions on [Github](https://github.com/special/torsion); please share your comments with the community!

Martin Weinelt [shared](https://lists.torproject.org/pipermail/tor-relays/2014-March/004168.html) a [plugin](https://github.com/mweinelt/munin-tor) that generates graphs in the [Munin network monitoring tool](http://munin-monitoring.org/) from data provided by Tor, using [Stem](https://stem.torproject.org/). “At the moment it supports a connection graph, getting its data from orconn-status. More graphs are possible, but not yet implemented. Ideas are welcome,” wrote Martin.

Amid the ongoing censorship of internet services in Turkey, there were [reports](https://lists.torproject.org/pipermail/tor-talk/2014-March/032487.html) that the Tor Project’s website was unavailable over connections supplied by some Turkish ISPs. Feel free to try one of the [mirrors](https://www.torproject.org/getinvolved/mirrors.html)!

Karsten Loesing [published](https://lists.torproject.org/pipermail/tor-dev/2014-March/006602.html) a draft of [a guide](http://csxeeumg5ynu2rk7.onion/) to running a blog over a Tor hidden service using the [Jekyll static site generator](http://jekyllrb.com/). “The intended audience are bloggers who can handle a terminal window but who don’t know the typical pitfalls of securely setting up a web server over a hidden service”, he wrote. However, the guide is in its first stages, and “may contain severe problems harming your privacy!” Feedback on its content, wording, and layout would be greatly appreciated.

Yawning Angel [called](https://lists.torproject.org/pipermail/tor-dev/2014-March/006592.html) for help with testing [obfsclient 0.0.2](https://github.com/Yawning/obfsclient/archive/v0.0.2.tar.gz), a C++ implementation of the obfs3 and ScrambleSuit pluggable transports: “This is mostly a bug fix release that addresses issues found in testing/actual use […] Questions, comments, feedback appreciated as always.”

Michael Rogers has been “working on a messaging app that uses Tor hidden services to provide unlinkability (from the point of view of a network observer) between users and their contacts”. But as “users know who their contacts are”, the mutual anonymity provided by hidden services is not a requirement. Michael [asked](https://lists.torproject.org/pipermail/tor-dev/2014-March/006572.html) how hidden services performance could be improved for this use case.

On the Tor Blog, Sukhbir Singh [posted](https://blog.torproject.org/blog/ways-get-tor-browser-bundle) a round-up of the various methods by which users can download and run the Tor Browser, covering download mirrors, GetTor, bridge address distribution, and pluggable transports usage. If you’re having trouble acquiring or using a copy of the Tor Browser, please look here for links and guidance.

Mike Perry [discovered](https://lists.torproject.org/pipermail/tor-talk/2014-March/032503.html) “that the Linux kernel appears to have a leak in how it applies transproxy rules to the TCP CLOSE\_WAIT shutdown condition under certain circumstances”. Be sure to look at Mike’s email if you use Tor’s TransProxy feature. velope later [improved](https://lists.torproject.org/pipermail/tor-talk/2014-March/032507.html) the original mitigating firewall rule.

As part of the ongoing project to rewrite the Tor Weather service, Sreenatha Bhatlapenumarthi and Karsten Loesing [collaborated](https://bugs.torproject.org/9889) to produce a Python script that enables it to determine whether or not relay operators have fulfilled the [requirements](https://www.torproject.org/getinvolved/tshirt) for a free Tor T-shirt.

Lukas Erlacher announced the avaibility of [OnionPy](https://lists.torproject.org/pipermail/tor-dev/2014-March/006603.html), “a Python wrapper for OnionOO with support for transparently caching OnionOO replies in memcached”. It should be useful to the on-going rewrite of the [Tor Weather service](https://weather.torproject.org/).

The deadline for submissions to the Tails logo contest passed on March 31st; you can review all of the proposed designs, from the minimalist to the psychedelic, [on the Tails website](https://tails.boum.org/blueprint/logo/).

# Tor help desk roundup

The help desk often gets confusing reports that after being directed to download the latest Tor Browser version by a flashing TorBrowserButton, users still sometimes see a message that their Tor Browser is out of date. This happens when the new Tor Browser version was installed over the previous one. Fortunately the [underlying bug](https://bugs.torproject.org/11242) will be fixed in the next Tor Browser release. We recommend extracting each Tor Browser update to an empty directory rather than overwriting the old one, to prevent similar unexpected behaviors. The longer-term solution for issues like this is an [auto-updating](https://bugs.torproject.org/4234) Tor Browser.

# News from Tor StackExchange

saurav wanted to know the total bandwidth of all guard nodes in the [current network](https://tor.stackexchange.com/q/1824/88). gacar pointed to the [bandwidth.csv file](https://metrics.torproject.org/stats/bandwidth.csv) and explained the format of the file.

Tor’s StackExchange site is doing a [self-evaluation](https://tor.stackexchange.com/review/site-eval). If you have an account, please log in and evaluate the questions as well as their answers. It helps to improve the answers and the site in general.

Furthermore, if you happen to visit the site, check the list of [unanswered questions](https://tor.stackexchange.com/unanswered). If you know an answer, please share your knowledge with the people.

* * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, David Fifield, Matt Pagan, qbi and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report  
important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

