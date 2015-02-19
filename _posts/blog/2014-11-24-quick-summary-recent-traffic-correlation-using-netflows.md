---
layout: post
title: "Quick Summary of recent traffic correlation using netflows"
permalink: blog/quick-summary-recent-traffic-correlation-using-netflows
date: 2014-11-24 11:58:11
author: phobos
category: blog
comments: closed
tags: ["netflows", "summary", "tor research", "traffic correlation"]
---

Here’s what you need to know about the [recent research study](https://blog.torproject.org/blog/traffic-correlation-using-netflows) on traffic correlation attacks:

While it’s great to see more research on traffic correlation attacks, this is not a new area of research. This is one study on the subject in a controlled environment using one readily available traffic monitoring technology to analyze Tor traffic. The researcher has clarified in the media that it was only 81.4 percent of their experiments not “81 percent of all Tor traffic” as has been reported elsewhere.

The Tor network provides anonymity by routing the user’s information through multiple servers (usually three) so that it is hard to detect the person’s physical location.

Tor protects users by:  
 1) encryption to ensure privacy of data within the Tor network,  
 2) authentication so clients know they're talking to the relays they meant to talk to, and  
 3) signatures to make sure all clients know the same set of relays.

In theory it may be possible to track Tor users by linking up their entry and exit points on the network but it is generally very difficult to do so. The Tor network design, however, does not protect against a targeted attack by a global passive adversary (such as the NSA) intent on figuring out whom to investigate through watching and measuring Tor traffic going into and out of the network and correlating the information on both sides. We encourage you to learn more about [what Tor does](https://www.torproject.org/download/download-easy.html.en#warning) provide.

Tor is used by 2.5 million people a day including the general public, journalists, companies, activists, military, and law enforcement and is a very safe, reliable way to protect your privacy on the Internet.
