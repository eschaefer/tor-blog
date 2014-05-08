---
layout: post
title: "Summer Conclusion (ARM Project)"
permalink: summer-conclusion-arm-project
date: 09/07/2009
author: atagar
category: blog
tags: ["arm", "atagar", "gsoc"]
---

Throughout the summer I've been working on a project called 'arm' (which stands for the 'anonymizing relay monitor'). It's a real-time, terminal monitor for Tor relays providing bandwidth/cpu/memory usage, relay configuration, event log, connections, and other details relay operators might find handy for checking Tor's status. The project's intended for command-line aficionados, ssh connections, and anyone stuck with a tty terminal.

Source, screen shots, and a development log are available on the [project's page](http://www.atagar.com/arm) and an interview by Brenno Winter discussing the project is available [here](http://www.atagar.com/arm/HFM_INT_0001.mp3).

The summer started with [an application](http://www.atagar.com/misc/gsocBlog09/) to [GSoC 2009](http://socghop.appspot.com/). Though it wasn't accepted, in retrospect I wouldn't change a thing since looking for alternative ideas eventually led me to [a thread by Jacob and Karsten from 2008](http://archives.seul.org/or/dev/Jan-2008/msg00005.html) proposing a terminal relay monitor. Coding it has been a fantastic experience, providing the opportunity to dabble in a couple areas that are utterly new to me.

First, all my past experience with Python came from writing small scripts. However, what Jacob had termed a "weekend project" has grown to over 3,000 lines, with all the design and refactoring goodness that comes along with it. In particular this meant learning in intimate detail just how "curses" earned its name and writing wrappers to make up for its shortcomings.

Second, this was my first time working with an active, established open source community. While development was still mostly hacking out code amid Voodoo Daddy swing, having a community to bounce ideas off of and provide feedback made the work vastly more interesting and worthwhile. It was also my first experiences with anonymity systems and I'd \*highly\* suggest the PETS conference to any future students interested in the field.

Barring the occasional bug fix or feature request the arm project is pretty well done so I'm next off to the dreaded task of job hunting. Though I'll need to pull back the time I contribute to Tor, I'm still hoping to stay active in the community. Thanks for the excellent summer - cheers! -Damian

