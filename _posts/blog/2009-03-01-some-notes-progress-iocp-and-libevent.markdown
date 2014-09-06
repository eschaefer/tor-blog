---
layout: post
title: "Some notes on progress with IOCP and Libevent"
permalink: blog/some-notes-progress-iocp-and-libevent
date: 2009-03-01
author: nickm
category: blog
tags: ["developerment", "hacking", "iocp", "libevent"]
---

Hi! I recently wrote up a status report for the progress we're making on hacking Libevent, and I thought I'd post it here too.

BACKGROUND

Tor currently uses Libevent for its high-performance networking calls. Libevent is a software library originally written by Niels Provos (then of UMichigan, now of Google), and now co-developed by Niels Provos and the Tor Project's Nick Mathewson. Its purpose is to provide consistent fast interfaces to various operating systems' mutually incompatible fast networking facilities. Libevent gives applications two basic interfaces to these networking layers: a low-level interface where the application is notified when an operation (like a network read or write) is ready to begin, and a higher-level interface where Libevent itself manages network operations and the application is notified when the network operations are completed.

Existing versions of Libevent have good performance everywhere but on Windows. This is because, while all other remotely common server operating systems provide a fast networking facility suitable for Libevent's low-level interface, Windows's fast ("IOCP") networking calls are only suitable for building a compatible version of Libevent's high-level interface. Additionally, Libevent has not even used these fast Windows calls for its high-level interface, because of certain deficiencies in Libevent's existing implementation (such as lack of full Windows compatibility in all its submodules, lack of thread-safe data structures, and inefficient data structures).

For Windows, using IOCP is not just a performance requirement, but a stability one. Many non-server versions of Windows require all network IO buffers to use "non-paged RAM" (memory that doesn't get swapped to disk), and limit the total amount of RAM that can be used for non-paged storage to an uncomfortably low amount.

So to make Libevent fast and stable on Windows, the tasks are:

1) Make Libevent's overall design flexible enough to support an IOCP-based backend for its high-level interface.

2) Write the IOCP-based backend for Windows.

Additionally, Tor today only uses Libevent's low-level interface because of missing features in the high-level interface, such as support for SSL-based connections and rate-limiting. Also, while the speed-performance of the high-level interface has been fine, it has used unacceptably large amounts of RAM in existing versions of Libevent. So to make Tor take advantage of Libevent's high-level networking capabilities, the tasks are:

3) Revise Libevent's high-level interface to support the features Tor needs.

4) Revise Tor's own networking layer to use Libevent's high-level interface.

Finally, Windows's IOCP performs best when it is run in an aggressively multi-threaded environment, where any one of a pool of worker threads might be notified about any operation's completion on any socket. Moving to a model of this kind is out-of-scope for this report, though Libevent and Tor both plan to move in this direction in the longer term.

STATUS

Items 1 and 3 are mostly done: Nick has re-written large portions of Libevent's underlying high-level ("bufferevents") interface in order to support multiple backends; to run safely in multiple threads; to allow for arbitrary data filters (including SSL and compression) and connection restraints (including rate limiting); and to provide acceptable RAM usage by use of improved data structures. These improvements and others are slated for inclusion in Libevent 2.0, which will represent the largest revision in Libevent since its beginning.

Item 2 is begun and underway. We expect to have the first version of a Windows IOCP-based implementation of the high-level Libevent interfaces completed by the end of March; perhaps sooner. After this point, we'll need to spend a while load-testing the implementation to ensure it behaves correctly and quickly. Additionally, our conference outreach has found us a volunteer domain expert in this area who has offered to help us out with high-load testing.

Item 4 will start once the Libevent interfaces have been tested enough that we are relatively confident of their stability. We will have two options at this point. First, we could make future versions of Tor require Libevent 2.0 everywhere, and replace Tor's buffered network IO code with calls to Libevent's. Alternatively, we could build Tor to use the low-level Libevent interface if built against an older Libevent, but use the high-level interface if built against a more recent one. The former approach would be easier to build, but might create unacceptable dependencies for some package bundlers depending on when the various free operating systems begin to ship Libevent 2. We will work with them to identify which approach is best for our users.

