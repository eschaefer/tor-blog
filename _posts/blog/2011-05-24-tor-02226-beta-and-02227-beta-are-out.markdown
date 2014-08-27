---
layout: post
title: "Tor 0.2.2.26-beta and 0.2.2.27-beta are out"
permalink: tor-02226-beta-and-02227-beta-are-out
date: 2011-05-24
author: erinn
category: blog
tags: ["alpha releases", "tor"]
---

 **Changes in version 0.2.2.27-beta - 2011-05-18**  
 Tor 0.2.2.27-beta fixes a bridge-related stability bug in the previous  
 release, and also adds a few more general bugfixes.

**Major bugfixes:**

- Fix a crash bug when changing bridges in a running Tor process.  
 Fixes bug 3213; bugfix on 0.2.2.26-beta.
- When the controller configures a new bridge, don't wait 10 to 60  
 seconds before trying to fetch its descriptor. Bugfix on  
 0.2.0.3-alpha; fixes bug 3198 (suggested by 2355).

**Minor bugfixes:**

- Require that onion keys have exponent 65537 in microdescriptors too.  
 Fixes more of bug 3207; bugfix on 0.2.2.26-beta.
- Tor used to limit HttpProxyAuthenticator values to 48 characters.  
 Changed the limit to 512 characters by removing base64 newlines.  
 Fixes bug 2752. Fix by Michael Yakubovich.
- When a client starts or stops using bridges, never use a circuit  
 that was built before the configuration change. This behavior could  
 put at risk a user who uses bridges to ensure that her traffic  
 only goes to the chosen addresses. Bugfix on 0.2.0.3-alpha; fixes  
 bug 3200.

**Changes in version 0.2.2.26-beta - 2011-05-17**  
 Tor 0.2.2.26-beta fixes a variety of potential privacy problems. It  
 also introduces a new "socksport auto" approach that should make it  
 easier to run multiple Tors on the same system, and does a lot of  
 cleanup to get us closer to a release candidate.

**Security/privacy fixes:**

- Replace all potentially sensitive memory comparison operations  
 with versions whose runtime does not depend on the data being  
 compared. This will help resist a class of attacks where an  
 adversary can use variations in timing information to learn  
 sensitive data. Fix for one case of bug 3122. (Safe memcmp  
 implementation by Robert Ransom based partially on code by DJB.)
- When receiving a hidden service descriptor, check that it is for  
 the hidden service we wanted. Previously, Tor would store any  
 hidden service descriptors that a directory gave it, whether it  
 wanted them or not. This wouldn't have let an attacker impersonate  
 a hidden service, but it did let directories pre-seed a client  
 with descriptors that it didn't want. Bugfix on 0.0.6.
- On SIGHUP, do not clear out all TrackHostExits mappings, client  
 DNS cache entries, and virtual address mappings: that's what  
 NEWNYM is for. Fixes bug 1345; bugfix on 0.1.0.1-rc.

**Major features:**

- The options SocksPort, ControlPort, and so on now all accept a  
 value "auto" that opens a socket on an OS-selected port. A  
 new ControlPortWriteToFile option tells Tor to write its  
 actual control port or ports to a chosen file. If the option  
 ControlPortFileGroupReadable is set, the file is created as  
 group-readable. Now users can run two Tor clients on the same  
 system without needing to manually mess with parameters. Resolves  
 part of ticket 3076.
- Set SO\_REUSEADDR on all sockets, not just listeners. This should  
 help busy exit nodes avoid running out of useable ports just  
 because all the ports have been used in the near past. Resolves  
 issue 2850.

**Minor features:**

- New "GETINFO net/listeners/(type)" controller command to return  
 a list of addresses and ports that are bound for listeners for a  
 given connection type. This is useful when the user has configured  
 "SocksPort auto" and the controller needs to know which port got  
 chosen. Resolves another part of ticket 3076.
- Add a new ControlSocketsGroupWritable configuration option: when  
 it is turned on, ControlSockets are group-writeable by the default  
 group of the current user. Patch by Jérémy Bobbio; implements  
 ticket 2972.
- Tor now refuses to create a ControlSocket in a directory that is  
 world-readable (or group-readable if ControlSocketsGroupWritable  
 is 0). This is necessary because some operating systems do not  
 enforce permissions on an AF\_UNIX sockets. Permissions on the  
 directory holding the socket, however, seems to work everywhere.
- Rate-limit a warning about failures to download v2 networkstatus  
 documents. Resolves part of bug 1352.
- Backport code from 0.2.3.x that allows directory authorities to  
 clean their microdescriptor caches. Needed to resolve bug 2230.
- When an HTTPS proxy reports "403 Forbidden", we now explain  
 what it means rather than calling it an unexpected status code.  
 Closes bug 2503. Patch from Michael Yakubovich.
- Update to the May 1 2011 Maxmind GeoLite Country database.

**Minor bugfixes:**

- Authorities now clean their microdesc cache periodically and when  
 reading from disk initially, not only when adding new descriptors.  
 This prevents a bug where we could lose microdescriptors. Bugfix  
 on 0.2.2.6-alpha. 2230
- Do not crash when our configuration file becomes unreadable, for  
 example due to a permissions change, between when we start up  
 and when a controller calls SAVECONF. Fixes bug 3135; bugfix  
 on 0.0.9pre6.
- Avoid a bug that would keep us from replacing a microdescriptor  
 cache on Windows. (We would try to replace the file while still  
 holding it open. That's fine on Unix, but Windows doesn't let us  
 do that.) Bugfix on 0.2.2.6-alpha; bug found by wanoskarnet.
- Add missing explanations for the authority-related torrc options  
 RephistTrackTime, BridgePassword, and V3AuthUseLegacyKey in the  
 man page. Resolves issue 2379.
- As an authority, do not upload our own vote or signature set to  
 ourself. It would tell us nothing new, and as of 0.2.2.24-alpha,  
 it would get flagged as a duplicate. Resolves bug 3026.
- Accept hidden service descriptors if we think we might be a hidden  
 service directory, regardless of what our consensus says. This  
 helps robustness, since clients and hidden services can sometimes  
 have a more up-to-date view of the network consensus than we do,  
 and if they think that the directory authorities list us a HSDir,  
 we might actually be one. Related to bug 2732; bugfix on  
 0.2.0.10-alpha.
- When a controller changes TrackHostExits, remove mappings for  
 hosts that should no longer have their exits tracked. Bugfix on  
 0.1.0.1-rc.
- When a controller changes VirtualAddrNetwork, remove any mappings  
 for hosts that were automapped to the old network. Bugfix on  
 0.1.1.19-rc.
- When a controller changes one of the AutomapHosts\* options, remove  
 any mappings for hosts that should no longer be automapped. Bugfix  
 on 0.2.0.1-alpha.
- Do not reset the bridge descriptor download status every time we  
 re-parse our configuration or get a configuration change. Fixes  
 bug 3019; bugfix on 0.2.0.3-alpha.

**Minor bugfixes (code cleanup):**

- When loading the microdesc journal, remember its current size.  
 In 0.2.2, this helps prevent the microdesc journal from growing  
 without limit on authorities (who are the only ones to use it in  
 0.2.2). Fixes a part of bug 2230; bugfix on 0.2.2.6-alpha.  
 Fix posted by "cypherpunks."
- The microdesc journal is supposed to get rebuilt only if it is  
 at least \_half\_ the length of the store, not \_twice\_ the length  
 of the store. Bugfix on 0.2.2.6-alpha; fixes part of bug 2230.
- Fix a potential null-pointer dereference while computing a  
 consensus. Bugfix on tor-0.2.0.3-alpha, found with the help of  
 clang's analyzer.
- Avoid a possible null-pointer dereference when rebuilding the mdesc  
 cache without actually having any descriptors to cache. Bugfix on  
 0.2.2.6-alpha. Issue discovered using clang's static analyzer.
- If we fail to compute the identity digest of a v3 legacy keypair,  
 warn, and don't use a buffer-full of junk instead. Bugfix on  
 0.2.1.1-alpha; fixes bug 3106.
- Resolve an untriggerable issue in smartlist\_string\_num\_isin(),  
 where if the function had ever in the future been used to check  
 for the presence of a too-large number, it would have given an  
 incorrect result. (Fortunately, we only used it for 16-bit  
 values.) Fixes bug 3175; bugfix on 0.1.0.1-rc.
- Require that introduction point keys and onion handshake keys  
 have a public exponent of 65537. Starts to fix bug 3207; bugfix  
 on 0.2.0.10-alpha.

**Removed features:**

- Caches no longer download and serve v2 networkstatus documents  
 unless FetchV2Networkstatus flag is set: these documents haven't  
 haven't been used by clients or relays since 0.2.0.x. Resolves  
 bug 3022.

