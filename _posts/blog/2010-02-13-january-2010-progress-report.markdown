---
layout: post
title: "January 2010 Progress Report"
permalink: blog/january-2010-progress-report
date: 2010-02-13
author: phobos
category: blog
tags: ["advocacy", "bug fixes", "enhancements", "feature removals", "progress report", "releases", "translations"]
---

 **New releases, new hires, new funding**
On January 19, 2010 we released the latest in the -stable series, Tor 0.2.1.22-stable.
Tor 0.2.1.22 fixes a critical privacy problem in bridge directory authorities -- it would tell you its whole history of bridge descriptors if you make the right directory request. This stable update also rotates two of the seven v3 directory authority keys and locations.
**Directory authority changes** :

- Rotate keys (both v3 identity and relay identity) for moria1 and gabelmoo.

**Major bugfixes:**

- Stop bridge directory authorities from answering dbg-stability.txt directory queries, which would let people fetch a list of all bridge identities they track. Bugfix on 0.2.1.6-alpha.

On January 19, 2010, we released the latest in the -alpha series, Tor 0.2.2.7-alpha.
Tor 0.2.2.7-alpha fixes a huge client-side performance bug, as well as laying the groundwork for further relay-side performance fixes. It also starts cleaning up client behavior with respect to the EntryNodes, ExitNodes, and StrictNodes config options. This release also rotates two directory authority keys, due to a security breach of some of the Torproject servers.
**Directory authority changes:**

- Rotate keys (both v3 identity and relay identity) for moria1 and gabelmoo.

**Major features (performance):**

- We were selecting our guards uniformly at random, and then weighting which of our guards we’d use uniformly at random. This imbalance meant that Tor clients were severely limited on throughput (and probably latency too) by the first hop in their circuit. Now we select guards weighted by currently advertised bandwidth. We also automatically discard guards picked using the old algorithm. Fixes bug 1217; bugfix on 0.2.1.3-alpha. Found by Mike Perry.
- When choosing which cells to relay first, relays can now favor circuits that have been quiet recently, to provide lower latency for low-volume circuits. By default, relays enable or disable this feature based on a setting in the consensus. You can override this default by using the new "CircuitPriorityHalflife" config option. Design and code by Ian Goldberg, Can Tang, and Chris Alexander.
- Add separate per-conn write limiting to go with the per-conn read limiting. We added a global write limit in Tor 0.1.2.5-alpha, but never per-conn write limits.
- New consensus params "bwconnrate" and "bwconnburst" to let us rate-limit client connections as they enter the network. It’s controlled in the consensus so we can turn it on and off for experiments. It’s starting out off. Based on proposal 163.

**Major features (relay selection options):**

- Switch to a StrictNodes config option, rather than the previous "StrictEntryNodes" / "StrictExitNodes" separation that was missing a "StrictExcludeNodes" option.
- If EntryNodes, ExitNodes, ExcludeNodes, or ExcludeExitNodes change during a config reload, mark and discard all our origin circuits. This fix should address edge cases where we change the config options and but then choose a circuit that we created before the change.
- If EntryNodes or ExitNodes are set, be more willing to use an unsuitable (e.g. slow or unstable) circuit. The user asked for it, they get it.
- Make EntryNodes config option much more aggressive even when StrictNodes is not set. Before it would prepend your requested entrynodes to your list of guard nodes, but feel free to use others after that. Now it chooses only from your EntryNodes if any of those are available, and only falls back to others if a) they’re all down and b) StrictNodes is not set.
- Now we refresh your entry guards from EntryNodes at each consensus fetch -- rather than just at startup and then they slowly rot as the network changes.

**Major bugfixes:**

- Stop bridge directory authorities from answering dbg-stability.txt directory queries, which would let people fetch a list of all bridge identities they track. Bugfix on 0.2.1.6-alpha.

**Minor features:**

- Log a notice when we get a new control connection. Now it’s easier for security-conscious users to recognize when a local application is knocking on their controller door. Suggested by bug 1196.
- New config option "CircuitStreamTimeout" to override our internal timeout schedule for how many seconds until we detach a stream from a circuit and try a new circuit. If your network is particularly slow, you might want to set this to a number like 60.
- New controller command "getinfo config-text". It returns the contents that Tor would write if you send it a SAVECONF command, so the controller can write the file to disk itself.
- New options for SafeLogging to allow scrubbing only log messages generated while acting as a relay.
- Ship the bridges spec file in the tarball too.
- Avoid a mad rush at the beginning of each month when each client rotates half of its guards. Instead we spread the rotation out throughout the month, but we still avoid leaving a precise timestamp in the state file about when we first picked the guard. Improves over the behavior introduced in 0.1.2.17.

**Minor bugfixes (compiling):**

- Fix compilation on OS X 10.3, which has a stub mlockall() but hides it. Bugfix on 0.2.2.6-alpha.
- Fix compilation on Solaris by removing support for the DisableAllSwap config option. Solaris doesn’t have an rlimit for mlockall, so we cannot use it safely. Fixes bug 1198; bugfix on 0.2.2.6-alpha.

**Minor bugfixes (crashes):**

- Do not segfault when writing buffer stats when we haven’t observed a single circuit to report about. Found by Fabian Lanze. Bugfix on 0.2.2.1-alpha.
- If we’re in the pathological case where there’s no exit bandwidth but there is non-exit bandwidth, or no guard bandwidth but there is non-guard bandwidth, don’t crash during path selection. Bugfix on 0.2.0.3-alpha.
- Fix an impossible-to-actually-trigger buffer overflow in relay descriptor generation. Bugfix on 0.1.0.15.

**Minor bugfixes (privacy):**

- Fix an instance where a Tor directory mirror might accidentally log the IP address of a misbehaving Tor client. Bugfix on 0.1.0.1-rc.
- Don’t list Windows capabilities in relay descriptors. We never made use of them, and maybe it’s a bad idea to publish them. Bugfix on 0.1.1.8-alpha.

**Minor bugfixes (other):**

- Resolve an edge case in path weighting that could make us misweight our relay selection. Fixes bug 1203; bugfix on 0.0.8rc1.
- Fix statistics on client numbers by country as seen by bridges that were broken in 0.2.2.1-alpha. Also switch to reporting full 24-hour intervals instead of variable 12-to-48-hour intervals.
- After we free an internal connection structure, overwrite it with a different memory value than we use for overwriting a freed internal circuit structure. Should help with debugging. Suggested by bug 1055.
- Update our OpenSSL 0.9.8l fix so that it works with OpenSSL 0.9.8m too.

**Removed features:**

- Remove the HSAuthorityRecordStats option that version 0 hidden service authorities could have used to track statistics of overall hidden service usage.

On January 19, 2010, we released an updated Tor Browser Bundle, version 1.3.1.

- update Firefox to 3.5.7
- update Pidgin to 2.6.5
- update Tor to 0.2.1.22

On January 25, 2010, we released Vidalia 0.2.7.

o- Remove the explicit palette set for the configuration dialog that prevented the dialog from inheriting colors from the user’s current system theme. (Ticket #485. Patch from mkirk.)
- Correct the path to the badge pixmap used in time skew warning messages. (Ticket #537. Patch from mkirk.)
- Fix compilation on Debian GNU/kFreeBSD. Patch from dererk.
- Clean up a couple status event messages related to dangerous port warnings.
- Change the vidalia\_ru.nsh output encoding from KOI8-R to Windows-1251. (Ticket #527)
- Add an option for building an OS X 10.4 compatible binary.

On January 26, 2010, we released an updated -alpha, Tor 0.2.2.8-alpha.
**Major bugfixes:**

- Fix a memory corruption bug on bridges that occured during the inclusion of stats data in extra-info descriptors. Also fix the interface for geoip\_get\_bridge\_stats\* to prevent similar bugs in the future. Diagnosis by Tas, patch by Karsten and Sebastian. Fixes bug 1208; bugfix on 0.2.2.7-alpha.

**Minor bugfixes:**

- Ignore OutboundBindAddress when connecting to localhost. Connections to localhost need to come \_from\_ localhost, or else local servers (like DNS and outgoing HTTP/SOCKS proxies) will often refuse to listen.

**Design, develop, and implement enhancements that make Tor a better tool for users in censored countries.**
Submitted Proposal 169. A backward-compatible change to the Tor connection establishment protocol to avoid the use of TLS renegotiation. In response to others using TLS renegotiation incorrectly, vendors are pulling support for TLS renegotiation. As TLS renegotiation disappears from the Internet, Tor’s use of it will stand out. In order to blend in with the crowd, we need to remove TLS renegotiation from the Tor protocol. The full spec can be found at [http://gitweb.torproject.org//tor.git?a=blob;f=doc/spec/proposals/169-el...](http://gitweb.torproject.org//tor.git?a=blob;f=doc/spec/proposals/169-eliminating-renegotiation.txt;hb=HEAD "http://gitweb.torproject.org//tor.git?a=blob;f=doc/spec/proposals/169-eliminating-renegotiation.txt;hb=HEAD").

**Architecture and technical design docs for Tor enhancements related to blocking-resistance.**
Submitted Proposal 169. A backward-compatible change to the Tor connection establishment protocol to avoid the use of TLS renegotiation. In response to others using TLS renegotiation incorrectly, vendors are pulling support for TLS renegotiation. As TLS renegotiation disappears from the Internet, Tor’s use of it will stand out. In order to blend in with the crowd, we need to remove TLS renegotiation from the Tor protocol. The full spec can be found at [http://gitweb.torproject.org//tor.git?a=blob;f=doc/spec/proposals/169-el...](http://gitweb.torproject.org//tor.git?a=blob;f=doc/spec/proposals/169-eliminating-renegotiation.txt;hb=HEAD "http://gitweb.torproject.org//tor.git?a=blob;f=doc/spec/proposals/169-eliminating-renegotiation.txt;hb=HEAD").

**Hide Tor’s network signature.**
Submitted Proposal 169. A backward-compatible change to the Tor connection establishment protocol to avoid the use of TLS renegotiation. In response to others using TLS renegotiation incorrectly, vendors are pulling support for TLS renegotiation. As TLS renegotiation disappears from the Internet, Tor’s use of it will stand out. In order to blend in with the crowd, we need to remove TLS renegotiation from the Tor protocol. The full spec can be found at [http://gitweb.torproject.org//tor.git?a=blob;f=doc/spec/proposals/169-el...](http://gitweb.torproject.org//tor.git?a=blob;f=doc/spec/proposals/169-eliminating-renegotiation.txt;hb=HEAD "http://gitweb.torproject.org//tor.git?a=blob;f=doc/spec/proposals/169-eliminating-renegotiation.txt;hb=HEAD").

**Grow the Tor network and user base. Outreach.**

- Paul, Karsten, and Roger attended Financial Cryptography and Data Security 2010 Conference. Roger Dingledine presented a paper he had written with Tsuen-Wan Ngan and Dan Wallach on “Building Incentives into Tor”. This paper won Best Paper Award at the conference. Learn more at [http://fc10.ifca.ai/](http://fc10.ifca.ai/ "http://fc10.ifca.ai/").
- Karsten and Roger attended the Workshop on Ethics in Computer Security Research, [http://www.cs.stevens.edu/~spock/wecsr2010/](http://www.cs.stevens.edu/~spock/wecsr2010/ "http://www.cs.stevens.edu/~spock/wecsr2010/"). They presented “A Case Study on Measuring Statistical Data in the Tor Anonymity Network.”
- Andrew attended the Internet Freedom speech by Secretary of State Clinton, [http://www.state.gov/secretary/rm/2010/01/135519.htm](http://www.state.gov/secretary/rm/2010/01/135519.htm "http://www.state.gov/secretary/rm/2010/01/135519.htm").
- Roger and Jacob discussed Tor with the Pirate Party of Sweden.
- Jacob met with NorduNet to discuss their bandwidth authority and how to help Tor grow in the NorduNet, [http://www.nordu.net](http://www.nordu.net "http://www.nordu.net").
- Jacob and Wikileaks people met with policymakers in Iceland to discuss freedom of speech, freedom of press, and that online privacy should be a fundamental right.
- Roger, Karen, and Andrew met with CDT, Internews, and BBG to discuss various topics.
- Andrew was interviewed for 90 minutes by vbs.tv about Tor, online anonymity and privacy, and the increasing usage of Tor as a censorship circumvention tool. vbs.tv will release the interview in 2010.

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**

On January 19, 2010, we released an updated Tor Browser Bundle, version 1.3.1.

- update Firefox to 3.5.7
- update Pidgin to 2.6.5
- update Tor to 0.2.1.22

**Bridge relay and bridge authority work.**
From the Tor 0.2.2.8-alpha release notes;
Fix a memory corruption bug on bridges that occurred during the inclusion of stats data in extra-
info descriptors. Also fix the interface for geoip get bridge stats to prevent similar bugs in the
future. Diagnosis by Tas, patch by Karsten and Sebastian. Fixes bug 1208; bugfix on 0.2.2.7-
alpha.
Roger and Christian defined a roadmap for bridgedb updates, scalability, and bugfixes. The plan can be found at [http://gitweb.torproject.org//bridgedb.git?a=blob\_plain;f=TODO;hb=HEAD](http://gitweb.torproject.org//bridgedb.git?a=blob_plain;f=TODO;hb=HEAD "http://gitweb.torproject.org//bridgedb.git?a=blob\_plain;f=TODO;hb=HEAD")

**Scalability, load balancing, directory overhead, efficiency.**
From the 0.2.2.7-alpha release notes:
We were selecting our guards uniformly at random, and then weighting which of our guards we’duse uniformly at random. This imbalance meant that Tor clients were severely limited on throughput (and probably latency too) by the first hop in their circuit. Now we select guards weighted by currently advertised bandwidth. We also automatically discard guards picked using the old algorithm. Fixes bug 1217; bugfix on 0.2.1.3-alpha. Found by Mike Perry.
When choosing which cells to relay first, relays can now favor circuits that have been quiet recently, to provide lower latency for low-volume circuits. By default, relays enable or disable this feature based on a setting in the consensus. You can override this default by using the new “CircuitPriorityHalflife” configuration option. Design and code by Ian Goldberg, Can Tang, and Chris Alexander.
Mike Perry implemented consensus parameters for the Circuit Build Times constants and found good defaults based on experimentation on a few simulated links. The simulations seem to indicate that tor does really poorly on links with greater than 1 second of latency. Mike wrote up his findings at [http://archives.seul.org/or/dev/Jan-2010/msg00012.html](http://archives.seul.org/or/dev/Jan-2010/msg00012.html "http://archives.seul.org/or/dev/Jan-2010/msg00012.html"). Mike’s work on circuit build times should improve tor client performance as the clients pick new guard nodes and learn better circuit build times.

**More reliable (e.g. split) download mechanism.**
Enhanced get-tor to handle Apple OS X split files.

**Translation work, ultimately a browser-based approach.**
Updated translations via the translation portal for Chinese, Norwegian, Russian, Dutch, French,
Polish, Swedish, Italian, German, Spanish, Burmese, and Turkish languages.

