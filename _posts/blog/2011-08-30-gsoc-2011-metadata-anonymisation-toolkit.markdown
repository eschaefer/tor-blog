---
layout: post
title: "GSoC 2011: Metadata Anonymisation Toolkit"
permalink: gsoc-2011-metadata-anonymisation-toolkit
date: 2011-08-30
author: jvoisin
category: blog
tags: ["gsoc", "metadata", "privacy", "python"]
---

This is a guest blog from one of our 2011 Google summer of code students, jvoisin.

It's the end of the [GSoC](https://code.google.com/soc/). It was a really nice experience, I learned a lot, met a lot of nice people on irc, and earned some money.

My project was to create a [Metadata Anonymisation Toolkit](https://gitweb.torproject.org/user/jvoisin/mat.git) (MAT), to improve privacy of online file publications. First, I heavily based my code on [hachoir](https://bitbucket.org/haypo/hachoir/wiki/Home) (a nice, but a slightly complex library), but now, must of the formats that the MAT supports do not use hachoir.  
 Despite several code restructuring and re-factorizations, silly ideas, re-implementations, and re-writing/... the MAT is living !

I made two big mistakes. The first being using python2.7, and [pygobject](https://live.gnome.org/PyGObject). Neither of these were in Debian stable/tails, so I had to rewrite those parts.

MAP consists of a modular API (feel free to add support for other formats !), a command line interface, and a graphic user interface (powered by pygtk).

It was my first "serious" project in python, and I was the first surprised about the ~3000 lines of code I produced. I'm pretty proud of the "pdf processing part", and I'm sad about the setup.py/packaging part (that are the most ugly/dirty/painful things that I ever touched/coded ).

I'm still unhappy with my code/piece of software, so I'll continue to improve it, so expect great work in the future, such as an [exiftool](http://www.sno.phy.queensu.ca/~phil/exiftool/) binding, watermark counter-measures, ..

Thank you mikeperry for being my mentor, thank you google for the amazing GSoC project, thank to every user that gave me feedback (and even more stuff to fix!), and special thanks to haypo, Mc2`, Kiri, intrigeri, bertagaz, Lunar^ and all #tails/#tor-dev !

Hope to see you next year.

