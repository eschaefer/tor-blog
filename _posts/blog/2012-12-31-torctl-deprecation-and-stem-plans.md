---
layout: post
title: "TorCtl Deprecation and Stem Plans"
permalink: torctl-deprecation-and-stem-plans
date: 2012-12-31 17:38:05
author: atagar
category: blog
status: closed
tags: ["controller", "python", "stem", "torctl"]
---

Hi all. Just a friendly heads up concerning a couple things going on in our python controller space.

The first is that Mike and I have decided to deprecate [TorCtl](https://gitweb.torproject.org/pytorctl.git) and make it a part of TorFlow (the framework used to support the Bandwidth Authorities and SoaT). The TorCtl codebase has largely been frozen for years out of concern for the stability of the Bandwidth Authorities (which lack any tests).

If you're writing scripts or controller applications for Tor then you're encouraged to move to either...

-   [Stem](https://stem.torproject.org/)
    ------------------------------------

    Library with a similar design to TorCtl, but friendlier APIs and documentation. This has reached feature parity with TorCtl and is still being actively developed, so if there's something it can do to better suit your needs then please let me know!

-   [Txtorcon](https://txtorcon.readthedocs.org/)
    ---------------------------------------------

    Twisted controller library written by Meejah, and used in projects like Ooni Probe.

Both of these libraries have extensive test suites and are being very actively maintained.

* * * * *

The second part are my plans regarding Stem. As of early December we've reached feature completion, covering just about everything in the control-spec and dir-spec.

Next up is migrating our controllers. So far we've moved [arm](http://www.atagar.com/arm/) (the largest python controller we have) and the [consensus-tracker](https://gitweb.torproject.org/atagar/tor-utils.git/blob/HEAD:/consensusTracker.py). Other controllers we have queued up to move are TorBEL, Tor Weather, and the control interpretor.

I've avoided making an initial release announcement for stem because until we have actual users of the library we won't be sure that we nailed a nice, intuitive API (and hence, can't promise that it'll be frozen).

On reflection this is letting the perfect be the enemy of the good. Stem's API is unlikely to change substantially, and holding off on an initial release poses a chicken-and-egg situation. Users want a frozen API before using stem, but we need users before feeling confident enough to lock down the API.

So here's what I propose. For the next couple months stem will have an open beta. If you'd like to have input on the future of our python controller space then please give Stem a try and [tell me the following](http://www.atagar.com/contact/)...

-   What pain points did you encounter? Is there anything that you'd like to see changed or that we're missing?

-   If your project is public then please tell me where I can find your code. I'll review it, both to suggest improvements and see how we can tweak stem to better suit your needs.

In the unlikely event we make a backward incompatible change I'll check with the beta participants to be sure we don't break anyone (and submit fixes if we do).

Cheers! -Damian (atagar on irc)

PS. Many thanks to Ravi, Sean, Eoin, Beck, Erik, Megan, Sathyanarayanan, and everyone else who has helped stem get to this point. Happy New Year!
