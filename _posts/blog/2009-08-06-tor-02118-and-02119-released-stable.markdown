---
layout: post
title: "Tor 0.2.1.18 and 0.2.1.19 released as stable"
permalink: blog/tor-02118-and-02119-released-stable
date: 2009-08-06
author: phobos
category: blog
tags: ["anonymity fixes", "bug fixes", "deprecated features", "feature enhancements", "stable release"]
---

Tor 0.2.1.18 lays the foundations for performance improvements, adds
status events to help users diagnose bootstrap problems, adds optional
authentication/authorization for hidden services, fixes a variety of
potential anonymity problems, and includes a huge pile of other features
and bug fixes.

Tor 0.2.1.19 fixes a major bug with accessing and providing hidden
services.

[https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

Changes in version 0.2.1.19 - 2009-07-28
**Major bugfixes:**

- Make accessing hidden services on 0.2.1.x work right again.
 Bugfix on 0.2.1.3-alpha; workaround for bug 1038. Diagnosis and
 part of patch provided by "optimist".

**Minor features:**

- When a relay/bridge is writing out its identity key fingerprint to
 the "fingerprint" file and to its logs, write it without spaces. Now
 it will look like the fingerprints in our bridges documentation,
 and confuse fewer users.

**Minor bugfixes:**

- Relays no longer publish a new server descriptor if they change
 their MaxAdvertisedBandwidth config option but it doesn't end up
 changing their advertised bandwidth numbers. Bugfix on 0.2.0.28-rc;
 fixes bug 1026. Patch from Sebastian.
- Avoid leaking memory every time we get a create cell but we have
 so many already queued that we refuse it. Bugfix on 0.2.0.19-alpha;
 fixes bug 1034. Reported by BarkerJr.

Changes in version 0.2.1.18 - 2009-07-24
**Major features (clients):**

- Start sending "bootstrap phase" status events to the controller,
 so it can keep the user informed of progress fetching directory
 information and establishing circuits. Also inform the controller
 if we think we're stuck at a particular bootstrap phase. Implements
 proposal 137.
- Clients replace entry guards that were chosen more than a few months
 ago. This change should significantly improve client performance,
 especially once more people upgrade, since relays that have been
 a guard for a long time are currently overloaded.
- Network status consensus documents and votes now contain bandwidth
 information for each relay. Clients use the bandwidth values
 in the consensus, rather than the bandwidth values in each
 relay descriptor. This approach opens the door to more accurate
 bandwidth estimates once the directory authorities start doing
 active measurements. Implements part of proposal 141.

**Major features (relays):**

- Disable and refactor some debugging checks that forced a linear scan
 over the whole server-side DNS cache. These accounted for over 50%
 of CPU time on a relatively busy exit node's gprof profile. Also,
 disable some debugging checks that appeared in exit node profile
 data. Found by Jacob.
- New DirPortFrontPage option that takes an html file and publishes
 it as "/" on the DirPort. Now relay operators can provide a
 disclaimer without needing to set up a separate webserver. There's
 a sample disclaimer in contrib/tor-exit-notice.html.

**Major features (hidden services):**

- Make it possible to build hidden services that only certain clients
 are allowed to connect to. This is enforced at several points,
 so that unauthorized clients are unable to send INTRODUCE cells
 to the service, or even (depending on the type of authentication)
 to learn introduction points. This feature raises the bar for
 certain kinds of active attacks against hidden services. Design
 and code by Karsten Loesing. Implements proposal 121.
- Relays now store and serve v2 hidden service descriptors by default,
 i.e., the new default value for HidServDirectoryV2 is 1. This is
 the last step in proposal 114, which aims to make hidden service
 lookups more reliable.

**Major features (path selection):**

- ExitNodes and Exclude\*Nodes config options now allow you to restrict
 by country code ("{US}") or IP address or address pattern
 ("255.128.0.0/16"). Patch from Robert Hogan. It still needs some
 refinement to decide what config options should take priority if
 you ask to both use a particular node and exclude it.

**Major features (misc):**

- When building a consensus, do not include routers that are down.
 This cuts down 30% to 40% on consensus size. Implements proposal
 138.
- New TestingTorNetwork config option to allow adjustment of
 previously constant values that could slow bootstrapping. Implements
 proposal 135. Patch from Karsten.
- Convert many internal address representations to optionally hold
 IPv6 addresses. Generate and accept IPv6 addresses in many protocol
 elements. Make resolver code handle nameservers located at IPv6
 addresses.
- More work on making our TLS handshake blend in: modify the list
 of ciphers advertised by OpenSSL in client mode to even more
 closely resemble a common web browser. We cheat a little so that
 we can advertise ciphers that the locally installed OpenSSL doesn't
 know about.
- Use the TLS1 hostname extension to more closely resemble browser
 behavior.

**Security fixes (anonymity/entropy):**

- Never use a connection with a mismatched address to extend a
 circuit, unless that connection is canonical. A canonical
 connection is one whose address is authenticated by the router's
 identity key, either in a NETINFO cell or in a router descriptor.
- Implement most of proposal 110: The first K cells to be sent
 along a circuit are marked as special "early" cells; only K "early"
 cells will be allowed. Once this code is universal, we can block
 certain kinds of denial-of-service attack by requiring that EXTEND
 commands must be sent using an "early" cell.
- Resume using OpenSSL's RAND\_poll() for better (and more portable)
 cross-platform entropy collection again. We used to use it, then
 stopped using it because of a bug that could crash systems that
 called RAND\_poll when they had a lot of fds open. It looks like the
 bug got fixed in late 2006. Our new behavior is to call RAND\_poll()
 at startup, and to call RAND\_poll() when we reseed later only if
 we have a non-buggy OpenSSL version.
- When the client is choosing entry guards, now it selects at most
 one guard from a given relay family. Otherwise we could end up with
 all of our entry points into the network run by the same operator.
 Suggested by Camilo Viecco. Fix on 0.1.1.11-alpha.
- Do not use or believe expired v3 authority certificates. Patch
 from Karsten. Bugfix in 0.2.0.x. Fixes bug 851.
- Drop begin cells to a hidden service if they come from the middle
 of a circuit. Patch from lark.
- When we erroneously receive two EXTEND cells for the same circuit
 ID on the same connection, drop the second. Patch from lark.
- Authorities now vote for the Stable flag for any router whose
 weighted MTBF is at least 5 days, regardless of the mean MTBF.
- Clients now never report any stream end reason except 'MISC'.
 Implements proposal 148.

**Major bugfixes (crashes):**

- Parse dates and IPv4 addresses in a locale- and libc-independent
 manner, to avoid platform-dependent behavior on malformed input.
- Fix a crash that occurs on exit nodes when a nameserver request
 timed out. Bugfix on 0.1.2.1-alpha; our CLEAR debugging code had
 been suppressing the bug since 0.1.2.10-alpha. Partial fix for
 bug 929.
- Do not assume that a stack-allocated character array will be
 64-bit aligned on platforms that demand that uint64\_t access is
 aligned. Possible fix for bug 604.
- Resolve a very rare crash bug that could occur when the user forced
 a nameserver reconfiguration during the middle of a nameserver
 probe. Fixes bug 526. Bugfix on 0.1.2.1-alpha.
- Avoid a "0 divided by 0" calculation when calculating router uptime
 at directory authorities. Bugfix on 0.2.0.8-alpha.
- Fix an assertion bug in parsing policy-related options; possible fix
 for bug 811.
- Rate-limit too-many-sockets messages: when they happen, they happen
 a lot and end up filling up the disk. Resolves bug 748.
- Fix a race condition that could cause crashes or memory corruption
 when running as a server with a controller listening for log
 messages.
- Avoid crashing when we have a policy specified in a DirPolicy or
 SocksPolicy or ReachableAddresses option with ports set on it,
 and we re-load the policy. May fix bug 996.
- Fix an assertion failure on 64-bit platforms when we allocated
 memory right up to the end of a memarea, then realigned the memory
 one step beyond the end. Fixes a possible cause of bug 930.
- Protect the count of open sockets with a mutex, so we can't
 corrupt it when two threads are closing or opening sockets at once.
 Fix for bug 939. Bugfix on 0.2.0.1-alpha.

**Major bugfixes (clients):**

- Discard router descriptors as we load them if they are more than
 five days old. Otherwise if Tor is off for a long time and then
 starts with cached descriptors, it will try to use the onion keys
 in those obsolete descriptors when building circuits. Fixes bug 887.
- When we choose to abandon a new entry guard because we think our
 older ones might be better, close any circuits pending on that
 new entry guard connection. This fix should make us recover much
 faster when our network is down and then comes back. Bugfix on
 0.1.2.8-beta; found by lodger.
- When Tor clients restart after 1-5 days, they discard all their
 cached descriptors as too old, but they still use the cached
 consensus document. This approach is good for robustness, but
 bad for performance: since they don't know any bandwidths, they
 end up choosing at random rather than weighting their choice by
 speed. Fixed by the above feature of putting bandwidths in the
 consensus.

**Major bugfixes (relays):**

- Relays were falling out of the networkstatus consensus for
 part of a day if they changed their local config but the
 authorities discarded their new descriptor as "not sufficiently
 different". Now directory authorities accept a descriptor as changed
 if BandwidthRate or BandwidthBurst changed. Partial fix for bug 962;
 patch by Sebastian.
- Ensure that two circuits can never exist on the same connection
 with the same circuit ID, even if one is marked for close. This
 is conceivably a bugfix for bug 779; fixes a bug on 0.1.0.4-rc.
- Directory authorities were neglecting to mark relays down in their
 internal histories if the relays fall off the routerlist without
 ever being found unreachable. So there were relays in the histories
 that haven't been seen for eight months, and are listed as being
 up for eight months. This wreaked havoc on the "median wfu" and
 "median mtbf" calculations, in turn making Guard and Stable flags
 wrong, hurting network performance. Fixes bugs 696 and 969. Bugfix
 on 0.2.0.6-alpha.

**Major bugfixes (hidden services):**

- When establishing a hidden service, introduction points that
 originate from cannibalized circuits were completely ignored
 and not included in rendezvous service descriptors. This might
 have been another reason for delay in making a hidden service
 available. Bugfix from long ago (0.0.9.x?)

**Major bugfixes (memory and resource management):**

- Fixed some memory leaks -- some quite frequent, some almost
 impossible to trigger -- based on results from Coverity.
- Speed up parsing and cut down on memory fragmentation by using
 stack-style allocations for parsing directory objects. Previously,
 this accounted for over 40% of allocations from within Tor's code
 on a typical directory cache.
- Use a Bloom filter rather than a digest-based set to track which
 descriptors we need to keep around when we're cleaning out old
 router descriptors. This speeds up the computation significantly,
 and may reduce fragmentation.

**New/changed config options:**

- Now NodeFamily and MyFamily config options allow spaces in
 identity fingerprints, so it's easier to paste them in.
 Suggested by Lucky Green.
- Allow ports 465 and 587 in the default exit policy again. We had
 rejected them in 0.1.0.15, because back in 2005 they were commonly
 misconfigured and ended up as spam targets. We hear they are better
 locked down these days.
- Make TrackHostExit mappings expire a while after their last use, not
 after their creation. Patch from Robert Hogan.
- Add an ExcludeExitNodes option so users can list a set of nodes
 that should be be excluded from the exit node position, but
 allowed elsewhere. Implements proposal 151.
- New --hush command-line option similar to --quiet. While --quiet
 disables all logging to the console on startup, --hush limits the
 output to messages of warning and error severity.
- New configure/torrc options (--enable-geoip-stats,
 DirRecordUsageByCountry) to record how many IPs we've served
 directory info to in each country code, how many status documents
 total we've sent to each country code, and what share of the total
 directory requests we should expect to see.
- Make outbound DNS packets respect the OutboundBindAddress setting.
 Fixes the bug part of bug 798. Bugfix on 0.1.2.2-alpha.
- Allow separate log levels to be configured for different logging
 domains. For example, this allows one to log all notices, warnings,
 or errors, plus all memory management messages of level debug or
 higher, with: Log [MM] debug-err [\*] notice-err file /var/log/tor.
- Update to the "June 3 2009" ip-to-country file.

**Minor features (relays):**

- Raise the minimum rate limiting to be a relay from 20000 bytes
 to 20480 bytes (aka 20KB/s), to match our documentation. Also
 update directory authorities so they always assign the Fast flag
 to relays with 20KB/s of capacity. Now people running relays won't
 suddenly find themselves not seeing any use, if the network gets
 faster on average.
- If we're a relay and we change our IP address, be more verbose
 about the reason that made us change. Should help track down
 further bugs for relays on dynamic IP addresses.
- Exit servers can now answer resolve requests for ip6.arpa addresses.
- Implement most of Proposal 152: allow specialized servers to permit
 single-hop circuits, and clients to use those servers to build
 single-hop circuits when using a specialized controller. Patch
 from Josh Albrecht. Resolves feature request 768.
- When relays do their initial bandwidth measurement, don't limit
 to just our entry guards for the test circuits. Otherwise we tend
 to have multiple test circuits going through a single entry guard,
 which makes our bandwidth test less accurate. Fixes part of bug 654;
 patch contributed by Josh Albrecht.

**Minor features (directory authorities):**

- Try not to open more than one descriptor-downloading connection
 to an authority at once. This should reduce load on directory
 authorities. Fixes bug 366.
- Add cross-certification to newly generated certificates, so that
 a signing key is enough information to look up a certificate. Start
 serving certificates by
 pairs. Implements proposal 157.
- When a directory authority downloads a descriptor that it then
 immediately rejects, do not retry downloading it right away. Should
 save some bandwidth on authorities. Fix for bug 888. Patch by
 Sebastian Hahn.
- Directory authorities now serve a /tor/dbg-stability.txt URL to
 help debug WFU and MTBF calculations.
- In directory authorities' approved-routers files, allow
 fingerprints with or without space.

**Minor features (directory mirrors):**

- When a download gets us zero good descriptors, do not notify
 Tor that new directory information has arrived.
- Servers support a new URL scheme for consensus downloads that
 allows the client to specify which authorities are trusted.
 The server then only sends the consensus if the client will trust
 it. Otherwise a 404 error is sent back. Clients use this
 new scheme when the server supports it (meaning it's running
 0.2.1.1-alpha or later). Implements proposal 134.

**Minor features (bridges):**

- If the bridge config line doesn't specify a port, assume 443.
 This makes bridge lines a bit smaller and easier for users to
 understand.
- If we're using bridges and our network goes away, be more willing
 to forgive our bridges and try again when we get an application
 request.

**Minor features (hidden services):**

- When the client launches an introduction circuit, retry with a
 new circuit after 30 seconds rather than 60 seconds.
- Launch a second client-side introduction circuit in parallel
 after a delay of 15 seconds (based on work by Christian Wilms).
- Hidden services start out building five intro circuits rather
 than three, and when the first three finish they publish a service
 descriptor using those. Now we publish our service descriptor much
 faster after restart.
- Drop the requirement to have an open dir port for storing and
 serving v2 hidden service descriptors.

**Minor features (build and packaging):**

- On Linux, use the prctl call to re-enable core dumps when the User
 option is set.
- Try to make sure that the version of Libevent we're running with
 is binary-compatible with the one we built with. May address bug
 897 and others.
- Add a new --enable-local-appdata configuration switch to change
 the default location of the datadir on win32 from APPDATA to
 LOCAL\_APPDATA. In the future, we should migrate to LOCAL\_APPDATA
 entirely. Patch from coderman.
- Build correctly against versions of OpenSSL 0.9.8 or later that
 are built without support for deprecated functions.
- On platforms with a maximum syslog string length, truncate syslog
 messages to that length ourselves, rather than relying on the
 system to do it for us.
- Automatically detect MacOSX versions earlier than 10.4.0, and
 disable kqueue from inside Tor when running with these versions.
 We previously did this from the startup script, but that was no
 help to people who didn't use the startup script. Resolves bug 863.
- Build correctly when configured to build outside the main source
 path. Patch from Michael Gold.
- Disable GCC's strict alias optimization by default, to avoid the
 likelihood of its introducing subtle bugs whenever our code violates
 the letter of C99's alias rules.
- Change the contrib/tor.logrotate script so it makes the new
 logs as "\_tor:\_tor" rather than the default, which is generally
 "root:wheel". Fixes bug 676, reported by Serge Koksharov.
- Change our header file guard macros to be less likely to conflict
 with system headers. Adam Langley noticed that we were conflicting
 with log.h on Android.
- Add a couple of extra warnings to --enable-gcc-warnings for GCC 4.3,
 and stop using a warning that had become unfixably verbose under
 GCC 4.3.
- Use a lockfile to make sure that two Tor processes are not
 simultaneously running with the same datadir.
- Allow OpenSSL to use dynamic locks if it wants.
- Add LIBS=-lrt to Makefile.am so the Tor RPMs use a static libevent.

**Minor features (controllers):**

- When generating circuit events with verbose nicknames for
 controllers, try harder to look up nicknames for routers on a
 circuit. (Previously, we would look in the router descriptors we had
 for nicknames, but not in the consensus.) Partial fix for bug 941.
- New controller event NEWCONSENSUS that lists the networkstatus
 lines for every recommended relay. Now controllers like Torflow
 can keep up-to-date on which relays they should be using.
- New controller event "clients\_seen" to report a geoip-based summary
 of which countries we've seen clients from recently. Now controllers
 like Vidalia can show bridge operators that they're actually making
 a difference.
- Add a 'getinfo status/clients-seen' controller command, in case
 controllers want to hear clients\_seen events but connect late.
- New CONSENSUS\_ARRIVED event to note when a new consensus has
 been fetched and validated.
- Add an internal-use-only \_\_ReloadTorrcOnSIGHUP option for
 controllers to prevent SIGHUP from reloading the configuration.
 Fixes bug 856.
- Return circuit purposes in response to GETINFO circuit-status.
 Fixes bug 858.
- Serve the latest v3 networkstatus consensus via the control
 port. Use "getinfo dir/status-vote/current/consensus" to fetch it.
- Add a "GETINFO /status/bootstrap-phase" controller option, so the
 controller can query our current bootstrap state in case it attaches
 partway through and wants to catch up.
- Provide circuit purposes along with circuit events to the controller.

**Minor features (tools):**

- Do not have tor-resolve automatically refuse all .onion addresses;
 if AutomapHostsOnResolve is set in your torrc, this will work fine.
- Add a -p option to tor-resolve for specifying the SOCKS port: some
 people find host:port too confusing.
- Print the SOCKS5 error message string as well as the error code
 when a tor-resolve request fails. Patch from Jacob.

**Minor bugfixes (memory and resource management):**

- Clients no longer cache certificates for authorities they do not
 recognize. Bugfix on 0.2.0.9-alpha.
- Do not use C's stdio library for writing to log files. This will
 improve logging performance by a minute amount, and will stop
 leaking fds when our disk is full. Fixes bug 861.
- Stop erroneous use of O\_APPEND in cases where we did not in fact
 want to re-seek to the end of a file before every last write().
- Fix a small alignment and memory-wasting bug on buffer chunks.
 Spotted by rovv.
- Add a malloc\_good\_size implementation to OpenBSD\_malloc\_linux.c,
 to avoid unused RAM in buffer chunks and memory pools.
- Reduce the default smartlist size from 32 to 16; it turns out that
 most smartlists hold around 8-12 elements tops.
- Make dumpstats() log the fullness and size of openssl-internal
 buffers.
- If the user has applied the experimental SSL\_MODE\_RELEASE\_BUFFERS
 patch to their OpenSSL, turn it on to save memory on servers. This
 patch will (with any luck) get included in a mainline distribution
 before too long.
- Fix a memory leak when v3 directory authorities load their keys
 and cert from disk. Bugfix on 0.2.0.1-alpha.
- Stop using malloc\_usable\_size() to use more area than we had
 actually allocated: it was safe, but made valgrind really unhappy.
- Make the assert\_circuit\_ok() function work correctly on circuits that
 have already been marked for close.
- Fix uninitialized size field for memory area allocation: may improve
 memory performance during directory parsing.

**Minor bugfixes (clients):**

- Stop reloading the router list from disk for no reason when we
 run out of reachable directory mirrors. Once upon a time reloading
 it would set the 'is\_running' flag back to 1 for them. It hasn't
 done that for a long time.
- When we had picked an exit node for a connection, but marked it as
 "optional", and it turned out we had no onion key for the exit,
 stop wanting that exit and try again. This situation may not
 be possible now, but will probably become feasible with proposal
 158. Spotted by rovv. Fixes another case of bug 752.
- Fix a bug in address parsing that was preventing bridges or hidden
 service targets from being at IPv6 addresses.
- Do not remove routers as too old if we do not have any consensus
 document. Bugfix on 0.2.0.7-alpha.
- When an exit relay resolves a stream address to a local IP address,
 do not just keep retrying that same exit relay over and
 over. Instead, just close the stream. Addresses bug 872. Bugfix
 on 0.2.0.32. Patch from rovv.
- Made Tor a little less aggressive about deleting expired
 certificates. Partial fix for bug 854.
- Treat duplicate certificate fetches as failures, so that we do
 not try to re-fetch an expired certificate over and over and over.
- Do not say we're fetching a certificate when we'll in fact skip it
 because of a pending download.
- If we have correct permissions on $datadir, we complain to stdout
 and fail to start. But dangerous permissions on
 $datadir/cached-status/ would cause us to open a log and complain
 there. Now complain to stdout and fail to start in both cases. Fixes
 bug 820, reported by seeess.

**Minor bugfixes (bridges):**

- When we made bridge authorities stop serving bridge descriptors over
 unencrypted links, we also broke DirPort reachability testing for
 bridges. So bridges with a non-zero DirPort were printing spurious
 warns to their logs. Bugfix on 0.2.0.16-alpha. Fixes bug 709.
- Don't allow a bridge to publish its router descriptor to a
 non-bridge directory authority. Fixes part of bug 932.
- When we change to or from being a bridge, reset our counts of
 client usage by country. Fixes bug 932.

**Minor bugfixes (relays):**

- Log correct error messages for DNS-related network errors on
 Windows.
- Actually return -1 in the error case for read\_bandwidth\_usage().
 Harmless bug, since we currently don't care about the return value
 anywhere. Bugfix on 0.2.0.9-alpha.
- Provide a more useful log message if bug 977 (related to buffer
 freelists) ever reappears, and do not crash right away.
- We were already rejecting relay begin cells with destination port
 of 0. Now also reject extend cells with destination port or address
 of 0. Suggested by lark.
- When we can't transmit a DNS request due to a network error, retry
 it after a while, and eventually transmit a failing response to
 the RESOLVED cell. Bugfix on 0.1.2.5-alpha.
- Solve a bug that kept hardware crypto acceleration from getting
 enabled when accounting was turned on. Fixes bug 907. Bugfix on
 0.0.9pre6.
- When a canonical connection appears later in our internal list
 than a noncanonical one for a given OR ID, always use the
 canonical one. Bugfix on 0.2.0.12-alpha. Fixes bug 805.
 Spotted by rovv.
- Avoid some nasty corner cases in the logic for marking connections
 as too old or obsolete or noncanonical for circuits. Partial
 bugfix on bug 891.
- Fix another interesting corner-case of bug 891 spotted by rovv:
 Previously, if two hosts had different amounts of clock drift, and
 one of them created a new connection with just the wrong timing,
 the other might decide to deprecate the new connection erroneously.
 Bugfix on 0.1.1.13-alpha.
- If one win32 nameserver fails to get added, continue adding the
 rest, and don't automatically fail.
- Fix a bug where an unreachable relay would establish enough
 reachability testing circuits to do a bandwidth test -- if
 we already have a connection to the middle hop of the testing
 circuit, then it could establish the last hop by using the existing
 connection. Bugfix on 0.1.2.2-alpha, exposed when we made testing
 circuits no longer use entry guards in 0.2.1.3-alpha.

**Minor bugfixes (directory authorities):**

- Limit uploaded directory documents to be 16M rather than 500K.
 The directory authorities were refusing v3 consensus votes from
 other authorities, since the votes are now 504K. Fixes bug 959;
 bugfix on 0.0.2pre17 (where we raised it from 50K to 500K ;) .
- Directory authorities should never send a 503 "busy" response to
 requests for votes or keys. Bugfix on 0.2.0.8-alpha; exposed by
 bug 959.
- Fix code so authorities \_actually\_ send back X-Descriptor-Not-New
 headers. Bugfix on 0.2.0.10-alpha.

**Minor bugfixes (hidden services):**

- When we can't find an intro key for a v2 hidden service descriptor,
 fall back to the v0 hidden service descriptor and log a bug message.
 Workaround for bug 1024.
- In very rare situations new hidden service descriptors were
 published earlier than 30 seconds after the last change to the
 service. (We currently think that a hidden service descriptor
 that's been stable for 30 seconds is worth publishing.)
- If a hidden service sends us an END cell, do not consider
 retrying the connection; just close it. Patch from rovv.
- If we are not using BEGIN\_DIR cells, don't attempt to contact hidden
 service directories if they have no advertised dir port. Bugfix
 on 0.2.0.10-alpha.

**Minor bugfixes (tools):**

- In the torify(1) manpage, mention that tsocks will leak your
 DNS requests.

**Minor bugfixes (controllers):**

- If the controller claimed responsibility for a stream, but that
 stream never finished making its connection, it would live
 forever in circuit\_wait state. Now we close it after SocksTimeout
 seconds. Bugfix on 0.1.2.7-alpha; reported by Mike Perry.
- Make DNS resolved controller events into "CLOSED", not
 "FAILED". Bugfix on 0.1.2.5-alpha. Fix by Robert Hogan. Resolves
 bug 807.
- The control port would close the connection before flushing long
 replies, such as the network consensus, if a QUIT command was issued
 before the reply had completed. Now, the control port flushes all
 pending replies before closing the connection. Also fix a spurious
 warning when a QUIT command is issued after a malformed or rejected
 AUTHENTICATE command, but before the connection was closed. Patch
 by Marcus Griep. Fixes bugs 1015 and 1016.
- Fix a bug that made stream bandwidth get misreported to the
 controller.

**Deprecated and removed features:**

- The old "tor --version --version" command, which would print out
 the subversion "Id" of most of the source files, is now removed. It
 turned out to be less useful than we'd expected, and harder to
 maintain.
- RedirectExits has been removed. It was deprecated since
 0.2.0.3-alpha.
- Finally remove deprecated "EXTENDED\_FORMAT" controller feature. It
 has been called EXTENDED\_EVENTS since 0.1.2.4-alpha.
- Cell pools are now always enabled; --disable-cell-pools is ignored.
- Directory mirrors no longer fetch the v1 directory or
 running-routers files. They are obsolete, and nobody asks for them
 anymore. This is the first step to making v1 authorities obsolete.
- Take out the TestVia config option, since it was a workaround for
 a bug that was fixed in Tor 0.1.1.21.
- Mark RendNodes, RendExcludeNodes, HiddenServiceNodes, and
 HiddenServiceExcludeNodes as obsolete: they never worked properly,
 and nobody seems to be using them. Fixes bug 754. Bugfix on
 0.1.0.1-rc. Patch from Christian Wilms.
- Remove all backward-compatibility code for relays running
 versions of Tor so old that they no longer work at all on the
 Tor network.

**Code simplifications and refactoring:**

- Tool-assisted documentation cleanup. Nearly every function or
 static variable in Tor should have its own documentation now.
- Rename the confusing or\_is\_obsolete field to the more appropriate
 is\_bad\_for\_new\_circs, and move it to or\_connection\_t where it
 belongs.
- Move edge-only flags from connection\_t to edge\_connection\_t: not
 only is this better coding, but on machines of plausible alignment,
 it should save 4-8 bytes per connection\_t. "Every little bit helps."
- Rename ServerDNSAllowBrokenResolvConf to ServerDNSAllowBrokenConfig
 for consistency; keep old option working for backward compatibility.
- Simplify the code for finding connections to use for a circuit.
- Revise the connection\_new functions so that a more typesafe variant
 exists. This will work better with Coverity, and let us find any
 actual mistakes we're making here.
- Refactor unit testing logic so that dmalloc can be used sensibly
 with unit tests to check for memory leaks.
- Move all hidden-service related fields from connection and circuit
 structure to substructures: this way they won't eat so much memory.
- Squeeze 2-5% out of client performance (according to oprofile) by
 improving the implementation of some policy-manipulation functions.
- Change the implementation of ExcludeNodes and ExcludeExitNodes to
 be more efficient. Formerly it was quadratic in the number of
 servers; now it should be linear. Fixes bug 509.
- Save 16-22 bytes per open circuit by moving the n\_addr, n\_port,
 and n\_conn\_id\_digest fields into a separate structure that's
 only needed when the circuit has not yet attached to an n\_conn.
- Optimize out calls to time(NULL) that occur for every IO operation,
 or for every cell. On systems like Windows where time() is a
 slow syscall, this fix will be slightly helpful.

