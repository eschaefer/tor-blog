---
layout: post
title: "New Tor Browser Bundles and Tor 0.2.4.7-alpha packages available"
permalink: blog/new-tor-browser-bundles-and-tor-0247-alpha-packages-available
date: 2013-01-06
author: erinn
category: blog
tags: ["certificate authority", "firefox", "security", "tbb", "tor alpha", "tor browser bundle", "vidalia bundle"]
---

All of the Tor Browser Bundles have been updated to Firefox 10.0.12esr in order to address the recent problems with [TurkTrust](https://blog.mozilla.org/security/2013/01/03/revoking-trust-in-two-turktrust-certficates/) [certificates](http://googleonlinesecurity.blogspot.se/2013/01/enhancing-digital-certificate-security.html). From Mozilla's post:

> TURKTRUST, a certificate authority in Mozilla’s root program, mis-issued two intermediate certificates to customers. TURKTRUST has scanned their certificate database and log files and confirmed that the mistake was made for only two certificates.
>
> This is not a Firefox-specific issue. Nevertheless, we are concerned that at least one of the mis-issued intermediate certificates was used for man-in-the-middle (MITM) traffic management of domain names that the customer did not legitimately own or control. We are also concerned that the private keys for these certificates were not kept as secure as would be expected for intermediate certificates.

All users are strongly encouraged to upgrade.

There was also a new Tor 0.2.4.7-alpha release and all alpha packages have been updated with that.

**A note about the Vidalia bundles:**

The plain Vidalia bundles have been [discontinued](https://blog.torproject.org/blog/plain-vidalia-bundles-be-discontinued-dont-panic). We apologize for any confusion or inconvenience that this has caused for our users. In order to continue to use the Vidalia bundle as a client, download one of the available bundles, go into the Vidalia "Settings" menu and click "Run as a client only".

[https://www.torproject.org/download/download-easy](https://www.torproject.org/download/download-easy "https://www.torproject.org/download/download-easy")

**Tor Browser Bundle (2.3.25-2)**

- Update Firefox to 10.0.12esr
- Update Libevent to 2.0.21-stable
- Update HTTPS Everywhere to 3.1.2
- Update NoScript to 2.6.4.2

**Tor Browser Bundle (2.4.7-alpha-1)**

- Update Firefox to 10.0.12esr
- Update Tor to 0.2.4.7-alpha
- Update Libevent to 2.0.21-stable
- Update HTTPS Everywhere to 4.0development.4
- Update NoScript to 2.6.4.2

