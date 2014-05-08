---
layout: post
title: "Tor 0.2.2.2-alpha released"
permalink: tor-0222alpha-released
date: 10/10/2009
author: phobos
category: blog
tags: ["alpha release", "bug fixes", "performance improvements"]
---

On September 21st, we released Tor version 0.2.2.2-alpha.

**Major features:**

- Tor now tracks how long it takes to build client-side circuits  
 over time, and adapts its timeout to local network performance.  
 Since a circuit that takes a long time to build will also provide  
 bad performance, we get significant latency improvements by  
 discarding the slowest 20% of circuits. Specifically, Tor creates  
 circuits more aggressively than usual until it has enough data  
 points for a good timeout estimate. Implements proposal 151.  
 We are especially looking for reports (good and bad) from users with  
 both EDGE and broadband connections that can move from broadband  
 to EDGE and find out if the build-time data in the .tor/state gets  
 reset without loss of Tor usability. You should also see a notice  
 log message telling you that Tor has reset its timeout.
- Directory authorities can now vote on arbitary integer values as  
 part of the consensus process. This is designed to help set  
 network-wide parameters. Implements proposal 167.
- Tor now reads the "circwindow" parameter out of the consensus,  
 and uses that value for its circuit package window rather than the  
 default of 1000 cells. Begins the implementation of proposal 168.

**Major bugfixes:**

- Fix a remotely triggerable memory leak when a consensus document  
 contains more than one signature from the same voter. Bugfix on  
 0.2.0.3-alpha.

**Minor bugfixes:**

- Fix an extremely rare infinite recursion bug that could occur if  
 we tried to log a message after shutting down the log subsystem.  
 Found by Matt Edman. Bugfix on 0.2.0.16-alpha.
- Fix parsing for memory or time units given without a space between  
 the number and the unit. Bugfix on 0.2.2.1-alpha; fixes bug 1076.
- A networkstatus vote must contain exactly one signature. Spec  
 conformance issue. Bugfix on 0.2.0.3-alpha.
- Fix an obscure bug where hidden services on 64-bit big-endian  
 systems might mis-read the timestamp in v3 introduce cells, and  
 refuse to connect back to the client. Discovered by "rotor".  
 Bugfix on 0.2.1.6-alpha.
- We were triggering a CLOCK\_SKEW controller status event whenever  
 we connect via the v2 connection protocol to any relay that has  
 a wrong clock. Instead, we should only inform the controller when  
 it's a trusted authority that claims our clock is wrong. Bugfix  
 on 0.2.0.20-rc; starts to fix bug 1074. Reported by SwissTorExit.
- We were telling the controller about CHECKING\_REACHABILITY and  
 REACHABILITY\_FAILED status events whenever we launch a testing  
 circuit or notice that one has failed. Instead, only tell the  
 controller when we want to inform the user of overall success or  
 overall failure. Bugfix on 0.1.2.6-alpha. Fixes bug 1075. Reported  
 by SwissTorExit.
- Don't warn when we're using a circuit that ends with a node  
 excluded in ExcludeExitNodes, but the circuit is not used to access  
 the outside world. This should help fix bug 1090, but more problems  
 remain. Bugfix on 0.2.1.6-alpha.
- Work around a small memory leak in some versions of OpenSSL that  
 stopped the memory used by the hostname TLS extension from being  
 freed.
- Make our 'torify' script more portable; if we have only one of  
 'torsocks' or 'tsocks' installed, don't complain to the user;  
 and explain our warning about tsocks better.

**Minor features:**

- Add a "getinfo status/accepted-server-descriptor" controller  
 command, which is the recommended way for controllers to learn  
 whether our server descriptor has been successfully received by at  
 least on directory authority. Un-recommend good-server-descriptor  
 getinfo and status events until we have a better design for them.
- Update to the "September 4 2009" ip-to-country file.

