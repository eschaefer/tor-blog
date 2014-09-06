---
layout: post
title: "Towards a Tor Censorship Analysis Tool"
permalink: blog/towards-tor-censorship-analysis-tool
date: 2013-02-06
author: phw
category: blog
tags: ["censorship", "measurement"]
---

The Tor network is [documented to be blocked](https://censorshipwiki.torproject.org) in several countries. Analyzing and circumventing these blocks typically requires detailed packet traces or access to machines inside censoring countries. Both, however, are not always easy to acquire:

1. Network traces are problematic for two reasons. First, they are difficult to obtain since they require the cooperation of users within censoring countries. Second, they are hard to anonymize and must not fall into wrong hands. Derived information, such as [flow diagrams](https://media.torproject.org/image/blog-images/2012-05-31-ethiopia-dpi-blocking-of-tor.png), is typically safe to publish but frequently lacks important information.
2. The alternative to network traces is to gain access to machines inside the censoring regime. This approach turns out to be difficult as well; mostly due to the lack of volunteers who could provide machines or the lack of VPS providers and open SOCKS proxies.

These problems show that there is a strong need for a lightweight tool which can assist in analyzing censorship events. This tool should be run by censored users and perform several tests to gain a rough understanding of how and if Tor could be blocked in the respective network. The results of these tests should make it back to the Tor project and would be used to improve circumvention technology such as [obfsproxy](https://www.torproject.org/projects/obfsproxy.html.en) and to [document censorship](https://censorshipwiki.torproject.org).

We created a [technical report which discusses the design requirements for such a censorship analysis tool](https://research.torproject.org/techreports/censorship-analysis-tool-2013-02-06.pdf). We list the desired features, discuss how they can be implemented and we give a rough overview of the software design. After all, this technical report should serve as basis for the development and deployment of the censorship analysis tool.

