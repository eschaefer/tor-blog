---
layout: post
title: "Tor 0.2.2.4-alpha released"
permalink: tor-0224-alpha-released
date: 10/12/2009
author: phobos
category: blog
tags: ["alpha release", "bug fixes", "circuit building fixes", "code refactoring", "IP Address changes", "memory leaks", "tinytest framework"]
---

On October 10, we released Tor version 0.2.2.4-alpha.

This release can be found at [https://www.torproject.org/download/](https://www.torproject.org/download/ "https://www.torproject.org/download/")

It contains the following:  
**Major bugfixes:**

- Fix several more asserts in the circuit\_build\_times code, for  
 example one that causes Tor to fail to start once we have  
 accumulated 5000 build times in the state file. Bugfixes on  
 0.2.2.2-alpha; fixes bug 1108.

**New directory authorities:**

- Move moria1 and Tonga to alternate IP addresses.

**Minor features:**

- Log SSL state transitions at debug level during handshake, and  
 include SSL states in error messages. This may help debug future  
 SSL handshake issues.
- Add a new "Handshake" log domain for activities that happen  
 during the TLS handshake.
- Revert to the "June 3 2009" ip-to-country file. The September one  
 seems to have removed most US IP addresses.
- Directory authorities now reject Tor relays with versions less than  
 0.1.2.14. This step cuts out four relays from the current network,  
 none of which are very big.

**Minor bugfixes:**

- Fix a couple of smaller issues with gathering statistics. Bugfixes  
 on 0.2.2.1-alpha.
- Fix two memory leaks in the error case of  
 circuit\_build\_times\_parse\_state. Bugfix on 0.2.2.2-alpha.
- Don't count one-hop circuits when we're estimating how long it  
 takes circuits to build on average. Otherwise we'll set our circuit  
 build timeout lower than we should. Bugfix on 0.2.2.2-alpha.
- Directory authorities no longer change their opinion of, or vote on,  
 whether a router is Running, unless they have themselves been  
 online long enough to have some idea. Bugfix on 0.2.0.6-alpha.  
 Fixes bug 1023.

**Code simplifications and refactoring:**

- Revise our unit tests to use the "tinytest" framework, so we  
 can run tests in their own processes, have smarter setup/teardown  
code, and so on. The unit test code has moved to its own  
 subdirectory, and has been split into multiple modules.

