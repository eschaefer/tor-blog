---
layout: post
title: "April 2008 Progress Report"
permalink: blog/april-2008-progress-report
date: 2008-05-14
author: phobos
category: blog
tags: ["progress report", "release candidate", "torbrowser", "torbutton", "translation"]
---

Tor 0.2.0.24-rc (released Apr 22) adds dizum (run by Alex de Joode)
as the new sixth v3 directory authority, makes relays with dynamic IP
addresses and no DirPort notice more quickly when their IP address
changes, fixes a few rare crashes and memory leaks, and fixes a few
other miscellaneous bugs. Tor 0.2.0.25-rc (released Apr 23) makes Tor
work again on OS X and certain BSDs.
 [http://archives.seul.org/or/talk/May-2008/msg00014.html](http://archives.seul.org/or/talk/May-2008/msg00014.html "http://archives.seul.org/or/talk/May-2008/msg00014.html")

Torbutton 1.1.18 (released Apr 17) fixes many usability and interoperability
items, in an attempt to make the new Torbutton not so obnoxious in its
zeal to protect the user. It also includes new translations for French,
Russian, Farsi, Italian, and Spanish.

We did a complete overhaul of the [https://check.torproject.org/](https://check.torproject.org/ "https://check.torproject.org/")
page. Now it accepts a language choice,
e.g. [https://check.torproject.org/?lang=fa-IR](https://check.torproject.org/?lang=fa-IR "https://check.torproject.org/?lang=fa-IR")
Available languages are German, English, Spanish, Italian, Farsi,
Japanese, Polish, Portugese, Russian, and Chinese. The Tor Browser
Bundle automatically uses the appropriate language as its home page,
based on which language of the Browser Bundle was downloaded.

Started on a documentation page to explain to users what bridges are,
how they can decide whether they need one, and how to configure their
Tor client to use them:
 [https://www.torproject.org/bridges.html](https://www.torproject.org/bridges.html "https://www.torproject.org/bridges.html")

We've also started working on a design proposal for making it easier
to set up a private or testing Tor network. With the advent of the v3
directory protocol, it currently takes up to 30 minutes before a test
network will produce a useful networkstatus consensus. Also, there are
a dozen different config options that need to be set correctly for
a Tor network running on a single IP address to not trigger various
security defenses. This approach should let more people set up their
own Tor networks, either for testing or because they can't reach the
main Tor network.
 [https://www.torproject.org/svn/trunk/doc/spec/proposals/135-private-tor-...](https://www.torproject.org/svn/trunk/doc/spec/proposals/135-private-tor-networks.txt "https://www.torproject.org/svn/trunk/doc/spec/proposals/135-private-tor-networks.txt")

We have the beginnings of a grand plan for how to successfully scale
the Tor network to orders of magnitude more relays than we have
currently. Much more work and thinking remain.
 [https://www.torproject.org/svn/trunk/doc/spec/proposals/ideas/xxx-grand-...](https://www.torproject.org/svn/trunk/doc/spec/proposals/ideas/xxx-grand-scaling-plan.txt "https://www.torproject.org/svn/trunk/doc/spec/proposals/ideas/xxx-grand-scaling-plan.txt")

We also did a retrospective on currently open but not finished design
proposals, so we don't have as many "open" proposals in the pipeline
but not getting attention:
 [http://archives.seul.org/or/dev/Apr-2008/msg00009.html](http://archives.seul.org/or/dev/Apr-2008/msg00009.html "http://archives.seul.org/or/dev/Apr-2008/msg00009.html")

We added several more research papers that we'd like to see written to
the [https://www.torproject.org/volunteer#Research](https://www.torproject.org/volunteer#Research "https://www.torproject.org/volunteer#Research") page. In May we'll add
a few more and then start pointing academic professors at the new list.

The development version of Vidalia now has GUI boxes to configure an http
proxy that Vidalia should launch when it starts. (The Tor Browser Bundle
already uses these config options internally to launch Polipo when it
starts.) The next steps are to make sure that Polipo (our preferred new
http proxy) is stable enough on Windows, and then start shipping some
new standard bundles with Polipo rather than Privoxy.

We cleaned up the Torbutton install in the OS X bundles so it installs
Torbutton for the local user, rather than global. Hopefully this will
make OS X users happier.

We're making progress on integrating a UPnP library into Vidalia. This
feature will allow users who want to set up a Tor relay but don't want
to muck with manual port forwarding on their router/firewall to just
click a button and have Vidalia interact with their router/firewall
automatically. This approach won't work in all cases, but it should work
in at least some. We hope to land the first version of this in May.

Steven Murdoch and Robert Watson worked towards a final version of
their PETS 2008 paper called "Metrics for Security and Performance in
Low-Latency Anonymity Systems." The final version will be available in
May at:
 [http://www.cl.cam.ac.uk/~sjm217/papers/pets08metrics.pdf](http://www.cl.cam.ac.uk/~sjm217/papers/pets08metrics.pdf "http://www.cl.cam.ac.uk/~sjm217/papers/pets08metrics.pdf")

So far there appear to be no free-software zip splitters that work
on Windows and produce self-contained exe files for automatically
reconstructing the file. Rather than using a closed-source shareware
application (as it seems a shame to put a trust gap in our build process
when we don't need to), the current plan is to write some instructions
for users to fetch the 7zip program, and then fetch a set of blocks,
and run a batch file to reconstruct them. We're in the process of trying
to learn how large the blocks can be -- preliminary guess is 2MB.

We have a first draft of a translation portal up here:
 [https://www.torproject.org/translation-portal](https://www.torproject.org/translation-portal "https://www.torproject.org/translation-portal")

The Vidalia GUI now has (manual) translation instructions:
 [http://trac.vidalia-project.net/wiki/Translations](http://trac.vidalia-project.net/wiki/Translations "http://trac.vidalia-project.net/wiki/Translations")

We've registered the Vidalia project on "LaunchPad", which is a
web-based translation site that is compatible with Vidalia's string
format:
 [https://translations.launchpad.net/vidalia/trunk/+pots/vidalia](https://translations.launchpad.net/vidalia/trunk/+pots/vidalia "https://translations.launchpad.net/vidalia/trunk/+pots/vidalia")
We're currently working to try to upload our current translations into
the LaunchPad interface.

We've registered the Torbutton project on "BabelZilla", which is a
web-based translation site designed specifically for Firefox extensions.
We've uploaded the current translation strings:
 [http://www.babelzilla.org/index.php?option=com\_wts&Itemid=88&extension=3...](http://www.babelzilla.org/index.php?option=com_wts&Itemid=88&extension=3510&type=lang "http://www.babelzilla.org/index.php?option=com\_wts&Itemid=88&extension=3510&type=lang")

Lastly, we've begun developer-oriented documentation for how to manage
and maintain these various translation web-interfaces:
 [https://www.torproject.org/svn/trunk/doc/translations.txt](https://www.torproject.org/svn/trunk/doc/translations.txt "https://www.torproject.org/svn/trunk/doc/translations.txt")

