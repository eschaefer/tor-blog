---
layout: post
title: "Tor, NSA, GCHQ, and QUICK ANT Speculation"
permalink: tor-nsa-gchq-and-quick-ant-speculation
date: 09/11/2013
author: phobos
category: blog
tags: ["gchq", "nsa", "quick ant", "snowden leaks", "speculation", "tor"]
---

Many Tor users and various press organizations are asking about [one slide in a Brazillian TV broadcast](https://people.torproject.org/~andrew/2013-09-10-quick-ant-tor-events-qfd.png). A graduate student in law and computer science at Stanford University, Jonathan Mayer, then [speculated on what this "QUICK ANT" could be](https://twitter.com/jonathanmayer/status/377292928718499841). Since then, we've heard all sorts of theories.

We've seen the same slides as you and Jonathan Mayer have seen. It's not clear what the NSA or GCHQ can or cannot do. It's not clear if they are "cracking" the various crypto used in Tor, or merely tracking Tor exit relays, Tor relays as a whole, or run their own private Tor network.

What we do know is that if someone can watch the entire Internet all at once, they can watch traffic enter tor and exit tor. This likely de-anonymizes the Tor user. We [describe the problem as part of our FAQ](https://www.torproject.org/docs/faq.html.en#AttacksOnOnionRouting).

We think the most likely explanation here is that they have some "Tor flow detector" scripts that let them pick Tor flows out of a set of flows they're looking at. This is basically the same problem as the blocking-resistance problem — they could do it by IP address ("that's a known Tor relay"), or by traffic fingerprint ("that looks like TLS but look here and here how it's different"), etc.

It's unlikely to have anything to do with deanonymizing Tor users, except insofar as they might have traffic flows from both sides of the circuit in their database. However, without concrete details, we can only speculate as well. We'd rather spend our time developing Tor and conducting research to make a better Tor.

Thanks to Roger and Lunar for edits and feedback on this post.

