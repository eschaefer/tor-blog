---
layout: post
title: "New Name for Obfsproxy Tor Browser Bundles"
permalink: new-name-obfsproxy-tor-browser-bundles
date: 2013-03-22
author: asn
category: blog
tags: ["bundles", "pluggable transports"]
---

Some days ago we released [new Pluggable Transport Bundles](https://blog.torproject.org/blog/new-pluggable-transports-bundles-02411-alpha-flashproxy-obfsproxy) which aim to  
replace the old Pyobfsproxy/Flashproxy bundles and the even older  
Obfsproxy bundles.

Users are encouraged to upgrade to the new bundles since they support  
all the currently deployed [pluggable transports](https://www.torproject.org/docs/pluggable-transports.html.en) and the latest  
versions of Firefox and Torbutton.

The new bundles also contain the latest release of the Python version  
of [Obfsproxy](https://www.torproject.org/projects/obfsproxy.html.en), which replaces the legacy version that was written in C.

Finally, from now on Obfuscated bundles will be called "Pluggable  
Transport Bundles" and each new version will contain all the deployed  
pluggable transports. Users need to use [http://bridges.torproject.org](http://bridges.torproject.org "http://bridges.torproject.org")  
to get bridges with pluggable transports ("obfuscated/obfsproxy  
bridges") for their bundles.

