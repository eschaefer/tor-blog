---
layout: post
title: "Some notes on progress with IOCP and Libevent"
permalink: some-notes-progress-iocp-and-libevent
date: 2009-03-01 17:37:33
author: nickm
category: blog
status: closed
tags: ["developerment", "hacking", "iocp", "libevent"]
---

Hi! I recently wrote up a status report for the progress we're making on hacking Libevent, and I thought I'd post it here too.

BACKGROUND

Tor currently uses Libevent for its high-performance networking calls. Libevent is a software library originally written by Niels Provos (then of UMichigan, now of Google), and now co-developed by Niels Provos and the Tor Project's Nick Mathewson. Its purpose is to provide consistent fast interfaces to various operating systems' mutually incompatible fast networking facilities. Libevent gives applications two basic interfaces to these networking layers: a low-level interface where the application is notified when an operation (like a network read or write) is ready to begin, and a higher-level interface where Libevent itself manages network operations and the application is notified when the network operations are completed. [**read more »**](https://blog.torproject.org/blog/some-notes-progress-iocp-and-libevent)
