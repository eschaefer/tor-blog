---
layout: post
title: "Tor 0.2.2.14-alpha released"
permalink: blog/tor-02214-alpha-released
date: 2010-07-19
author: phobos
category: blog
tags: ["alpha release", "directory authority", "geoip", "performance improvements"]
---

Tor 0.2.2.14-alpha greatly improves client-side handling of circuit build
timeouts, which are used to estimate speed and improve performance. We
also move to a much better GeoIP database, port Tor to Windows CE,
introduce new compile flags that improve code security, add an eighth
v3 directory authority, and address a lot of more minor issues.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

Packages will be appearing over the next few days or weeks. (We've decided
to start announcing alpha versions when they're released, rather than
waiting for all the packages first.)

Changes in version 0.2.2.14-alpha - 2010-07-12
 o Major bugfixes:
 - Tor directory authorities no longer crash when started with a
 cached-microdesc-consensus file in their data directory. Bugfix
 on 0.2.2.6-alpha; fixes bug 1532.
 - Treat an unset $HOME like an empty $HOME rather than triggering an
 assert. Bugfix on 0.0.8pre1; fixes bug 1522.
 - Ignore negative and large circuit build timeout values that can
 happen during a suspend or hibernate. These values caused various
 asserts to fire. Bugfix on 0.2.2.2-alpha; fixes bug 1245.
 - Alter calculation of Pareto distribution parameter 'Xm' for
 Circuit Build Timeout learning to use the weighted average of the
 top N=3 modes (because we have three entry guards). Considering
 multiple modes should improve the timeout calculation in some cases,
 and prevent extremely high timeout values. Bugfix on 0.2.2.2-alpha;
 fixes bug 1335.
 - Alter calculation of Pareto distribution parameter 'Alpha' to use a
 right censored distribution model. This approach improves over the
 synthetic timeout generation approach that was producing insanely
 high timeout values. Now we calculate build timeouts using truncated
 times. Bugfix on 0.2.2.2-alpha; fixes bugs 1245 and 1335.
 - Do not close circuits that are under construction when they reach
 the circuit build timeout. Instead, leave them building (but do not
 use them) for up until the time corresponding to the 95th percentile
 on the Pareto CDF or 60 seconds, whichever is greater. This is done
 to provide better data for the new Pareto model. This percentile
 can be controlled by the consensus.

o Major features:
 - Move to the June 2010 Maxmind GeoLite country db (rather than the
 June 2009 ip-to-country GeoIP db) for our statistics that count
 how many users relays are seeing from each country. Now we have
 more accurate data for many African countries.
 - Port Tor to build and run correctly on Windows CE systems, using
 the wcecompat library. Contributed by Valerio Lupi.
 - New "--enable-gcc-hardening" ./configure flag (off by default)
 to turn on gcc compile time hardening options. It ensures
 that signed ints have defined behavior (-fwrapv), enables
 -D\_FORTIFY\_SOURCE=2 (requiring -O2), adds stack smashing protection
 with canaries (-fstack-protector-all), turns on ASLR protection if
 supported by the kernel (-fPIE, -pie), and adds additional security
 related warnings. Verified to work on Mac OS X and Debian Lenny.
 - New "--enable-linker-hardening" ./configure flag (off by default)
 to turn on ELF specific hardening features (relro, now). This does
 not work with Mac OS X or any other non-ELF binary format.

o New directory authorities:
 - Set up maatuska (run by Linus Nordberg) as the eighth v3 directory
 authority.

o Minor features:
 - New config option "WarnUnsafeSocks 0" disables the warning that
 occurs whenever Tor receives only an IP address instead of a
 hostname. Setups that do DNS locally over Tor are fine, and we
 shouldn't spam the logs in that case.
 - Convert the HACKING file to asciidoc, and add a few new sections
 to it, explaining how we use Git, how we make changelogs, and
 what should go in a patch.
 - Add a TIMEOUT\_RATE keyword to the BUILDTIMEOUT\_SET control port
 event, to give information on the current rate of circuit timeouts
 over our stored history.
 - Add ability to disable circuit build time learning via consensus
 parameter and via a LearnCircuitBuildTimeout config option. Also
 automatically disable circuit build time calculation if we are
 either a AuthoritativeDirectory, or if we fail to write our state
 file. Fixes bug 1296.
 - More gracefully handle corrupt state files, removing asserts
 in favor of saving a backup and resetting state.
 - Rename the "log.h" header to "torlog.h" so as to conflict with fewer
 system headers.

o Minor bugfixes:
 - Build correctly on OSX with zlib 1.2.4 and higher with all warnings
 enabled.
 - When a2x fails, mention that the user could disable manpages instead
 of trying to fix their asciidoc installation.
 - Where available, use Libevent 2.0's periodic timers so that our
 once-per-second cleanup code gets called even more closely to
 once per second than it would otherwise. Fixes bug 943.
 - If you run a bridge that listens on multiple IP addresses, and
 some user configures a bridge address that uses a different IP
 address than your bridge writes in its router descriptor, and the
 user doesn't specify an identity key, their Tor would discard the
 descriptor because "it isn't one of our configured bridges", and
 fail to bootstrap. Now believe the descriptor and bootstrap anyway.
 Bugfix on 0.2.0.3-alpha.
 - If OpenSSL fails to make a duplicate of a private or public key, log
 an error message and try to exit cleanly. May help with debugging
 if bug 1209 ever remanifests.
 - Save a couple bytes in memory allocation every time we escape
 certain characters in a string. Patch from Florian Zumbiehl.
 - Make it explicit that we don't cannibalize one-hop circuits. This
 happens in the wild, but doesn't turn out to be a problem because
 we fortunately don't use those circuits. Many thanks to outofwords
 for the initial analysis and to swissknife who confirmed that
 two-hop circuits are actually created.
 - Make directory mirrors report non-zero dirreq-v[23]-shares again.
 Fixes bug 1564; bugfix on 0.2.2.9-alpha.
 - Eliminate a case where a circuit build time warning was displayed
 after network connectivity resumed. Bugfix on 0.2.2.2-alpha.

