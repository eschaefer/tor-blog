---
layout: post
title: "New Bundles"
permalink: new-bundles
date: 02/08/2013
author: erinn
category: blog
tags: ["alpha release", "bundle upgrades", "openssl", "tbb", "tor browser bundle"]
---

 **UPDATE: Don't upgrade to these bundles.** The version of OpenSSL in these bundles -- even though it fixes some bugs -- introduces new bugs that will prevent Tor from working on many computers. See the following links for more information:

- [Watch out for openssl 1.0.1d if you're using AESNI](https://lists.torproject.org/pipermail/tor-talk/2013-February/027252.html)
- [stitched aes-ni ciphers in openssl 1.0.1d seems to break SSL Handshakes/Renegotiations](https://trac.torproject.org/projects/tor/ticket/8179)

Please continue using the old bundles. All of the download links have been downgraded to the previous version. We will release updated bundles in a few days. Thanks.

All of the bundles have been updated. The alpha bundles contain the latest Tor 0.2.4.10-alpha and all of the bundles have received an [OpenSSL update](http://www.openssl.org/news/secadv_20130205.txt) (1.0.1d for everything except the PPC Vidalia bundles which have 0.9.8y). The regular obfsproxy bundles have been discontinued but pyobfsproxy/flashproxy bundles are available from the [obfsproxy](https://www.torproject.org/projects/obfsproxy) page. We plan to begin shipping these as part of the regular release cycle within the next month or two.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Tor Browser Bundle (2.3.25-3)**

- Update OpenSSL to 1.0.1d
- Update HTTPS Everywhere to 3.1.3
- Update NoScript to 2.6.4.4

**Tor Browser Bundle (2.4.10-alpha-1)**

- Update Tor to 0.2.4.10-alpha
- Update OpenSSL to 1.0.1d
- Update NoScript to 2.6.4.4
- Add PDF Viewer (PDF.js) to README

