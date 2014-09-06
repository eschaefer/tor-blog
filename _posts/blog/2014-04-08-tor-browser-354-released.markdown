---
layout: post
title: "Tor Browser 3.5.4 is Released"
permalink: blog/tor-browser-354-released
date: 2014-04-08
author: mikeperry
category: blog
tags: ["tbb", "tbb-3.5", "tor-browser", "tor-browser-bundle"]
---

The 3.5.4-stable release of the Tor Browser is now available on the [Download page](https://www.torproject.org/download/download-easy.html). You can also download the bundles directly from the [distribution directory](https://www.torproject.org/dist/torbrowser/3.5.4/).

This release updates only OpenSSL to version 1.0.1g, to address potential client-side vectors for [CVE-2014-0160](https://blog.torproject.org/blog/openssl-bug-cve-2014-0160).

The browser itself does not use OpenSSL, and is not vulnerable to this CVE. However, this release is still considered an important security update, because it is theoretically possible to extract sensitive information from the Tor client sub-process.

Here is the changelog:

- All Platforms

  - Update OpenSSL to 1.0.1g

