---
layout: post
title: "Tor Weekly News — September 25th, 2013"
permalink: tor-weekly-news-%E2%80%94-september-25th-2013
date: 09/25/2013
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the thirteenth issue of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what's happening in the well-heeled Tor community.

# Reimbursement of exit operators

In July 2012, Roger Dingledine wrote [a post on the Tor blog](https://blog.torproject.org/blog/turning-funding-more-exit-relays) in which he raised the prospect of offering funding to organizations running fast Tor exit nodes. In so doing, Roger wrote, “we will improve the network's diversity as well as being able to handle more users.” He also announced that donors were already interested in financing such a scheme. Then, in April this year, Moritz Bartl [stated](https://lists.torproject.org/pipermail/tor-relays/2013-April/001996.html) that torservers.net was looking to move away from establishing additional exit nodes, in favor of providing support of various kinds to partner organizations running their own exits.

These plans, and the discussion they provoked, are now about to bear fruit in the form of a financial reimbursement scheme directed at torservers.net's partner organizations. Moritz [wrote again](https://lists.torproject.org/pipermail/tor-relays/2013-September/002824.html) on the the tor-relays list to announce that reimbursements are scheduled to begin at the end of this month, drawn from a one-time donation by the U.S. Government's Broadcasting Board of Governors.

The ensuing debate focused both on the technical aspects of reimbursement — that is, how best to [determine the division of funds based on information harvested from the network metrics](https://lists.torproject.org/pipermail/tor-relays/2013-September/002825.html) — and the question of the [security issues that could potentially arise from such a scheme](https://lists.torproject.org/pipermail/tor-relays/2013-September/002831.html).

Moritz specified that currently the only organizations to qualify for reimbursements are those that he personally knows: “so, if you’re interested in becoming a partner, start social interaction with me”, he wrote. Questions or comments regarding these proposals are welcome on the tor-relays list, and further announcements and discussion about the reimbursement system will be published on its [dedicated mailing lists](https://lists.torproject.org/pipermail/tor-relays/2013-May/002138.html).

# Tails 0.20.1 is out

Tails saw its [33<sup>rd</sup> release](https://tails.boum.org/news/version_0.20.1/) on September 19th. The most visible change might be the upgrade of tor to version 0.2.4.17-rc, which should result in faster and more reliable access to the network after the [sudden bump in Tor clients](https://blog.torproject.org/blog/how-to-handle-millions-new-tor-clients).

Among other minor bugfixes and improvements, persistence volumes are now properly unmounted on shutdown. This should prevent data loss in some situations, and avoid a sometimes lengthy pause upon activation.

It also fixes [several important security issues](https://tails.boum.org/security/Numerous_security_holes_in_0.20/). It is recommended that [all users upgrade as soon as possible](https://tails.boum.org/news/version_0.20.1/).

# New Tor Browser Bundles released

A [new set of stable and beta Tor Browser Bundles was released](https://blog.torproject.org/blog/new-tor-browser-bundles-firefox-1709esr) on September 20th. The Tor Browser is now based on Firefox 17.0.9esr and fixes [several important security issues](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html#firefox17.0.9).

Queries for the default search engine, Startpage, are no longer subject to its [invasive “family filter”](https://bugs.torproject.org/8839). The beta branch also include an updated version of HTTPS Everywhere that no longer causes a storm of requests to clients1.google.com, an [issue](https://bugs.torproject.org/9713) reported by many users after the last release.

Once again, it is recommended that all users upgrade as soon as possible.

# Tor mini-hackathon at GNU 30th Anniversary Celebration

Nick Mathewson [sent an invitation](https://lists.torproject.org/pipermail/tor-talk/2013-September/030154.html) encouraging everyone to attend the [GNU 30th Anniversary Celebration](https://gnu.org/gnu30/celebration) on September 28th and 29th at MIT, Cambridge, MA, USA. Part of the event is a hackathon, and Tor is featured alongside a few other projects. If you want to spend some of the weekend helping the Tor community, [sign up on the webpage](https://crm.fsf.org/civicrm/event/register?id=10) and come along!

# Clock skew: false alarm

Small offsets in system time offer an attractive opportunity for fingerprinting Tor clients. In order to eliminate unnecessary exposure, Nick Mathewson has been working on [proposal 222](https://gitweb.torproject.org/torspec.git/blob_plain/refs/heads/master:/proposals/222-remove-client-timestamps.txt).

Unfortunately, this process introduced a bug into the tor daemon which became apparent after the directory authority named “turtles” was upgraded. The result was that relays started to [warn their operators](https://lists.torproject.org/pipermail/tor-relays/2013-September/002888.html) of an implausible clock skew. This was, of course, a false alarm.

The issue was quickly worked around, and [fixed properly](https://bugs.torproject.org/9798) a few hours later.

# Tor Help Desk Roundup

One user contacted the help desk for assistance running _torbrowser_, an application not affiliated with the Tor Project that attempts to mimic the Tor Browser Bundle. The _torbrowser_ application violates the Tor Project’s trademark, and the Tor Project encourages users to avoid it. Multiple Tor Project developers have contacted SourceForge, which hosts this application’s website, attempting to get the project removed. Andrew Lewman [has said that lawyers have now been engaged](https://lists.torproject.org/pipermail/tor-talk/2013-August/029614.html).

A number of University students continued to contact the help desk to report difficulties circumventing their University’s Cyberoam firewall. These students report being unable to access the Tor network even when using the Pluggable Transports Browser with obfs3 bridges. One person reported success circumventing the firewall when using an obfsproxy bridge on port 443. This issue is ongoing, but a [bug report has been filed](https://bugs.torproject.org/9601).

# Miscellaneous news

Jacob Appelbaum [inquired with VUPEN](http://storify.com/fredericjacobs/discussion-between-tor-s-ioerror-and-vupen-s-chaou) about the Tor Project having the right of first refusal for Tor Browser bugs, in order to protect users.

The [proposed Tor page on Stack Exchange](http://area51.stackexchange.com/proposals/56447/tor) has now reached 100% commitment, and will soon be launching as a live beta. Thanks to everyone who signed up!.

sajolida [reported on the latest Tails “low-hanging fruits session”](https://mailman.boum.org/pipermail/tails-dev/2013-September/003703.html). The [date and a tentative agenda](https://mailman.boum.org/pipermail/tails-dev/2013-September/003696.html) for the next online contributors meeting have also been set.

As GSoC entered its final phase, Kostas Jakeliunas reported on the [searchable metrics archive](https://lists.torproject.org/pipermail/tor-dev/2013-September/005483.html), Johannes Fürmann on [EvilGenius](https://lists.torproject.org/pipermail/tor-dev/2013-September/005484.html), and Cristian-Matei Toader on [Tor capabilities](https://lists.torproject.org/pipermail/tor-dev/2013-September/005490.html).

How can we provide Tor users an easy way to verify the signatures on Tor software? Sherief Alaa raised this question on the tor-dev mailing list when [asking for comments](https://lists.torproject.org/pipermail/tor-dev/2013-September/005491.html) on plans to write a “small” GUI tool.

* * *

This issue of Tor Weekly News has been assembled by harmony, Lunar, dope457, Matt Pagan, and Jacob Appelbaum.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

