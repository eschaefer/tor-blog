---
layout: post
title: "New Python/Django-based TorStatus"
permalink: new-pythondjango-based-torstatus
date: 2011-08-29 03:02:33
author: karsten
category: blog
status: closed
tags: ["django", "get involved", "python", "relay information", "tor network", "tor status", "wesleyan hfoss"]
---

We're excited to announce that a group of students from Wesleyan has created a new [TorStatus](http://www.torstatusbeta.org/) website written in Python. Their new website is a fine addition to Kasimir Gabert's [Tor Network Status](http://torstatus.blutmagie.de/) page. Kasimir's page is currently the most popular website to learn about running Tor relays.

We're glad that we now have a new Python/Django-based TorStatus, as many developers in the Tor community have been working on complementary Tor Python libraries.

The new TorStatus started out as a rewrite of the old PHP-based TorStatus, so we're building from Kasimir's great ideas. The new TorStatus adds a new landing page, paged results that decrease latency, and carefully crafted graphs with a focus on aesthetics. But it's not only the features that make this code so great. We believe that many more developers will be interested in modifying and extending the codebase! At least that's much simpler now with the move to Python/Django.

The new TorStatus project was done by [Norman Danner](http://ndanner.web.wesleyan.edu/)'s students during their summer [The Humanitarian Free and Open Source Software at Wesleyan University](http://hfoss.wesleyan.edu/summer-institute-2011) course. Thanks to Jeremy, Diego, and Vlad for designing, coding, and testing this new TorStatus! Thanks to Damian for co-mentoring the students on Tor's side.

What's next? Want to help out with coding on the new TorStatus? You should start by looking at the [codebase](https://gitweb.torproject.org/torstatus.git) and the list of open [tickets](https://trac.torproject.org/projects/tor/query?component=TorStatus&status=!closed). Feel free to leave a comment here or drop by [\#tor-dev](irc://irc.oftc.net/tor) if you have suggestions or are interested in helping out!
