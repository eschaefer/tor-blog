---
layout: post
title: "A new alpha series begins: Tor 0.2.6.1-alpha is released"
permalink: new-alpha-series-begins-tor-0261-alpha-released
date: 2014-10-30 12:52:11
author: nickm
category: blog
comments: open
tags: ["026", "0261", "alpha", "release", "tor"]
---

Tor 0.2.6.1-alpha is the first release in the Tor 0.2.6.x series. It includes numerous code cleanups and new tests, and fixes a large number of annoying bugs. Out-of-memory conditions are handled better than in 0.2.5, pluggable transports have improved proxy support, and clients now use optimistic data for contacting hidden services. Also, we are now more robust to changes in what we consider a parseable directory object, so that tightening restrictions does not have a risk of introducing infinite download loops.

This is the first alpha release in a new series, so expect there to be bugs. Users who would rather test out a more stable branch should stay with 0.2.5.x for now.

This announcement is for the source release only; I'd expect that compiled packages for several platforms should be available over the next several days.

Changes in version 0.2.6.1-alpha - 2014-10-30

-   New compiler and system requirements:
    -   Tor 0.2.6.x requires that your compiler support more of the C99 language standard than before. The 'configure' script now detects whether your compiler supports C99 mid-block declarations and designated initializers. If it does not, Tor will not compile.

        We may revisit this requirement if it turns out that a significant number of people need to build Tor with compilers that don't bother implementing a 15-year-old standard. Closes ticket 13233.

    -   Tor no longer supports systems without threading support. When we began working on Tor, there were several systems that didn't have threads, or where the thread support wasn't able to run the threads of a single process on multiple CPUs. That no longer holds: every system where Tor needs to run well now has threading support. Resolves ticket 12439.

  [**read more »**](https://blog.torproject.org/blog/new-alpha-series-begins-tor-0261-alpha-released)
