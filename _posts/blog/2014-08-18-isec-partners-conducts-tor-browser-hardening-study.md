---
layout: post
title: "iSEC Partners Conducts Tor Browser Hardening Study"
permalink: isec-partners-conducts-tor-browser-hardening-study
date: 2014-08-18 18:13:16
author: mikeperry
category: blog
status: closed
tags: ["security", "tbb", "tor browser"]
---

In May, the [Open Technology Fund](https://www.opentechfund.org/) commissioned [iSEC Partners](https://www.isecpartners.com/) to study current and future hardening options for the Tor Browser. The Open Technology Fund is the primary funder of Tor Browser development, and it commissions security analysis and review for all of the projects that it funds as a standard practice. We worked with iSEC to define the scope of the engagement to focus on the following six main areas:

1.  Review of the current state of hardening in Tor Browser
2.  Investigate additional hardening options and instrumentation
3.  Perform historical vulnerability analysis on Firefox, in order to make informed vulnerability surface reduction recommendations
4.  Investigate image, audio, and video codecs and their respective library's vulnerability history
5.  Review our current about:config settings, both for vulnerability surface reduction and security
6.  Review alternate/obscure protocol and application handlers

  
The [complete report](https://github.com/iSECPartners/publications/tree/master/reports/Tor%20Browser%20Bundle) is available in the iSEC publications github repo. All tickets related to the report can be found using the [tbb-isec-report keyword](https://trac.torproject.org/projects/tor/query?status=!closed&keywords=~tbb-isec-report). General Tor Browser security tickets can be found using the [tbb-security keyword](https://trac.torproject.org/projects/tor/query?status=!closed&keywords=~tbb-security).

Major Findings and Recommendations
==================================

The report had the following high-level findings and recommendations.

-   **Address Space Layout Randomization is disabled on Windows and Mac**
-   **Participate in Pwn2Own**
-   **Test and recommend the Microsoft Enhanced Mitigation Experience Toolkit on Windows**
-   **Replace the Firefox memory allocator (jemalloc) with ctmalloc/PartitionAlloc**
-   **Make use of advanced ParitionAlloc features and other instrumentation to reduce the risk from use-after-free vulnerabilities**

Vulnerability Surface Reduction (Security Slider)
=================================================

A large portion of the report was also focused on analyzing historical Firefox vulnerability data and other sources of large vulnerability surface for a planned "Security Slider" UI in Tor Browser.

The Security Slider was first suggested by Roger Dingledine as a way to make it easy for users to trade off between functionality and security, gradually disabling features ranked by both vulnerability count and web prevalence/usability impact.

The report makes several recommendations along these lines, but a brief distillation can be found on the [ticket for the slider](https://trac.torproject.org/projects/tor/ticket/9387#comment:43).

At a high level, we plan for four levels in this slider. "Low" security will be the current Tor Browser settings, with the addition of JIT support. "Medium-Low" will disable most of the JIT, and make HTML5 media click-to-play via NoScript. "Medium-High" will disable the rest of the JIT, will disable JS on non-HTTPS url bar origins, and disable SVG. "High" will fully disable Javascript, block remote fonts via NoScript, and disable all media codecs except for WebM (which will remain click-to-play).

The Long Term
=============

A web browser is a very large and complicated piece of software, and while we believe that the [privacy properties](https://www.torproject.org/projects/torbrowser/design/#privacy) of Tor Browser are better than those of every other web browser currently available, it is very important to us that we raise the bar to successful code execution and exploitation of Tor Browser as well.

We are very eager to see the deployment of [sandboxing support in Firefox](https://wiki.mozilla.org/Security/Sandbox), which should go a long way to improving the security of Tor Browser as well. To improve security for their users, Mozilla has recently shifted [10 engineers](https://groups.google.com/forum/#!searchin/mozilla.dev.platform/e10s/mozilla.dev.platform/q0Ku_8j26Pc/OtHXnNThv0IJ) into the Electrolysis project, which provides the groundwork for producing a multiprocess sandbox architecture for the desktop Firefox. This will allow them to provide a Google Chrome style security sandbox for website content, to reduce the risk from software vulnerabilities, and generally impede exploitability.

Until that time, we will also be investigating providing [hardened builds of Tor Browser](https://trac.torproject.org/projects/tor/ticket/10599) using the [AddressSanitizer](https://code.google.com/p/address-sanitizer/wiki/AddressSanitizer) and [Virtual Table Verification](https://gcc.gnu.org/wiki/vtv) features of newer GCC releases. While this will not eliminate all vectors of memory corruption-based exploitation (in particular, the hardening properties of AddressSanitizer are not as good as those provided by [SoftBounds+CETS](www.github.com/santoshn/softboundcets-34/) for example, but that compiler is not yet production-ready), it should raise the bar to exploitation. We are hopeful that these builds in combination with PartitionAlloc and the Security Slider will satisfy the needs of our users who require high security and who are willing to trade performance and usability in order to get it.

We also hope to include optional [application-wide sandboxes](https://trac.torproject.org/projects/tor/ticket/5791) for Tor Browser as part of the official distribution.

Why not Google Chrome?
======================

It is no secret that in many ways, both we and Mozilla are playing catch-up to reach the level of code execution security provided by Google Chrome, and in fact closely following the Google Chrome security team was one of the recommendations of the iSEC report.

In particular, Google Chrome benefits from a [multiprocess sandboxing architecture](http://www.chromium.org/Home/chromium-security/guts), as well as several further [hardening options and innovations](http://www.chromium.org/Home/chromium-security/brag-sheet) (such as PartitionAlloc).

Unfortunately, our budget for the browser project is still very constrained compared to the amount of work that is required to provide the [privacy properties we feel are important](https://www.torproject.org/projects/torbrowser/design/#privacy), and Firefox remains a far more cost-effective platform for us for several reasons. In particular, Firefox's flexible extension system, fully scriptable UI, solid proxy support, and its long Extended Support Release cycle all allow us to accomplish far more with fewer resources than we could with any other web browser.

Further, Google Chrome is far less amenable to supporting [basic web privacy](https://www.torproject.org/projects/torbrowser/design/#privacy) and Tor-critical features (such as solid proxy support) than Mozilla Firefox. [Initial efforts](https://blog.torproject.org/blog/google-chrome-incognito-mode-tor-and-fingerprinting) to work with the Google Chrome team saw some success in terms of adding APIs that are crucial to addons such as HTTPS-Everywhere, but we ran into several roadblocks when it came to Tor-specific features and changes. In particular, [several bugs required for basic proxy-safe Tor support](https://trac.torproject.org/projects/tor/wiki/doc/ImportantGoogleChromeBugs#ProxyBypassBugs) for Google Chrome's Incognito Mode ended up blocked for various reasons. The [worst offender](https://code.google.com/p/chromium/issues/detail?id=80722) on this front is the use of the Microsoft Windows CryptoAPI for certificate validation, without any alternative. This bug means that certificate revocation checking and intermediate certificate retrieval happen outside of the browser's proxy settings, and is subject to alteration by the OEM and/or the enterprise administrator. Worse, beyond the Tor proxy issues, the use of this OS certificate validation API means that the OEM and enterprise also have a simple entry point for installing their own root certificates to enable transparent HTTPS man-in-the-middle, with full browser validation and no user consent or awareness. All of this is not to mention the need for defenses against [third party tracking](https://www.torproject.org/projects/torbrowser/design/#identifier-linkability) and [fingerprinting](https://www.torproject.org/projects/torbrowser/design/#fingerprinting-linkability) to prevent the linking of Tor activity to non-Tor usage, and which would also be useful for the wider non-Tor userbase.

While we'd love for this situation to change, and are open to working with Google to improve things, at present it means that our only option for Chrome is to maintain an even more invasive fork than our current Firefox patch set, with much less likelihood of a future merge than with Firefox. As a ballpark estimate, maintaining such a fork would require somewhere between 3 and 5 times the engineering staff and infrastructure we currently have at our disposal, in addition to the ramp-up time to port our current feature set over.

Unless either our funding situation or Google's attitude towards the features we require changes, Mozilla Firefox will remain the best platform for us to demonstrate that it is in fact possible to provide [true privacy by design](http://www.w3.org/2012/dnt-ws/position-papers/21.pdf) for the web for those who want it. It is very distressing that this means playing catch-up and forcing our users to make usability tradeoffs in exchange for improved browser security, but we will continue to do what we can to improve that situation, both with Mozilla and with our own independent efforts.
