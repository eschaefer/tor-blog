---
layout: post
title: "Tor 0.2.2.28-beta and 0.2.2.29-beta are out"
permalink: blog/tor-02228-beta-and-02229-beta-are-out
date: 2011-06-24
author: erinn
category: blog
tags: ["alpha releases", "bug fixes", "tor"]
---

 **Changes in version 0.2.2.29-beta - 2011-06-20**
 Tor 0.2.2.29-beta reverts an accidental behavior change for users who
 have bridge lines in their torrc but don't want to use them; gets
 us closer to having the control socket feature working on Debian;
 and fixes a variety of smaller bugs.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Major bugfixes:**

- Revert the UseBridges option to its behavior before 0.2.2.28-beta.
 When we changed the default behavior to "use bridges if any
 are listed in the torrc", we surprised users who had bridges
 in their torrc files but who didn't actually want to use them.
 Partial resolution for bug 3354.

**Privacy fixes:**

- Don't attach new streams to old rendezvous circuits after SIGNAL
 NEWNYM. Previously, we would keep using an existing rendezvous
 circuit if it remained open (i.e. if it were kept open by a
 long-lived stream, or if a new stream were attached to it before
 Tor could notice that it was old and no longer in use). Bugfix on
 0.1.1.15-rc; fixes bug 3375.

**Minor bugfixes:**

- Fix a bug when using ControlSocketsGroupWritable with User. The
 directory's group would be checked against the current group, not
 the configured group. Patch by Jérémy Bobbio. Fixes bug 3393;
 bugfix on 0.2.2.26-beta.
- Make connection\_printf\_to\_buf()'s behaviour sane. Its callers
 expect it to emit a CRLF iff the format string ends with CRLF;
 it actually emitted a CRLF iff (a) the format string ended with
 CRLF or (b) the resulting string was over 1023 characters long or
 (c) the format string did not end with CRLF \*and\* the resulting
 string was 1021 characters long or longer. Bugfix on 0.1.1.9-alpha;
 fixes part of bug 3407.
- Make send\_control\_event\_impl()'s behaviour sane. Its callers
 expect it to always emit a CRLF at the end of the string; it
 might have emitted extra control characters as well. Bugfix on
 0.1.1.9-alpha; fixes another part of bug 3407.
- Make crypto\_rand\_int() check the value of its input correctly.
 Previously, it accepted values up to UINT\_MAX, but could return a
 negative number if given a value above INT\_MAX+1. Found by George
 Kadianakis. Fixes bug 3306; bugfix on 0.2.2pre14.
- Avoid a segfault when reading a malformed circuit build state
 with more than INT\_MAX entries. Found by wanoskarnet. Bugfix on
 0.2.2.4-alpha.
- When asked about a DNS record type we don't support via a
 client DNSPort, reply with NOTIMPL rather than an empty
 reply. Patch by intrigeri. Fixes bug 3369; bugfix on 2.0.1-alpha.
- Fix a rare memory leak during stats writing. Found by coverity.

**Minor features:**

- Update to the June 1 2011 Maxmind GeoLite Country database.

**Code simplifications and refactoring:**

- Remove some dead code as indicated by coverity.
- Remove a few dead assignments during router parsing. Found by
 coverity.
- Add some forgotten return value checks during unit tests. Found
 by coverity.
- Don't use 1-bit wide signed bit fields. Found by coverity.

**Changes in version 0.2.2.28-beta - 2011-06-04**
 Tor 0.2.2.28-beta makes great progress towards a new stable release: we
 fixed a big bug in whether relays stay in the consensus consistently,
 we moved closer to handling bridges and hidden services correctly,
 and we started the process of better handling the dreaded "my Vidalia
 died, and now my Tor demands a password when I try to reconnect to it"
 usability issue.

**Major bugfixes:**

- Don't decide to make a new descriptor when receiving a HUP signal.
 This bug has caused a lot of 0.2.2.x relays to disappear from the
 consensus periodically. Fixes the most common case of triggering
 bug 1810; bugfix on 0.2.2.7-alpha.
- Actually allow nameservers with IPv6 addresses. Fixes bug 2574.
- Don't try to build descriptors if "ORPort auto" is set and we
 don't know our actual ORPort yet. Fix for bug 3216; bugfix on
 0.2.2.26-beta.
- Resolve a crash that occurred when setting BridgeRelay to 1 with
 accounting enabled. Fixes bug 3228; bugfix on 0.2.2.18-alpha.
- Apply circuit timeouts to opened hidden-service-related circuits
 based on the correct start time. Previously, we would apply the
 circuit build timeout based on time since the circuit's creation;
 it was supposed to be applied based on time since the circuit
 entered its current state. Bugfix on 0.0.6; fixes part of bug 1297.
- Use the same circuit timeout for client-side introduction
 circuits as for other four-hop circuits, rather than the timeout
 for single-hop directory-fetch circuits; the shorter timeout may
 have been appropriate with the static circuit build timeout in
 0.2.1.x and earlier, but caused many hidden service access attempts
 to fail with the adaptive CBT introduced in 0.2.2.2-alpha. Bugfix
 on 0.2.2.2-alpha; fixes another part of bug 1297.
- In ticket 2511 we fixed a case where you could use an unconfigured
 bridge if you had configured it as a bridge the last time you ran
 Tor. Now fix another edge case: if you had configured it as a bridge
 but then switched to a different bridge via the controller, you
 would still be willing to use the old one. Bugfix on 0.2.0.1-alpha;
 fixes bug 3321.

**Major features:**

- Add an \_\_OwningControllerProcess configuration option and a
 TAKEOWNERSHIP control-port command. Now a Tor controller can ensure
 that when it exits, Tor will shut down. Implements feature 3049.
- If "UseBridges 1" is set and no bridges are configured, Tor will
 now refuse to build any circuits until some bridges are set.
 If "UseBridges auto" is set, Tor will use bridges if they are
 configured and we are not running as a server, but otherwise will
 make circuits as usual. The new default is "auto". Patch by anonym,
 so the Tails LiveCD can stop automatically revealing you as a Tor
 user on startup.

**Minor bugfixes:**

- Fix warnings from GCC 4.6's "-Wunused-but-set-variable" option.
- Remove a trailing asterisk from "exit-policy/default" in the
 output of the control port command "GETINFO info/names". Bugfix
 on 0.1.2.5-alpha.
- Use a wide type to hold sockets when built for 64-bit Windows builds.
 Fixes bug 3270.
- Warn when the user configures two HiddenServiceDir lines that point
 to the same directory. Bugfix on 0.0.6 (the version introducing
 HiddenServiceDir); fixes bug 3289.
- Remove dead code from rend\_cache\_lookup\_v2\_desc\_as\_dir. Fixes
 part of bug 2748; bugfix on 0.2.0.10-alpha.
- Log malformed requests for rendezvous descriptors as protocol
 warnings, not warnings. Also, use a more informative log message
 in case someone sees it at log level warning without prior
 info-level messages. Fixes the other part of bug 2748; bugfix
 on 0.2.0.10-alpha.
- Clear the table recording the time of the last request for each
 hidden service descriptor from each HS directory on SIGNAL NEWNYM.
 Previously, we would clear our HS descriptor cache on SIGNAL
 NEWNYM, but if we had previously retrieved a descriptor (or tried
 to) from every directory responsible for it, we would refuse to
 fetch it again for up to 15 minutes. Bugfix on 0.2.2.25-alpha;
 fixes bug 3309.
- Fix a log message that said "bits" while displaying a value in
 bytes. Found by wanoskarnet. Fixes bug 3318; bugfix on
 0.2.0.1-alpha.
- When checking for 1024-bit keys, check for 1024 bits, not 128
 bytes. This allows Tor to correctly discard keys of length 1017
 through 1023. Bugfix on 0.0.9pre5.

**Minor features:**

- Relays now log the reason for publishing a new relay descriptor,
 so we have a better chance of hunting down instances of bug 1810.
 Resolves ticket 3252.
- Revise most log messages that refer to nodes by nickname to
 instead use the "$key=nickname at address" format. This should be
 more useful, especially since nicknames are less and less likely
 to be unique. Resolves ticket 3045.
- Log (at info level) when purging pieces of hidden-service-client
 state because of SIGNAL NEWNYM.

**Removed options:**

- Remove undocumented option "-F" from tor-resolve: it hasn't done
 anything since 0.2.1.16-rc.

