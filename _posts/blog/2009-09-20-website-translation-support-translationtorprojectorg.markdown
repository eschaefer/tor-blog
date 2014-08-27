---
layout: post
title: "Website translation support for translation.torproject.org"
permalink: website-translation-support-translationtorprojectorg
date: 2009-09-20
author: Runa
category: blog
tags: ["gsoc", "translation", "website"]
---

This summer I was working on a set of scripts that would make it possible to translate the [Tor Project website](https://www.torproject.org/) via [Pootle](http://translate.sourceforge.net/wiki/pootle) on [translation.torproject.org](http://translation.torproject.org). The website is based on a set of .wml files, but Pootle only takes files in the .pot and po format. The goal was to find a solution that would make it easy to not only translate from .wml to .po and back, but enable us to convert and keep the already translated documents.

The solution that I chose was to use the [po4a framework](http://po4a.alioth.debian.org/) in a set of scripts. The first script, [wml2po.sh](https://tor-svn.freehaven.net/svn/website/trunk/wml2po.sh), converts from .wml to .po and adds the correct charset, encoding and copyright holder. The script also checks to see which .po files need to be updated and which don't. The second script, [po2wml.sh](https://tor-svn.freehaven.net/svn/website/trunk/po2wml.sh) writes the translated documents, i.e. converts from .po back to .wml. I also documented the things one would need to know before using the scripts, as well as the process of converting already translated documents. See the [howto](https://tor-svn.freehaven.net/svn/translation/trunk/tools/gsoc09/HOWTO) and the [readme](https://tor-svn.freehaven.net/svn/translation/trunk/tools/gsoc09/README).

The project did not come without its challenges, and it took time before I got on the right track and found a solution that everyone was happy with. I looked at different scripts and SVN hooks before I settled on having two scripts that can be run at any time by anyone. In addition to that, my mentor was travelling a lot and communication was not very frequent. However, I do feel that I learned a lot and, at the same time, the communication with other GSoC students was a great help.

Overall, I'm pleased with how GSoC turned out. I am looking forward to seeing my code be put to use and to start working on other projects for Tor.

