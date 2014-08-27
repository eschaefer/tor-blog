---
layout: post
title: "Tor 0.2.0.30 is released as stable"
permalink: tor-02030-released-stable
date: 2008-08-26
author: phobos
category: blog
tags: ["dns proxy", "rate limiting", "stable release", "tor"]
---

Tor 0.2.0.30 is released. A better formatted version of this report can be found [at gmane.org](http://permalink.gmane.org/gmane.network.onion-routing.announce/21)

Tor 0.2.0.30 switches to a more efficient directory distribution design,  
adds features to make connections to the Tor network harder to block,  
allows Tor to act as a DNS proxy, adds separate rate limiting for relayed  
traffic to make it easier for clients to become relays, fixes a variety  
of potential anonymity problems, and includes the usual huge pile of  
other features and bug fixes.

[https://www.torproject.org/download.html](https://www.torproject.org/download.html "https://www.torproject.org/download.html")

Changes in version 0.2.0.30 - 2008-07-15  
 o New v3 directory design:  
 - Tor now uses a new way to learn about and distribute information  
 about the network: the directory authorities vote on a common  
 network status document rather than each publishing their own  
 opinion. Now clients and caches download only one networkstatus  
 document to bootstrap, rather than downloading one for each  
 authority. Clients only download router descriptors listed in  
 the consensus. Implements proposal 101; see doc/spec/dir-spec.txt  
 for details.  
 - Set up moria1, tor26, and dizum as v3 directory authorities  
 in addition to being v2 authorities. Also add three new ones:  
 ides (run by Mike Perry), gabelmoo (run by Karsten Loesing), and  
 dannenberg (run by CCC).  
 - Switch to multi-level keys for directory authorities: now their  
 long-term identity key can be kept offline, and they periodically  
 generate a new signing key. Clients fetch the "key certificates"  
 to keep up to date on the right keys. Add a standalone tool  
 "tor-gencert" to generate key certificates. Implements proposal 103.  
 - Add a new V3AuthUseLegacyKey config option to make it easier for  
 v3 authorities to change their identity keys if another bug like  
 Debian's OpenSSL RNG flaw appears.  
 - Authorities and caches fetch the v2 networkstatus documents  
 less often, now that v3 is recommended.

o Make Tor connections stand out less on the wire:  
 - Use an improved TLS handshake designed by Steven Murdoch in proposal  
 124, as revised in proposal 130. The new handshake is meant to  
 be harder for censors to fingerprint, and it adds the ability  
 to detect certain kinds of man-in-the-middle traffic analysis  
 attacks. The new handshake format includes version negotiation for  
 OR connections as described in proposal 105, which will allow us  
 to improve Tor's link protocol more safely in the future.  
 - Enable encrypted directory connections by default for non-relays,  
 so censor tools that block Tor directory connections based on their  
 plaintext patterns will no longer work. This means Tor works in  
 certain censored countries by default again.  
 - Stop including recognizeable strings in the commonname part of  
 Tor's x509 certificates.

o Implement bridge relays:  
 - Bridge relays (or "bridges" for short) are Tor relays that aren't  
 listed in the main Tor directory. Since there is no complete public  
 list of them, even an ISP that is filtering connections to all the  
 known Tor relays probably won't be able to block all the bridges.  
 See doc/design-paper/blocking.pdf and proposal 125 for details.  
 - New config option BridgeRelay that specifies you want to be a  
 bridge relay rather than a normal relay. When BridgeRelay is set  
 to 1, then a) you cache dir info even if your DirPort ins't on,  
 and b) the default for PublishServerDescriptor is now "bridge"  
 rather than "v2,v3".  
 - New config option "UseBridges 1" for clients that want to use bridge  
 relays instead of ordinary entry guards. Clients then specify  
 bridge relays by adding "Bridge" lines to their config file. Users  
 can learn about a bridge relay either manually through word of  
 mouth, or by one of our rate-limited mechanisms for giving out  
 bridge addresses without letting an attacker easily enumerate them  
 all. See [https://www.torproject.org/bridges](https://www.torproject.org/bridges "https://www.torproject.org/bridges") for details.  
 - Bridge relays behave like clients with respect to time intervals  
 for downloading new v3 consensus documents -- otherwise they  
 stand out. Bridge users now wait until the end of the interval,  
 so their bridge relay will be sure to have a new consensus document.

o Implement bridge directory authorities:  
 - Bridge authorities are like normal directory authorities, except  
 they don't serve a list of known bridges. Therefore users that know  
 a bridge's fingerprint can fetch a relay descriptor for that bridge,  
 including fetching updates e.g. if the bridge changes IP address,  
 yet an attacker can't just fetch a list of all the bridges.  
 - Set up Tonga as the default bridge directory authority.  
 - Bridge authorities refuse to serve bridge descriptors or other  
 bridge information over unencrypted connections (that is, when  
 responding to direct DirPort requests rather than begin\_dir cells.)  
 - Bridge directory authorities do reachability testing on the  
 bridges they know. They provide router status summaries to the  
 controller via "getinfo ns/purpose/bridge", and also dump summaries  
 to a file periodically, so we can keep internal stats about which  
 bridges are functioning.  
 - If bridge users set the UpdateBridgesFromAuthority config option,  
 but the digest they ask for is a 404 on the bridge authority,  
 they fall back to contacting the bridge directly.  
 - Bridges always use begin\_dir to publish their server descriptor to  
 the bridge authority using an anonymous encrypted tunnel.  
 - Early work on a "bridge community" design: if bridge authorities set  
 the BridgePassword config option, they will serve a snapshot of  
 known bridge routerstatuses from their DirPort to anybody who  
 knows that password. Unset by default.  
 - Tor now includes an IP-to-country GeoIP file, so bridge relays can  
 report sanitized aggregated summaries in their extra-info documents  
 privately to the bridge authority, listing which countries are  
 able to reach them. We hope this mechanism will let us learn when  
 certain countries start trying to block bridges.  
 - Bridge authorities write bridge descriptors to disk, so they can  
 reload them after a reboot. They can also export the descriptors  
 to other programs, so we can distribute them to blocked users via  
 the BridgeDB interface, e.g. via [https://bridges.torproject.org/](https://bridges.torproject.org/ "https://bridges.torproject.org/")  
 and bridges torproject.org.

o Tor can be a DNS proxy:  
 - The new client-side DNS proxy feature replaces the need for  
 dns-proxy-tor: Just set "DNSPort 9999", and Tor will now listen  
 for DNS requests on port 9999, use the Tor network to resolve them  
 anonymously, and send the reply back like a regular DNS server.  
 The code still only implements a subset of DNS.  
 - Add a new AutomapHostsOnResolve option: when it is enabled, any  
 resolve request for hosts matching a given pattern causes Tor to  
 generate an internal virtual address mapping for that host. This  
 allows DNSPort to work sensibly with hidden service users. By  
 default, .exit and .onion addresses are remapped; the list of  
 patterns can be reconfigured with AutomapHostsSuffixes.  
 - Add an "-F" option to tor-resolve to force a resolve for a .onion  
 address. Thanks to the AutomapHostsOnResolve option, this is no  
 longer a completely silly thing to do.

o Major features (relay usability):  
 - New config options RelayBandwidthRate and RelayBandwidthBurst:  
 a separate set of token buckets for relayed traffic. Right now  
 relayed traffic is defined as answers to directory requests, and  
 OR connections that don't have any local circuits on them. See  
 proposal 111 for details.  
 - Create listener connections before we setuid to the configured  
 User and Group. Now non-Windows users can choose port values  
 under 1024, start Tor as root, and have Tor bind those ports  
 before it changes to another UID. (Windows users could already  
 pick these ports.)  
 - Added a new ConstrainedSockets config option to set SO\_SNDBUF and  
 SO\_RCVBUF on TCP sockets. Hopefully useful for Tor servers running  
 on "vserver" accounts. Patch from coderman.

o Major features (directory authorities):  
 - Directory authorities track weighted fractional uptime and weighted  
 mean-time-between failures for relays. WFU is suitable for deciding  
 whether a node is "usually up", while MTBF is suitable for deciding  
 whether a node is "likely to stay up." We need both, because  
 "usually up" is a good requirement for guards, while "likely to  
 stay up" is a good requirement for long-lived connections.  
 - Directory authorities use a new formula for selecting which relays  
 to advertise as Guards: they must be in the top 7/8 in terms of  
 how long we have known about them, and above the median of those  
 nodes in terms of weighted fractional uptime.  
 - Directory authorities use a new formula for selecting which relays  
 to advertise as Stable: when we have 4 or more days of data, use  
 median measured MTBF rather than median declared uptime. Implements  
 proposal 108.  
 - Directory authorities accept and serve "extra info" documents for  
 routers. Routers now publish their bandwidth-history lines in the  
 extra-info docs rather than the main descriptor. This step saves  
 60% (!) on compressed router descriptor downloads. Servers upload  
 extra-info docs to any authority that accepts them; directory  
 authorities now allow multiple router descriptors and/or extra  
 info documents to be uploaded in a single go. Authorities, and  
 caches that have been configured to download extra-info documents,  
 download them as needed. Implements proposal 104.  
 - Authorities now list relays who have the same nickname as  
 a different named relay, but list them with a new flag:  
 "Unnamed". Now we can make use of relays that happen to pick the  
 same nickname as a server that registered two years ago and then  
 disappeared. Implements proposal 122.  
 - Store routers in a file called cached-descriptors instead of in  
 cached-routers. Initialize cached-descriptors from cached-routers  
 if the old format is around. The new format allows us to store  
 annotations along with descriptors, to record the time we received  
 each descriptor, its source, and its purpose: currently one of  
 general, controller, or bridge.

o Major features (other):  
 - New config options WarnPlaintextPorts and RejectPlaintextPorts so  
 Tor can warn and/or refuse connections to ports commonly used with  
 vulnerable-plaintext protocols. Currently we warn on ports 23,  
 109, 110, and 143, but we don't reject any. Based on proposal 129  
 by Kevin Bauer and Damon McCoy.  
 - Integrate Karsten Loesing's Google Summer of Code project to publish  
 hidden service descriptors on a set of redundant relays that are a  
 function of the hidden service address. Now we don't have to rely  
 on three central hidden service authorities for publishing and  
 fetching every hidden service descriptor. Implements proposal 114.  
 - Allow tunnelled directory connections to ask for an encrypted  
 "begin\_dir" connection or an anonymized "uses a full Tor circuit"  
 connection independently. Now we can make anonymized begin\_dir  
 connections for (e.g.) more secure hidden service posting and  
 fetching.

o Major bugfixes (crashes and assert failures):  
 - Stop imposing an arbitrary maximum on the number of file descriptors  
 used for busy servers. Bug reported by Olaf Selke; patch from  
 Sebastian Hahn.  
 - Avoid possible failures when generating a directory with routers  
 with over-long versions strings, or too many flags set.  
 - Fix a rare assert error when we're closing one of our threads:  
 use a mutex to protect the list of logs, so we never write to the  
 list as it's being freed. Fixes the very rare bug 575, which is  
 kind of the revenge of bug 222.  
 - Avoid segfault in the case where a badly behaved v2 versioning  
 directory sends a signed networkstatus with missing client-versions.  
 - When we hit an EOF on a log (probably because we're shutting down),  
 don't try to remove the log from the list: just mark it as  
 unusable. (Bulletproofs against bug 222.)

o Major bugfixes (code security fixes):  
 - Detect size overflow in zlib code. Reported by Justin Ferguson and  
 Dan Kaminsky.  
 - Rewrite directory tokenization code to never run off the end of  
 a string. Fixes bug 455. Patch from croup.  
 - Be more paranoid about overwriting sensitive memory on free(),  
 as a defensive programming tactic to ensure forward secrecy.

o Major bugfixes (anonymity fixes):  
 - Reject requests for reverse-dns lookup of names that are in  
 a private address space. Patch from lodger.  
 - Never report that we've used more bandwidth than we're willing to  
 relay: it leaks how much non-relay traffic we're using. Resolves  
 bug 516.  
 - As a client, do not believe any server that tells us that an  
 address maps to an internal address space.  
 - Warn about unsafe ControlPort configurations.  
 - Directory authorities now call routers Fast if their bandwidth is  
 at least 100KB/s, and consider their bandwidth adequate to be a  
 Guard if it is at least 250KB/s, no matter the medians. This fix  
 complements proposal 107.  
 - Directory authorities now never mark more than 2 servers per IP as  
 Valid and Running (or 5 on addresses shared by authorities).  
 Implements proposal 109, by Kevin Bauer and Damon McCoy.  
 - If we're a relay, avoid picking ourselves as an introduction point,  
 a rendezvous point, or as the final hop for internal circuits. Bug  
 reported by taranis and lodger.  
 - Exit relays that are used as a client can now reach themselves  
 using the .exit notation, rather than just launching an infinite  
 pile of circuits. Fixes bug 641. Reported by Sebastian Hahn.  
 - Fix a bug where, when we were choosing the 'end stream reason' to  
 put in our relay end cell that we send to the exit relay, Tor  
 clients on Windows were sometimes sending the wrong 'reason'. The  
 anonymity problem is that exit relays may be able to guess whether  
 the client is running Windows, thus helping partition the anonymity  
 set. Down the road we should stop sending reasons to exit relays,  
 or otherwise prevent future versions of this bug.  
 - Only update guard status (usable / not usable) once we have  
 enough directory information. This was causing us to discard all our  
 guards on startup if we hadn't been running for a few weeks. Fixes  
 bug 448.  
 - When our directory information has been expired for a while, stop  
 being willing to build circuits using it. Fixes bug 401.

o Major bugfixes (peace of mind for relay operators)  
 - Non-exit relays no longer answer "resolve" relay cells, so they  
 can't be induced to do arbitrary DNS requests. (Tor clients already  
 avoid using non-exit relays for resolve cells, but now servers  
 enforce this too.) Fixes bug 619. Patch from lodger.  
 - When we setconf ClientOnly to 1, close any current OR and Dir  
 listeners. Reported by mwenge.

o Major bugfixes (other):  
 - If we only ever used Tor for hidden service lookups or posts, we  
 would stop building circuits and start refusing connections after  
 24 hours, since we falsely believed that Tor was dormant. Reported  
 by nwf.  
 - Add a new \_\_HashedControlSessionPassword option for controllers  
 to use for one-off session password hashes that shouldn't get  
 saved to disk by SAVECONF --- Vidalia users were accumulating a  
 pile of HashedControlPassword lines in their torrc files, one for  
 each time they had restarted Tor and then clicked Save. Make Tor  
 automatically convert "HashedControlPassword" to this new option but  
 only when it's given on the command line. Partial fix for bug 586.  
 - Patch from "Andrew S. Lists" to catch when we contact a directory  
 mirror at IP address X and he says we look like we're coming from  
 IP address X. Otherwise this would screw up our address detection.  
 - Reject uploaded descriptors and extrainfo documents if they're  
 huge. Otherwise we'll cache them all over the network and it'll  
 clog everything up. Suggested by Aljosha Judmayer.  
 - When a hidden service was trying to establish an introduction point,  
 and Tor \*did\* manage to reuse one of the preemptively built  
 circuits, it didn't correctly remember which one it used,  
 so it asked for another one soon after, until there were no  
 more preemptive circuits, at which point it launched one from  
 scratch. Bugfix on 0.0.9.x.

o Rate limiting and load balancing improvements:  
 - When we add data to a write buffer in response to the data on that  
 write buffer getting low because of a flush, do not consider the  
 newly added data as a candidate for immediate flushing, but rather  
 make it wait until the next round of writing. Otherwise, we flush  
 and refill recursively, and a single greedy TLS connection can  
 eat all of our bandwidth.  
 - When counting the number of bytes written on a TLS connection,  
 look at the BIO actually used for writing to the network, not  
 at the BIO used (sometimes) to buffer data for the network.  
 Looking at different BIOs could result in write counts on the  
 order of ULONG\_MAX. Fixes bug 614.  
 - If we change our MaxAdvertisedBandwidth and then reload torrc,  
 Tor won't realize it should publish a new relay descriptor. Fixes  
 bug 688, reported by mfr.  
 - Avoid using too little bandwidth when our clock skips a few seconds.  
 - Choose which bridge to use proportional to its advertised bandwidth,  
 rather than uniformly at random. This should speed up Tor for  
 bridge users. Also do this for people who set StrictEntryNodes.

o Bootstrapping faster and building circuits more intelligently:  
 - Fix bug 660 that was preventing us from knowing that we should  
 preemptively build circuits to handle expected directory requests.  
 - When we're checking if we have enough dir info for each relay  
 to begin establishing circuits, make sure that we actually have  
 the descriptor listed in the consensus, not just any descriptor.  
 - Correctly notify one-hop connections when a circuit build has  
 failed. Possible fix for bug 669. Found by lodger.  
 - Clients now hold circuitless TLS connections open for 1.5 times  
 MaxCircuitDirtiness (15 minutes), since it is likely that they'll  
 rebuild a new circuit over them within that timeframe. Previously,  
 they held them open only for KeepalivePeriod (5 minutes).

o Performance improvements (memory):  
 - Add OpenBSD malloc code from "phk" as an optional malloc  
 replacement on Linux: some glibc libraries do very poorly with  
 Tor's memory allocation patterns. Pass --enable-openbsd-malloc to  
 ./configure to get the replacement malloc code.  
 - Switch our old ring buffer implementation for one more like that  
 used by free Unix kernels. The wasted space in a buffer with 1mb  
 of data will now be more like 8k than 1mb. The new implementation  
 also avoids realloc();realloc(); patterns that can contribute to  
 memory fragmentation.  
 - Change the way that Tor buffers data that it is waiting to write.  
 Instead of queueing data cells in an enormous ring buffer for each  
 client->OR or OR->OR connection, we now queue cells on a separate  
 queue for each circuit. This lets us use less slack memory, and  
 will eventually let us be smarter about prioritizing different kinds  
 of traffic.  
 - Reference-count and share copies of address policy entries; only 5%  
 of them were actually distinct.  
 - Tune parameters for cell pool allocation to minimize amount of  
 RAM overhead used.  
 - Keep unused 4k and 16k buffers on free lists, rather than wasting 8k  
 for every single inactive connection\_t. Free items from the  
 4k/16k-buffer free lists when they haven't been used for a while.  
 - Make memory debugging information describe more about history  
 of cell allocation, so we can help reduce our memory use.  
 - Be even more aggressive about releasing RAM from small  
 empty buffers. Thanks to our free-list code, this shouldn't be too  
 performance-intensive.  
 - Log malloc statistics from mallinfo() on platforms where it exists.  
 - Use memory pools to allocate cells with better speed and memory  
 efficiency, especially on platforms where malloc() is inefficient.  
 - Add a --with-tcmalloc option to the configure script to link  
 against tcmalloc (if present). Does not yet search for non-system  
 include paths.

o Performance improvements (socket management):  
 - Count the number of open sockets separately from the number of  
 active connection\_t objects. This will let us avoid underusing  
 our allocated connection limit.  
 - We no longer use socket pairs to link an edge connection to an  
 anonymous directory connection or a DirPort test connection.  
 Instead, we track the link internally and transfer the data  
 in-process. This saves two sockets per "linked" connection (at the  
 client and at the server), and avoids the nasty Windows socketpair()  
 workaround.  
 - We were leaking a file descriptor if Tor started with a zero-length  
 cached-descriptors file. Patch by "freddy77".

o Performance improvements (CPU use):  
 - Never walk through the list of logs if we know that no log target  
 is interested in a given message.  
 - Call routerlist\_remove\_old\_routers() much less often. This should  
 speed startup, especially on directory caches.  
 - Base64 decoding was actually showing up on our profile when parsing  
 the initial descriptor file; switch to an in-process all-at-once  
 implementation that's about 3.5x times faster than calling out to  
 OpenSSL.  
 - Use a slightly simpler string hashing algorithm (copying Python's  
 instead of Java's) and optimize our digest hashing algorithm to take  
 advantage of 64-bit platforms and to remove some possibly-costly  
 voodoo.  
 - When implementing AES counter mode, update only the portions of the  
 counter buffer that need to change, and don't keep separate  
 network-order and host-order counters on big-endian hosts (where  
 they are the same).  
 - Add an in-place version of aes\_crypt() so that we can avoid doing a  
 needless memcpy() call on each cell payload.  
 - Use Critical Sections rather than Mutexes for synchronizing threads  
 on win32; Mutexes are heavier-weight, and designed for synchronizing  
 between processes.

o Performance improvements (bandwidth use):  
 - Don't try to launch new descriptor downloads quite so often when we  
 already have enough directory information to build circuits.  
 - Version 1 directories are no longer generated in full. Instead,  
 authorities generate and serve "stub" v1 directories that list  
 no servers. This will stop Tor versions 0.1.0.x and earlier from  
 working, but (for security reasons) nobody should be running those  
 versions anyway.  
 - Avoid going directly to the directory authorities even if you're a  
 relay, if you haven't found yourself reachable yet or if you've  
 decided not to advertise your dirport yet. Addresses bug 556.  
 - If we've gone 12 hours since our last bandwidth check, and we  
 estimate we have less than 50KB bandwidth capacity but we could  
 handle more, do another bandwidth test.  
 - Support "If-Modified-Since" when answering HTTP requests for  
 directories, running-routers documents, and v2 and v3 networkstatus  
 documents. (There's no need to support it for router descriptors,  
 since those are downloaded by descriptor digest.)  
 - Stop fetching directory info so aggressively if your DirPort is  
 on but your ORPort is off; stop fetching v2 dir info entirely.  
 You can override these choices with the new FetchDirInfoEarly  
 config option.

o Changed config option behavior (features):  
 - Configuration files now accept C-style strings as values. This  
 helps encode characters not allowed in the current configuration  
 file format, such as newline or #. Addresses bug 557.  
 - Add hidden services and DNSPorts to the list of things that make  
 Tor accept that it has running ports. Change starting Tor with no  
 ports from a fatal error to a warning; we might change it back if  
 this turns out to confuse anybody. Fixes bug 579.  
 - Make PublishServerDescriptor default to 1, so the default doesn't  
 have to change as we invent new directory protocol versions.  
 - Allow people to say PreferTunnelledDirConns rather than  
 PreferTunneledDirConns, for those alternate-spellers out there.  
 - Raise the default BandwidthRate/BandwidthBurst to 5MB/10MB, to  
 accommodate the growing number of servers that use the default  
 and are reaching it.  
 - Make it possible to enable HashedControlPassword and  
 CookieAuthentication at the same time.  
 - When a TrackHostExits-chosen exit fails too many times in a row,  
 stop using it. Fixes bug 437.

o Changed config option behavior (bugfixes):  
 - Do not read the configuration file when we've only been told to  
 generate a password hash. Fixes bug 643. Bugfix on 0.0.9pre5. Fix  
 based on patch from Sebastian Hahn.  
 - Actually validate the options passed to AuthDirReject,  
 AuthDirInvalid, AuthDirBadDir, and AuthDirBadExit.  
 - Make "ClientOnly 1" config option disable directory ports too.  
 - Don't stop fetching descriptors when FetchUselessDescriptors is  
 set, even if we stop asking for circuits. Bug reported by tup  
 and ioerror.  
 - Servers used to decline to publish their DirPort if their  
 BandwidthRate or MaxAdvertisedBandwidth were below a threshold. Now  
 they look only at BandwidthRate and RelayBandwidthRate.  
 - Treat "2gb" when given in torrc for a bandwidth as meaning 2gb,  
 minus 1 byte: the actual maximum declared bandwidth.  
 - Make "TrackHostExits ." actually work. Bugfix on 0.1.0.x.  
 - Make the NodeFamilies config option work. (Reported by  
 lodger -- it has never actually worked, even though we added it  
 in Oct 2004.)  
 - If Tor is invoked from something that isn't a shell (e.g. Vidalia),  
 now we expand "-f ~/.tor/torrc" correctly. Suggested by Matt Edman.

o New config options:  
 - New configuration options AuthDirMaxServersPerAddr and  
 AuthDirMaxServersperAuthAddr to override default maximum number  
 of servers allowed on a single IP address. This is important for  
 running a test network on a single host.  
 - Three new config options (AlternateDirAuthority,  
 AlternateBridgeAuthority, and AlternateHSAuthority) that let the  
 user selectively replace the default directory authorities by type,  
 rather than the all-or-nothing replacement that DirServer offers.  
 - New config options AuthDirBadDir and AuthDirListBadDirs for  
 authorities to mark certain relays as "bad directories" in the  
 networkstatus documents. Also supports the "!baddir" directive in  
 the approved-routers file.  
 - New config option V2AuthoritativeDirectory that all v2 directory  
 authorities must set. This lets v3 authorities choose not to serve  
 v2 directory information.

o Minor features (other):  
 - When we're not serving v2 directory information, there is no reason  
 to actually keep any around. Remove the obsolete files and directory  
 on startup if they are very old and we aren't going to serve them.  
 - When we negotiate a v2 link-layer connection (not yet implemented),  
 accept RELAY\_EARLY cells and turn them into RELAY cells if we've  
 negotiated a v1 connection for their next step. Initial steps for  
 proposal 110.  
 - When we have no consensus, check FallbackNetworkstatusFile (defaults  
 to $PREFIX/share/tor/fallback-consensus) for a consensus. This way  
 we can start out knowing some directory caches. We don't ship with  
 a fallback consensus by default though, because it was making  
 bootstrapping take too long while we tried many down relays.  
 - Authorities send back an X-Descriptor-Not-New header in response to  
 an accepted-but-discarded descriptor upload. Partially implements  
 fix for bug 535.  
 - If we find a cached-routers file that's been sitting around for more  
 than 28 days unmodified, then most likely it's a leftover from  
 when we upgraded to 0.2.0.8-alpha. Remove it. It has no good  
 routers anyway.  
 - When we (as a cache) download a descriptor because it was listed  
 in a consensus, remember when the consensus was supposed to expire,  
 and don't expire the descriptor until then.  
 - Optionally (if built with -DEXPORTMALLINFO) export the output  
 of mallinfo via http, as tor/mallinfo.txt. Only accessible  
 from localhost.  
 - Tag every guard node in our state file with the version that  
 we believe added it, or with our own version if we add it. This way,  
 if a user temporarily runs an old version of Tor and then switches  
 back to a new one, she doesn't automatically lose her guards.  
 - When somebody requests a list of statuses or servers, and we have  
 none of those, return a 404 rather than an empty 200.  
 - Merge in some (as-yet-unused) IPv6 address manipulation code. (Patch  
 from croup.)  
 - Add an HSAuthorityRecordStats option that hidden service authorities  
 can use to track statistics of overall hidden service usage without  
 logging information that would be as useful to an attacker.  
 - Allow multiple HiddenServicePort directives with the same virtual  
 port; when they occur, the user is sent round-robin to one  
 of the target ports chosen at random. Partially fixes bug 393 by  
 adding limited ad-hoc round-robining.  
 - Revamp file-writing logic so we don't need to have the entire  
 contents of a file in memory at once before we write to disk. Tor,  
 meet stdio.

o Minor bugfixes (other):  
 - Alter the code that tries to recover from unhandled write  
 errors, to not try to flush onto a socket that's given us  
 unhandled errors.  
 - Directory mirrors no longer include a guess at the client's IP  
 address if the connection appears to be coming from the same /24  
 network; it was producing too many wrong guesses.  
 - If we're trying to flush the last bytes on a connection (for  
 example, when answering a directory request), reset the  
 time-to-give-up timeout every time we manage to write something  
 on the socket.  
 - Reject router descriptors with out-of-range bandwidthcapacity or  
 bandwidthburst values.  
 - If we can't expand our list of entry guards (e.g. because we're  
 using bridges or we have StrictEntryNodes set), don't mark relays  
 down when they fail a directory request. Otherwise we're too quick  
 to mark all our entry points down.  
 - Authorities no longer send back "400 you're unreachable please fix  
 it" errors to Tor servers that aren't online all the time. We're  
 supposed to tolerate these servers now.  
 - Let directory authorities startup even when they can't generate  
 a descriptor immediately, e.g. because they don't know their  
 address.  
 - Correctly enforce that elements of directory objects do not appear  
 more often than they are allowed to appear.  
 - Stop allowing hibernating servers to be "stable" or "fast".  
 - On Windows, we were preventing other processes from reading  
 cached-routers while Tor was running. (Reported by janbar)  
 - Check return values from pthread\_mutex functions.  
 - When opening /dev/null in finish\_daemonize(), do not pass the  
 O\_CREAT flag. Fortify was complaining, and correctly so. Fixes  
 bug 742; fix from Michael Scherer. Bugfix on 0.0.2pre19.

o Controller features:  
 - The GETCONF command now escapes and quotes configuration values  
 that don't otherwise fit into the torrc file.  
 - The SETCONF command now handles quoted values correctly.  
 - Add "GETINFO/desc-annotations/id/≤OR digest>" so controllers can  
 ask about source, timestamp of arrival, purpose, etc. We need  
 something like this to help Vidalia not do GeoIP lookups on bridge  
 addresses.  
 - Allow multiple HashedControlPassword config lines, to support  
 multiple controller passwords.  
 - Accept LF instead of CRLF on controller, since some software has a  
 hard time generating real Internet newlines.  
 - Add GETINFO values for the server status events  
 "REACHABILITY\_SUCCEEDED" and "GOOD\_SERVER\_DESCRIPTOR". Patch from  
 Robert Hogan.  
 - There is now an ugly, temporary "desc/all-recent-extrainfo-hack"  
 GETINFO for Torstat to use until it can switch to using extrainfos.  
 - New config option CookieAuthFile to choose a new location for the  
 cookie authentication file, and config option  
 CookieAuthFileGroupReadable to make it group-readable.  
 - Add a SOURCE\_ADDR field to STREAM NEW events so that controllers can  
 match requests to applications. Patch from Robert Hogan.  
 - Add a RESOLVE command to launch hostname lookups. Original patch  
 from Robert Hogan.  
 - Add GETINFO status/enough-dir-info to let controllers tell whether  
 Tor has downloaded sufficient directory information. Patch from Tup.  
 - You can now use the ControlSocket option to tell Tor to listen for  
 controller connections on Unix domain sockets on systems that  
 support them. Patch from Peter Palfrader.  
 - New "GETINFO address-mappings/\*" command to get address mappings  
 with expiry information. "addr-mappings/\*" is now deprecated.  
 Patch from Tup.  
 - Add a new config option \_\_DisablePredictedCircuits designed for  
 use by the controller, when we don't want Tor to build any circuits  
 preemptively.  
 - Let the controller specify HOP=%d as an argument to ATTACHSTREAM,  
 so we can exit from the middle of the circuit.  
 - Implement "getinfo status/circuit-established".  
 - Implement "getinfo status/version/..." so a controller can tell  
 whether the current version is recommended, and whether any versions  
 are good, and how many authorities agree. Patch from "shibz".  
 - Controllers should now specify cache=no or cache=yes when using  
 the +POSTDESCRIPTOR command.  
 - Add a "PURPOSE=" argument to "STREAM NEW" events, as suggested by  
 Robert Hogan. Fixes the first part of bug 681.  
 - When reporting clock skew, and we know that the clock is \_at least  
 as skewed\_ as some value, but we don't know the actual value,  
 report the value as a "minimum skew."

o Controller bugfixes:  
 - Generate "STATUS\_SERVER" events rather than misspelled  
 "STATUS\_SEVER" events. Caught by mwenge.  
 - Reject controller commands over 1MB in length, so rogue  
 processes can't run us out of memory.  
 - Change the behavior of "getinfo status/good-server-descriptor"  
 so it doesn't return failure when any authority disappears.  
 - Send NAMESERVER\_STATUS messages for a single failed nameserver  
 correctly.  
 - When the DANGEROUS\_VERSION controller status event told us we're  
 running an obsolete version, it used the string "OLD" to describe  
 it. Yet the "getinfo" interface used the string "OBSOLETE". Now use  
 "OBSOLETE" in both cases.  
 - Respond to INT and TERM SIGNAL commands before we execute the  
 signal, in case the signal shuts us down. We had a patch in  
 0.1.2.1-alpha that tried to do this by queueing the response on  
 the connection's buffer before shutting down, but that really  
 isn't the same thing at all. Bug located by Matt Edman.  
 - Provide DNS expiry times in GMT, not in local time. For backward  
 compatibility, ADDRMAP events only provide GMT expiry in an extended  
 field. "GETINFO address-mappings" always does the right thing.  
 - Use CRLF line endings properly in NS events.  
 - Make 'getinfo fingerprint' return a 551 error if we're not a  
 server, so we match what the control spec claims we do. Reported  
 by daejees.  
 - Fix a typo in an error message when extendcircuit fails that  
 caused us to not follow the \r\n-based delimiter protocol. Reported  
 by daejees.  
 - When tunneling an encrypted directory connection, and its first  
 circuit fails, do not leave it unattached and ask the controller  
 to deal. Fixes the second part of bug 681.  
 - Treat some 403 responses from directory servers as INFO rather than  
 WARN-severity events.

o Portability / building / compiling:  
 - When building with --enable-gcc-warnings, check for whether Apple's  
 warning "-Wshorten-64-to-32" is available.  
 - Support compilation to target iPhone; patch from cjacker huang.  
 To build for iPhone, pass the --enable-iphone option to configure.  
 - Detect non-ASCII platforms (if any still exist) and refuse to  
 build there: some of our code assumes that 'A' is 65 and so on.  
 - Clear up some MIPSPro compiler warnings.  
 - Make autoconf search for libevent, openssl, and zlib consistently.  
 - Update deprecated macros in configure.in.  
 - When warning about missing headers, tell the user to let us  
 know if the compile succeeds anyway, so we can downgrade the  
 warning.  
 - Include the current subversion revision as part of the version  
 string: either fetch it directly if we're in an SVN checkout, do  
 some magic to guess it if we're in an SVK checkout, or use  
 the last-detected version if we're building from a .tar.gz.  
 Use this version consistently in log messages.  
 - Correctly report platform name on Windows 95 OSR2 and Windows 98 SE.  
 - Read resolv.conf files correctly on platforms where read() returns  
 partial results on small file reads.  
 - Build without verbose warnings even on gcc 4.2 and 4.3.  
 - On Windows, correctly detect errors when listing the contents of  
 a directory. Fix from lodger.  
 - Run 'make test' as part of 'make dist', so we stop releasing so  
 many development snapshots that fail their unit tests.  
 - Add support to detect Libevent versions in the 1.4.x series  
 on mingw.  
 - Add command-line arguments to unit-test executable so that we can  
 invoke any chosen test from the command line rather than having  
 to run the whole test suite at once; and so that we can turn on  
 logging for the unit tests.  
 - Do not automatically run configure from autogen.sh. This  
 non-standard behavior tended to annoy people who have built other  
 programs.  
 - Fix a macro/CPP interaction that was confusing some compilers:  
 some GCCs don't like #if/#endif pairs inside macro arguments.  
 Fixes bug 707.  
 - Fix macro collision between OpenSSL 0.9.8h and Windows headers.  
 Fixes bug 704; fix from Steven Murdoch.  
 - Correctly detect transparent proxy support on Linux hosts that  
 require in.h to be included before netfilter\_ipv4.h. Patch  
 from coderman.

o Logging improvements:  
 - When we haven't had any application requests lately, don't bother  
 logging that we have expired a bunch of descriptors.  
 - When attempting to open a logfile fails, tell us why.  
 - Only log guard node status when guard node status has changed.  
 - Downgrade the 3 most common "INFO" messages to "DEBUG". This will  
 make "INFO" 75% less verbose.  
 - When SafeLogging is disabled, log addresses along with all TLS  
 errors.  
 - Report TLS "zero return" case as a "clean close" and "IO error"  
 as a "close". Stop calling closes "unexpected closes": existing  
 Tors don't use SSL\_close(), so having a connection close without  
 the TLS shutdown handshake is hardly unexpected.  
 - When we receive a consensus from the future, warn about skew.  
 - Make "not enough dir info yet" warnings describe \*why\* Tor feels  
 it doesn't have enough directory info yet.  
 - On the USR1 signal, when dmalloc is in use, log the top 10 memory  
 consumers. (We already do this on HUP.)  
 - Give more descriptive well-formedness errors for out-of-range  
 hidden service descriptor/protocol versions.  
 - Stop recommending that every server operator send mail to tor-ops.  
 Resolves bug 597. Bugfix on 0.1.2.x.  
 - Improve skew reporting: try to give the user a better log message  
 about how skewed they are, and how much this matters.  
 - New --quiet command-line option to suppress the default console log.  
 Good in combination with --hash-password.  
 - Don't complain that "your server has not managed to confirm that its  
 ports are reachable" if we haven't been able to build any circuits  
 yet.  
 - Detect the reason for failing to mmap a descriptor file we just  
 wrote, and give a more useful log message. Fixes bug 533.  
 - Always prepend "Bug: " to any log message about a bug.  
 - When dumping memory usage, list bytes used in buffer memory  
 free-lists.  
 - When running with dmalloc, dump more stats on hup and on exit.  
 - Put a platform string (e.g. "Linux i686") in the startup log  
 message, so when people paste just their logs, we know if it's  
 OpenBSD or Windows or what.  
 - When logging memory usage, break down memory used in buffers by  
 buffer type.  
 - When we are reporting the DirServer line we just parsed, we were  
 logging the second stanza of the key fingerprint, not the first.  
 - Even though Windows is equally happy with / and \ as path separators,  
 try to use \ consistently on Windows and / consistently on Unix: it  
 makes the log messages nicer.  
 - On OSX, stop warning the user that kqueue support in libevent is  
 "experimental", since it seems to have worked fine for ages.

o Contributed scripts and tools:  
 - Update linux-tor-prio.sh script to allow QoS based on the uid of  
 the Tor process. Patch from Marco Bonetti with tweaks from Mike  
 Perry.  
 - Include the "tor-ctrl.sh" bash script by Stefan Behte to provide  
 Unix users an easy way to script their Tor process (e.g. by  
 adjusting bandwidth based on the time of the day).  
 - In the exitlist script, only consider the most recently published  
 server descriptor for each server. Also, when the user requests  
 a list of servers that \_reject\_ connections to a given address,  
 explicitly exclude the IPs that also have servers that accept  
 connections to that address. Resolves bug 405.  
 - Include a new contrib/tor-exit-notice.html file that exit relay  
 operators can put on their website to help reduce abuse queries.

o Newly deprecated features:  
 - The status/version/num-versioning and status/version/num-concurring  
 GETINFO controller options are no longer useful in the v3 directory  
 protocol: treat them as deprecated, and warn when they're used.  
 - The RedirectExits config option is now deprecated.

o Removed features:  
 - Drop the old code to choke directory connections when the  
 corresponding OR connections got full: thanks to the cell queue  
 feature, OR conns don't get full any more.  
 - Remove the old "dns worker" server DNS code: it hasn't been default  
 since 0.1.2.2-alpha, and all the servers are using the new  
 eventdns code.  
 - Remove the code to generate the oldest (v1) directory format.  
 - Remove support for the old bw\_accounting file: we've been storing  
 bandwidth accounting information in the state file since  
 0.1.2.5-alpha. This may result in bandwidth accounting errors  
 if you try to upgrade from 0.1.1.x or earlier, or if you try to  
 downgrade to 0.1.1.x or earlier.  
 - Drop support for OpenSSL version 0.9.6. Just about nobody was using  
 it, it had no AES, and it hasn't seen any security patches since  
 2004.  
 - Stop overloading the circuit\_t.onionskin field for both "onionskin  
 from a CREATE cell that we are waiting for a cpuworker to be  
 assigned" and "onionskin from an EXTEND cell that we are going to  
 send to an OR as soon as we are connected". Might help with bug 600.  
 - Remove the tor\_strpartition() function: its logic was confused,  
 and it was only used for one thing that could be implemented far  
 more easily.  
 - Remove the contrib scripts ExerciseServer.py, PathDemo.py,  
 and TorControl.py, as they use the old v0 controller protocol,  
 and are obsoleted by TorFlow anyway.  
 - Drop support for v1 rendezvous descriptors, since we never used  
 them anyway, and the code has probably rotted by now. Based on  
 patch from Karsten Loesing.  
 - Stop allowing address masks that do not correspond to bit prefixes.  
 We have warned about these for a really long time; now it's time  
 to reject them. (Patch from croup.)  
 - Remove an optimization in the AES counter-mode code that assumed  
 that the counter never exceeded 2^68. When the counter can be set  
 arbitrarily as an IV (as it is by Karsten's new hidden services  
 code), this assumption no longer holds.  
 - Disable the SETROUTERPURPOSE controller command: it is now  
 obsolete.

