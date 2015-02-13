---
layout: post
title: "Investigating http proxy performance with Tor"
permalink: investigating-http-proxy-performance-tor
date: 2009-08-19 16:57:17
author: phobos
category: blog
status: closed
tags: ["caching", "faster firefox", "faster tor", "open research", "performance", "polipo", "privoxy", "socks5", "tor browser bundle", "vidalia bundle"]
---

A while ago there was a thread on [OR-TALK](http://archives.seul.org/or/talk/) that devolved into  

> "why does Tor still ship ancient privoxy?"

and  

> "why are you shipping polipo with the Tor Browser Bundle instead of current privoxy?"

For those interested, the thread is here, [http://archives.seul.org/or/talk/Jul-2009/msg00063.html](http://archives.seul.org/or/talk/Jul-2009/msg00063.html "http://archives.seul.org/or/talk/Jul-2009/msg00063.html").

Scott had a good argument for why we should update the bundles to the latest privoxy, and I agree, we should. But then I started thinking about why we needed a proxy at all. Almost all browsers support socks5 direct, isn't that faster than a middleman proxy?

This got me thinking about why polipo is in the TBB, but not the other packages. The TBB "feels faster" when using Tor than using the installed Tor, Vidalia, and Privoxy. However, I couldn't find any actual testing of performance of polipo vs. privoxy vs. socks5 direct. [**read more »**](https://blog.torproject.org/blog/investigating-http-proxy-performance-tor)
