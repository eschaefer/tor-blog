---
layout: post
title: "VisiTor - or: a script to tell you how many of your users are probably Tor users"
permalink: blog/visitor-or-script-tell-you-how-many-your-users-are-probably-tor-users
date: 2010-10-04
author: karsten
category: blog
tags: ["metrics apache"]
---

We have heard from web server operators who are wondering how many of
their visitors are using Tor to do so.

We can now answer this question. We have an exit list archive back to
February 2010 and a tool to compare an Apache HTTP server log to these
lists. We can further guess how many of the requests come from Torbutton
users by looking at the user-agent string.

There's a lot of sensitive data involved here, which is why we give out
the archived exit lists and our tool so that web server operators can
run the comparison themselves.

You'll find the exit list archive and the VisiTor tool here:

- [https://metrics.torproject.org/data.html#exitlist](https://metrics.torproject.org/data.html#exitlist "https://metrics.torproject.org/data.html#exitlist")
- [https://metrics.torproject.org/tools.html#visitor](https://metrics.torproject.org/tools.html#visitor "https://metrics.torproject.org/tools.html#visitor")

If you are running a web server and want to help us make the tool
better, please download the sources, review the 350 lines of finest
Java code, run the tool on your machine, and let us know how that works!

(There will be a Python version once we're happy with the Java version.
Want to help writing (and maintaining) a Python version?)

