---
layout: post
title: "Tor 0.2.2.6-alpha released"
permalink: tor-0226-alpha-released
date: 2009-12-03 00:29:12
author: phobos
category: blog
status: closed
tags: ["alpha release", "android", "enhancements", "new features", "openssl"]
---

On November 19, we released the latest in the Tor alpha series, version 0.2.2.6-alpha. This release lays the groundwork for many upcoming features:  
 support for the new lower-footprint "microdescriptor" directory design,  
 future-proofing our consensus format against new hash functions or  
 other changes, and an Android port. It also makes Tor compatible with  
 the upcoming OpenSSL 0.9.8l release, and fixes a variety of bugs.

It can be downloaded at [https://www.torproject.org/download.html.en](https://www.torproject.org/download.html.en "https://www.torproject.org/download.html.en")

**Major features:**

Directory authorities can now create, vote on, and serve multiple  
 parallel formats of directory data as part of their voting process.  
 Partially implements Proposal 162: "Publish the consensus in  
 multiple flavors".

Directory authorities can now agree on and publish small summaries  
 of router information that clients can use in place of regular  
 server descriptors. This transition will eventually allow clients [**read more »**](https://blog.torproject.org/blog/tor-0226-alpha-released)
