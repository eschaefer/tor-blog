---
layout: post
title: "Politically motivated censorship in Bethlehem, Palestine"
permalink: politically-motivated-censorship-bethlehem-palestine
date: 2012-04-23 16:34:57
author: art
category: blog
status: closed
tags: ["censorship", "ooni", "ooniprobe", "Palestine"]
---

The internet agency Hadara is restricting access to certain content for users in Bethlehem, Palestine. The content of the websites in question appears to be in support of Muhammad Dahlan, the former leader of Fatah.

The Hadara network in Palestine is using a transparent HTTP proxy to inspect content and to censor the content of specific sites. A transparent HTTP proxy intercepts all of the customer's access attempts, technically the HTTP requests being done on the network by the customer's browser, and then the proxy makes requests in place of the client. Sometimes this is a good thing, especially on congested networks or very expensive network connections. This is useful because the proxy can serve the cached version of the requested object if it already has the most up to date version of the requested page; therefore an ISP may minimize the amount of traffic that needs to leave it's network. Sometimes it's a bad thing, such as when the ISP censors access to an otherwise normally available resource.

We've found that the Hadara transparent HTTP proxy is not being used simply to decrease webpage loading times or to reduce costs. It is also being used to censor access and to block content. The [Open Observatory of Network Interference](http://ooni.nu) ([OONI](http://ooni.nu/)), did a scan of over 1 million websites to understand which ones where being censored and which were freely accessible.

The OONI scanning techniques involved connecting to a known good HTTP server and making HTTP GET requests. Each GET request contained specially crafted Host header field that contained a given possibly blocked website. These requests were intercepted by the transparent HTTP proxy and when the site was present inside of the blocklist, it would return an error page, rather than the expected content.

In each case of a blocked page, the error page would be served immediately (without requiring a connection to the outside network) it was possible to parallelize a large amount of simultaneous connections and to set a very low timeout value. Because of this we were able to probe access for the Alexa top 1 million domains in less than 7 days.

At the moment there has not been any official response from the ISP in question and the actors responsible for the censorship have not come out. We believe that the access to information is an intrinsic human right and measures that limit people ability to read should be fought.

For more technical details check out [the full report on the OONI webpage](http://ooni.nu/releases/2012/Hadara_Palestine.html).

For the journalistic stories relating to this filtering, please see [the article on Ma'An](http://www.maannews.net/eng/ViewDetails.aspx?ID=478726) and [this post on EFF](https://www.eff.org/deeplinks/2012/04/palestinian-authority-found-block-critical-news-sites).
