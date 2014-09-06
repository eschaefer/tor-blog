---
layout: post
title: "Polipo Portability Enhancements Summary"
permalink: blog/polipo-portability-enhancements-summary
date: 2009-09-12
author: chrisd
category: blog
tags: ["gsoc 2009", "libevent", "polipo"]
---

Over the summer for GSoC 2009, I worked on Polipo, Tor's favored Web proxy for bridging the gap between HTTP and SOCKS protocols. The proxy also provides an efficient memory cache to help speed up browsing. I had an opportunity to learn about Polipo and Libevent, and I had a chance to attend [PETS](http://petsymposium.org/2009/), a privacy conference, and meet some of the Tor folks in person. [Polipo](http://www.pps.jussieu.fr/~jch/software/polipo/) is authored by Juliusz Chroboczek. [Libevent](http://www.monkey.org/~provos/libevent/) is developed by Nick Mathewson and Niels Provos. Nick Mathewson also happens to work for the Tor Project and was my GSoC mentor over the summer.

My work included integrating support for Libevent, a library for managing I/O events portably. The main advantage of using Libevent over Polipo's built-in event loop is Libevent's support of platform-specific APIs for monitoring large numbers of connections for I/O events. Polipo, when compiled to use Libevent, should be quicker when juggling many open connections. Informal benchmarking seemed to back this up, although more thorough profiling is still TODO. Modern versions of Libevent also contain an asynchronous DNS resolver, which I tied into Polipo, as well. Polipo's original event system and asynchronous DNS resolver are still available in case Libevent is unavailable on a user's system.

I also did some work to get Polipo to run better on Windows. I got a start fixing the disk cache and path name handling, Windows socket errors should now be printed correctly, and SIGINT and SIGBREAK signals are handled to cleanly quit when the user hits Ctrl-C or closes the DOS box. Also, Libevent's DNS resolver supports fetching name servers from the Windows registry, so Polipo no longer should block when performing lookups when it is compiled with Libevent support. More work remains to refine Windows support, but I hope this is a good start.

The main thing that I left undone during GSoC is the controller GUI for launching and managing Polipo on Windows and providing status information to the user. The exact design of the GUI is still up for discussion, but it shouldn't take too much time to develop once something is settled on. I'm currently working on modifications to Polipo's configurator to support the controller, and this is going pretty smoothly.

Looking farther ahead, it would be good to consider a few ways to improve Polipo's performance. Roger mentioned to me during PETS that retrieving web pages might be made more efficient by packing client requests into Tor's RELAY BEGIN cells, so that the requests can be sent by the exit node immediately after connection to the requested server without the additional latency that currently exists while the client waits for notice of a successful connection. This would require changes to Polipo and Tor to implement, and there may be design issues worth considering, such as the limited payload space available in cells. Another thing that could potentially increase performance is adding support for Libevent's buffer events, which make use of more efficient I/O routines on Windows. This would be pretty difficult to do, yet worth considering.

Working on this project was a fun and informative experience, and I hope to stay a member of the Tor community. I've had some experience working on open source projects before, but it's unique to find developers as dedicated as those working on Tor. In fact, Tor is a full-time job for several of the developers, and I think seeing a high level of development activity helps to keep volunteers around.

