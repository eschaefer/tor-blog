---
layout: post
title: "Top changes in Tor since the 2004 design paper (Part 3)"
permalink: top-changes-tor-2004-design-paper-part-3
date: 2012-11-01
author: sjmurdoch
category: blog
tags: []
---

In this third and final installment of Nick Mathewson and Steven Murdoch's blog series (previously [part 1](https://blog.torproject.org/blog/top-changes-tor-2004-design-paper-part-1) and [part 2](https://blog.torproject.org/blog/top-changes-tor-2004-design-paper-part-2)) we discuss how Tor has made its traffic harder to fingerprint, as well as usability and security improvements to how users interact with Tor.

## 9. Link protocol TLS, renegotiation

Tor's original (version 1) TLS handshake was fairly straightforward. The client said that it supported a sensible set of cryptographic algorithms and parameters (ciphersuites, in TLS terminology) and the server selected one. If one side wanted to prove to the other that it was a Tor node, it would send a two-element certificate chain signed by the key published in the Tor directory.

This approach met all the security properties envisaged at the time the 2004 design paper was written, but Tor's increasing use in censorship resistance changed the requirements – Tor's protocol signature also had to look like that of HTTPS web traffic, to prevent censors using deep-packet-inspection to detect and block Tor.

It turned out that Tor's original design looked very different from HTTPS. Firstly, web browsers offer a wide range of ciphersuites which Tor cannot use, such as those using RC4 (due to the narrow security margins) and RSA key exchange (due to lack of [forward secrecy](https://en.wikipedia.org/wiki/Perfect_forward_secrecy)). Secondly, in HTTPS web traffic, the client seldom offers a certificate, and the server usually offers a one-element certificate chain, whereas in Tor node-to-node communication both sides offer a two-element certificate chain.

Therefore [proposal 124](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/124-tls-certificates.txt), later superseded by [proposal 130](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/130-v2-conn-protocol.txt), tried to resolve the situation and the resulting version 2 connection protocol was implemented in Tor 0.2.0.20-rc. Here, the client presents a large selection of ciphersuites (including some it doesn't actually support), selected to appear similar to that of a web browser. The server then chooses one which is suitable for use in Tor, but if the server chooses one which is not adequately secure, the client will pull down the connection.

To make the certificate part of the handshake look closer to HTTPS, the client sends no certificate, and the server sends a one-element dummy certificate chain. The certificate offered by the server is designed to not contain distinctive strings which could be used for blocking (version 1 certificates used "Tor" or "TOR" as the organization name). Once the handshake is complete, Tor then restarts the handshake (via TLS renegotiation), but now encrypted under the keys established in the first handshake, and sends the two-element certificate chains as before.

This improves the situation for anti-blocking considerably, although more could still be done. In particular, the fact that renegotiation is occurring is not hidden from an observer because the type of TLS messages (known as records) is not encrypted in TLS, and renegotiation records are of a different type from data records. Therefore version 3 of the connection protocol, described in [proposal 176](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/176-revising-handshake.txt) and implemented in Tor 0.2.3.6-alpha, moves the second stage of the handshake into data records, binding the inner to the outer handshake through sharing some key material.

## 10. Rise and fall of .exit

In Tor 0.0.9rc5, Tor had the .exit feature added. Here, if the user requested _domain_._nickname_.exit then Tor would make a connection to _domain_ using the Tor node called _nickname_ as the last hop (if possible). This was a convenient feature for exploring how the Internet looked from different locations, but it also raised some security concerns.

In particular, a malicious website could embed an image with a .exit hostname, forcing the Tor client to select an attacker-controlled exit node. Then, if the user also chooses an attacker-controlled entry node the circuit could be de-anonymized. This strategy increases the probability of a successful attack from about (M/N)<sup>2</sup> to M/N (where M is the amount of attacker-controlled network resource and N is the total network resource).

Therefore, in Tor 0.2.2.1-alpha, .exit notation was disabled by default. In Tor 0.2.3.17-beta an exception was made, allowing .exit notation when it is specified in the configuration file or by a controller. These sources are assumed to be safe, and by combining the .exit notation with the MapAddress option it is possible for the client to always contact some domain names via a particular exit node. This is useful when a service is running on the same machine as a Tor node, as then the user can choose for circuits to never leave the Tor network.

## 11. Controller protocol

Tor has always had a minimalist user interface – it can be configured on the command line or a configuration file and sends output to a log file. This is fine for advanced users, but most users will prefer a GUI. Building a GUI into Tor would be difficult, and would force certain choices (e.g. GUI toolkit) to be made which might not suit all users and all platforms. Therefore the approach taken by Tor in 0.0.9pre5 is to build an interface for other programs – the control protocol – to communicate with the Tor daemon, extracting information to display on the GUI and changing the Tor configuration based on user actions.

The control protocol has also proven useful to researchers experimenting with Tor. Initially the functionality exposed in the control protocol was simply that exposed by the configuration file and log files. Providing status information in a specified and machine-readable format made the task of monitoring and controlling Tor easier. Later, functionality was added to the control protocol which should not be exposed to ordinary Tor users but is useful to researchers, such as allowing controllers to arbitrarily control the path selection process (added in 0.1.0.1-rc).

In 0.1.1.1-alpha the protocol was changed to version 1, which used ASCII rather than binary commands to make it easier to write and debug controllers as well as allow advanced users to telnet into the control port and manually type commands.

## 12. Torbutton

The 2004 design paper stated that Tor explicitly did not make any attempt to scrub application data which might contain identifying information. By adopting the near universal SOCKS protocol, almost any application could send its traffic over Tor, but there was no guarantee it would be safe to do so. This is in contrast to the the predecessors to Tor from the Onion Routing project which required an "application proxy" to be written for each protocol carried by Tor. These proxies greatly increased the cost for supporting each additional application.

Still, there was clear need for a place to perform the protocol scrubbing, and so Tor recommended that [Privoxy](http://www.privoxy.org/) take the place of an application proxy for HTTP. However, the disadvantages of this approach gradually became clear, in particular Privoxy could not inspect or modify HTTPS traffic and so malicious websites could send their tracking code over HTTPS and avoid scrubbing.

Therefore, more and more of the scrubbing was performed by a Firefox add-on, [Torbutton](https://www.torproject.org/torbutton/), which also could turn Tor on and off – hence the name. Torbutton had full access to content regardless of whether it was HTTP or HTTPS and could also disable features of Firefox which were bad for privacy. A proxy was still needed though, because Firefox's SOCKS support handled high-latency connections badly, so the lighter-weight [Polipo](http://www.pps.univ-paris-diderot.fr/~jch/software/polipo/) was adopted instead.

## 13. Tor Browser Bundle

Now to use Tor, most users would need to download and install Tor, Firefox, Torbutton and Polipo, probably along with a GUI controller such as [Vidalia](https://www.torproject.org/projects/vidalia.html.en). This was inconvenient, especially for customers of Internet cafes who could not install software on the computer they were using. So the Tor Browser Bundle was created which included all this software, pre-configured to be run from a USB drive.

This was far easier to use than the previous way to install Tor, and eventually became the default. It had the added advantage that we could modify the browser to include patches which made Polipo unnecessary and to fix some privacy problems which could not be solved from within a Firefox add-on. It was also safer for users because now Torbutton could not be disabled, meaning that the user had different web browsers for anonymous and non-anonymous browsing and were less likely to muddle up the two.

