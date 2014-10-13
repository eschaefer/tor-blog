---
layout: post
title: "Tor Weekly News — September 17th, 2014"
permalink: tor-weekly-news-%E2%80%94-september-17th-2014
date: 2014-09-17
author: harmony
category: blog
tags: ["tor weekly news"]
---

Welcome to the thirty-seventh issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the community around Tor, the anonymity network that makes full use of its library card.

# tor 0.2.5.7-rc is out

Nick Mathewson [announced](https://lists.torproject.org/pipermail/tor-talk/2014-September/034740.html) the first release candidate in tor’s 0.2.5.x series. This version “fixes several regressions from earlier in the 0.2.5.x release series, and some long-standing bugs related to ORPort reachability testing and failure to send CREATE cells”; relay operators running it will also receive a warning if they try to configure a hidden service on the same process as their relay, as the public nature of much information about Tor relays [can help identify services running on the same machine](https://bugs.torproject.org/12908#comment:5). As ever, you can read the full list of improvements and fixes in Nick’s announcement, and download the source code from the Tor Project’s [distribution directory](https://www.torproject.org/dist/).

# Tor protects library patrons’ right to privacy

April Glaser and Alison Macrina [published](http://boingboing.net/2014/09/13/radical-librarianship-how-nin.html) an article for BoingBoing on efforts by Massachusetts librarians to guarantee their patrons’ right to access information without fear of surveillance or censorship. Macrina and her colleagues, in partnership with the ACLU of Massachusetts, have been giving workshops on the use of privacy-preserving technologies to other librarians, and spreading the word about the risk that pervasive surveillance poses to freedom of thought and intellectual inquiry.

As the authors remark, “it’s no secret that libraries are among our most democratic institutions. Libraries provide access to information and protect patrons’ right to explore new ideas, no matter how controversial or subversive […] and protecting unfettered access to information is important whether that research is done using physical books or online search engines. But now it has become common knowledge that governments and corporations are tracking our digital lives, and that surveillance means our right to freely research information is in jeopardy”.

Tor and Tails are a natural fit for any response to this problem, and BoingBoing reports that not only have “multiple Massachusetts libraries […] installed the Tor browser on all of their public PCs” following the workshops, some have even “set up Tor middle relays on their libraries’ networks”.

It would be a shame, however, if these exciting developments were restricted to the state of Massachusetts. If you are a library user concerned about this issue, share the article with your local librarians. If you work in a library, contact the authors of the article at the addresses they provide to find out how you can offer privacy workshops and tools to your own community!

# Hidden service enumeration and how to prevent it

When a Tor user wants to connect to a hidden service, their client makes a request over the Tor network to a relay acting as a “hidden service directory”, or HSDir. In return, the client receives a hidden service “descriptor” containing the information necessary for a connection to be made, including the set of [Introduction Points](https://www.torproject.org/docs/hidden-services) that the hidden service is currently using.

Hidden services would ideally not be discoverable unless the address is public or has been shared directly, but one of the weaknesses of the current protocol is that hidden service directories know which services they are serving descriptors for; this same shortcoming was an element of the [“RELAY\_EARLY” traffic confirmation attack](https://blog.torproject.org/blog/tor-security-advisory-relay-early-traffic-confirmation-attack) discovered in July. Although the full set of descriptors is not published to all directories at once — at any given time, [six directories](https://gitweb.torproject.org/torspec.git/blob/HEAD:/rend-spec.txt#l496) are responsible for a service’s descriptor — the list is rotated frequently, so it would not be hard for an adversary to run a relay stable enough to gain the HSDir flag, and harvest hidden service addresses as they are uploaded to it in turn.

Fabio Pietrosanti [informed](https://lists.torproject.org/pipermail/tor-talk/2014-September/034751.html) the tor-talk mailing list of an experiment designed to detect this enumeration of hidden services: he set up thirty new hidden services, keeping their addresses secret, with each service running a script to report any attempts at access from outside. As the existence of these services was not disclosed to anyone, any requests to the service could only come from a client that had obtained the address from a directory which had previously held the descriptor, possibly “a malicious Tor relay acting as a TorHS directory, with Tor’s code modified to dump from the RAM memory the TorHS list, then harvest them with an http client/script/crawler”. After approximately a month, according to Fabio’s message, a client did indeed try to access one of the “honeypot” services.

Regular readers of Tor Weekly News will [know](https://lists.torproject.org/pipermail/tor-news/2013-December/000023.html) that the hidden service protocol is being fully redesigned, and this “next-generation” proposal already suggests [defenses against this kind of attack](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/224-rend-spec-ng.txt#l571), but (as ever) more eyes are needed. If you’re interested, see George Kadianakis’ introduction to the [issues facing hidden services](https://blog.torproject.org/blog/hidden-services-need-some-love); those familiar with cryptography in C are welcome to review the discussion of this particular issue on the [bug tracker](https://bugs.torproject.org/8106).

# Miscellaneous news

Nathan Freitas [announced](https://lists.mayfirst.org/pipermail/guardian-dev/2014-September/003773.html) version 14.0.8.1 of Orbot, the Tor client for Android. The highlights of this release are an upgrade to tor 0.2.5.7-rc (see above), which solves an issue with the “airplane mode” feature, as well as a number of improvements to do with transparent proxying. Find the full changelog and download links in Nathan’s message.

Juha Nurmi [described](https://blog.torproject.org/blog/ahmia-search-after-gsoc-development) the current state of ahmia.fi, the search engine for hidden services, following a successful Google Summer of Code project. The post includes notes on the design, content statistics, and plans for future work.

David Fifield called for a volunteer operating a “ [big fast bridge](https://lists.torproject.org/pipermail/tor-dev/2014-September/007482.html)” to take over the running of the [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek) pluggable transport: “I want to do this both to diffuse trust, so that I don’t run all the infrastructure, and because my bridge is not especially fast and I’m not especially adept at performance tuning”.

David also [wondered](https://lists.torproject.org/pipermail/tor-dev/2014-September/007481.html) why the number of FTE users appeared to dip in late August, and explored possible reasons behind the [correlation in usage statistics](https://lists.torproject.org/pipermail/tor-dev/2014-September/007480.html) for meek and Flashproxy, whose backends both run on the same bridge. Karsten Loesing [suggested](https://lists.torproject.org/pipermail/tor-dev/2014-September/007483.html) that the latter was because “we’re counting consensuses downloaded from a bridge via any supported transport, and then we’re attributing those downloads to specific transports based on what fraction of IPs connected per transport”.

Tim [reported](https://lists.torproject.org/pipermail/tor-dev/2014-September/007471.html) on progress made towards a “ [fuzzer](https://en.wikipedia.org/wiki/Fuzz_testing)” for Tor, based on the Tor research framework previously [announced](https://lists.torproject.org/pipermail/tor-dev/2014-July/007232.html) by Gareth Owen, including a draft design for the process and a list of patches against Tor made during development.

Matt Pagan submitted his [status report](https://lists.torproject.org/pipermail/tor-reports/2014-September/000650.html) for August, while Roger Dingledine sent out the report for [SponsorF](https://lists.torproject.org/pipermail/tor-reports/2014-September/000649.html).

Karsten Loesing [posted](https://lists.torproject.org/pipermail/tor-dev/2014-September/007469.html) the minutes of last week’s Globe/Atlas developer IRC meeting.

* * *
This issue of Tor Weekly News has been assembled by harmony, Lunar, Roger Dingledine, George Kadianakis, and special.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

