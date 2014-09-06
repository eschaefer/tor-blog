---
layout: post
title: "January 2009 Progress Report"
permalink: blog/january-2009-progress-report
date: 2009-02-23
author: phobos
category: blog
tags: ["bug fixes", "progress report", "releases", "security fixes", "translations"]
---

 **New releases, new hires, new funding**

Tor 0.2.1.10-alpha (released January 6) fixes two major bugs in bridge
relays (one that would make the bridge relay not so useful if it had
DirPort set to 0, and one that could let an attacker learn a little bit
of information about the bridge's users), and a bug that would cause your
Tor relay to ignore a circuit create request it can't decrypt (rather
than reply with an error). It also fixes a wide variety of other bugs.
 [http://archives.seul.org/or/talk/Jan-2009/msg00078.html](http://archives.seul.org/or/talk/Jan-2009/msg00078.html "http://archives.seul.org/or/talk/Jan-2009/msg00078.html")

Tor 0.2.1.11-alpha (released Jan 20) finishes fixing the "if your Tor is
off for a week it will take a long time to bootstrap again" bug. It also
fixes an important security-related bug reported by Ilja van Sprundel. You
should upgrade. (We'll send out more details about the bug once people
have had some time to upgrade.)
 [http://archives.seul.org/or/talk/Jan-2009/msg00171.html](http://archives.seul.org/or/talk/Jan-2009/msg00171.html "http://archives.seul.org/or/talk/Jan-2009/msg00171.html")

Tor 0.2.0.33 (released Jan 21) fixes a variety of bugs that were making
relays less useful to users. It also finally fixes a bug where a relay or
client that's been off for many days would take a long time to bootstrap.
 [http://archives.seul.org/or/announce/Jan-2009/msg00000.html](http://archives.seul.org/or/announce/Jan-2009/msg00000.html "http://archives.seul.org/or/announce/Jan-2009/msg00000.html")

Tor Browser Bundle 1.1.8 (released Jan 22) updates Tor to 0.2.1.11-alpha
(security update), updates OpenSSL to 0.9.8j (security update), updates
Firefox to 3.0.5, updates Pidgin to 2.5.4, and updates libevent to 1.4.9.
 [https://svn.torproject.org/svn/torbrowser/trunk/README](https://svn.torproject.org/svn/torbrowser/trunk/README "https://svn.torproject.org/svn/torbrowser/trunk/README")

This month we also hired three new people: Martin Peck is working on
Tor VM, a new way of packaging Tor on Windows that will let people use
Youtube safely again; Mike Perry is working on Torbutton maintenance
and development and on Torflow, a set of scripts to do measurements on
the Tor network; and Andrew Lewman is our new executive director.

**Enhancements**
Major bugfixes in the Tor 0.2.1.10-alpha and 0.2.0.33 releases:
- If the cached networkstatus consensus is more than five days old,
 discard it rather than trying to use it. In theory it could be useful
 because it lists alternate directory mirrors, but in practice it just
 means we spend many minutes trying directory mirrors that are long
 gone from the network. Helps bug 887 a bit; bugfix on 0.2.0.x.

Tor 0.2.1.10-alpha contains cleanups that let Tor build on Google's
Android phone:
- Change our header file guard macros to be less likely to conflict
 with system headers. Adam Langley noticed that we were conflicting
 with log.h on Android.

Major bugfixes in the Tor 0.2.1.11-alpha and 0.2.0.33 releases:
- Discard router descriptors as we load them if they are more than
 five days old. Otherwise if Tor is off for a long time and then
 starts with cached descriptors, it will try to use the onion
 keys in those obsolete descriptors when building circuits. Bugfix
 on 0.2.0.x. Fixes bug 887.

Security bugfixes in the Tor 0.2.1.11-alpha and 0.2.0.33 releases:
- Fix a heap-corruption bug that may be remotely triggerable on
 some platforms. Reported by Ilja van Sprundel.

Circuit-building speedups in Tor 0.2.1.10-alpha:
- When a relay gets a create cell it can't decrypt (e.g. because it's
 using the wrong onion key), we were dropping it and letting the
 client time out. Now actually answer with a destroy cell. Fixes
 bug 904. Bugfix on 0.0.2pre8.

Scalability fixes from the Tor 0.2.0.33 ChangeLog:
- Clip the MaxCircuitDirtiness config option to a minimum of 10 seconds,
 and the CircuitBuildTimeout to a minimum of 30 seconds. Warn the user if
 lower values are given in the configuration. These fixes prevent a user
 from rebuilding circuits too often, which can be a denial-of-service
 attack on the network.
- When a stream at an exit relay is in state "resolving" or
 "connecting" and it receives an "end" relay cell, the exit relay
 would silently ignore the end cell and not close the stream. If
 the client never closes the circuit, then the exit relay never
 closes the TCP connection. Bug introduced in Tor 0.1.2.1-alpha;
 reported by "wood".
- When sending CREATED cells back for a given circuit, use a 64-bit
 connection ID to find the right connection, rather than an addr:port
 combination. Now that we can have multiple OR connections between
 the same ORs, it is no longer possible to use addr:port to uniquely
 identify a connection.

Bootstrapping speedups in Tor 0.2.1.11-alpha:
- When our circuit fails at the first hop (e.g. we get a destroy
 cell back), avoid using that OR connection anymore, and also
 tell all the one-hop directory requests waiting for it that they
 should fail. Bugfix on 0.2.1.3-alpha.

**Architecture**
Proposal 158 ("Clients download consensus + microdescriptors") suggests a
new way forward for reducing directory overhead for clients, and replaced
part of proposal 141. Rather than modifying the circuit-building protocol
to fetch a server descriptor inline at each circuit extend, we instead put
all of the information that clients need either into the consensus itself,
or into a new set of data about each relay called a microdescriptor.
 [https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/158-microdes...](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/158-microdescriptors.txt "https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/158-microdescriptors.txt")

From the 0.2.0.33 ChangeLog:
- Never use OpenSSL compression: it wastes RAM and CPU trying to compress
 cells, which are basically all encrypted, compressed, or both. It also
 made us stand out from other applications on the wire.

**Advocacy**
Jillian York continued blogging for us about the good uses of Tor:
 [http://www.knightpulse.org/blog/tor](http://www.knightpulse.org/blog/tor "http://www.knightpulse.org/blog/tor")

"Federico Heinz advocates anonymous browsing in Argentina", Jan 8
 [http://www.knightpulse.org/blog/09/01/08/federico-heinz-advocates-anonym...](http://www.knightpulse.org/blog/09/01/08/federico-heinz-advocates-anonymous-browsing-argentina "http://www.knightpulse.org/blog/09/01/08/federico-heinz-advocates-anonymous-browsing-argentina")

"Human Rights Organizations in Argentina welcome anonymous browsing", Jan 25
 [http://www.knightpulse.org/blog/09/01/25/human-rights-organizations-arge...](http://www.knightpulse.org/blog/09/01/25/human-rights-organizations-argentina-welcome-anonymous-browsing "http://www.knightpulse.org/blog/09/01/25/human-rights-organizations-argentina-welcome-anonymous-browsing")

"Watch how you get around", Jan 30
 [http://www.knightpulse.org/blog/09/01/30/watch-how-you-get-around](http://www.knightpulse.org/blog/09/01/30/watch-how-you-get-around "http://www.knightpulse.org/blog/09/01/30/watch-how-you-get-around")

**Pre-configured bundles**
Tor Browser Bundle 1.1.8 (released Jan 22) updates Tor to 0.2.1.11-alpha
(security update), updates OpenSSL to 0.9.8j (security update), updates
Firefox to 3.0.5, updates Pidgin to 2.5.4, and updates libevent to 1.4.9.
 [https://svn.torproject.org/svn/torbrowser/trunk/README](https://svn.torproject.org/svn/torbrowser/trunk/README "https://svn.torproject.org/svn/torbrowser/trunk/README")

We continued work on Vidalia features to support where we want Tor
Browser Bundle to go. In particular, we're changing it to be able to
launch Firefox natively, rather than use the "PortableFirefox" pile of
complex scripts. We hope this change will also let users run a normal
Firefox alongside TBB. More on that in February.

We also continued work on Tor VM, a new way of packaging Tor on
Windows that will (among other things) let people use Youtube safely
again. Hopefully we'll have some simple instructions up about that in
February too.

**Bridges**
Major bugfixes in the Tor 0.2.1.10-alpha and 0.2.0.33 releases:
- Bridge relays that had DirPort set to 0 would stop fetching
 descriptors shortly after startup, and then briefly resume
 after a new bandwidth test and/or after publishing a new bridge
 descriptor. Bridge users that try to bootstrap from them would
 get a recent networkstatus but would get descriptors from up to
 18 hours earlier, meaning most of the descriptors were obsolete
 already. Reported by Tas; bugfix on 0.2.0.13-alpha.
- Prevent bridge relays from serving their 'extrainfo' document
 to anybody who asks, now that extrainfo docs include potentially
 sensitive aggregated client geoip summaries. Bugfix on
 0.2.0.13-alpha.

Bugfixes in the Tor 0.2.1.10-alpha release:
- When we made bridge authorities stop serving bridge descriptors over
 unencrypted links, we also broke DirPort reachability testing for
 bridges. So bridges with a non-zero DirPort were printing spurious
 warns to their logs. Bugfix on 0.2.0.16-alpha. Fixes bug 709.

New feature in Tor 0.2.1.10-alpha:
- New controller event "clients\_seen" to report a geoip-based summary
 of which countries we've seen clients from recently. Now controllers
 like Vidalia can show bridge operators that they're actually making
 a difference.
Vidalia will add support for this feature in February.

**Alternate download methods**
Our "gettor" email auto-responder is up and working:
 [https://svn.torproject.org/svn/projects/gettor/README](https://svn.torproject.org/svn/projects/gettor/README "https://svn.torproject.org/svn/projects/gettor/README")
 [https://www.torproject.org/finding-tor#Mail](https://www.torproject.org/finding-tor#Mail "https://www.torproject.org/finding-tor#Mail")

Thandy itself is working smoothly at this point too -- it can contact
the central repository, check all the keys, look in the registry and
compare the currently installed version to the new choices, fetch the
right packages, check all the signatures, and launch the install.

As of December we only had a new MSI-based installer for Tor, but not for
Vidalia, Torbutton, or Polipo. Now we do, though it's still in testing:
 [https://data.peertech.org/torbld](https://data.peertech.org/torbld "https://data.peertech.org/torbld")

**Translations**
Our translation server is up and online:
 [https://translation.torproject.org/](https://translation.torproject.org/ "https://translation.torproject.org/")
 [https://www.torproject.org/translation-portal](https://www.torproject.org/translation-portal "https://www.torproject.org/translation-portal")

We continued enhancements to the Chinese and Russian Tor website
translations. Our Farsi translation from this summer is slowly becoming
obsolete; we should solve that at some point.

