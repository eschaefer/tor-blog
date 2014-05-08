---
layout: post
title: "The MD5 certificate collision attack, and what it means for Tor"
permalink: md5-certificate-collision-attack%2C-and-what-it-means-tor
date: 12/30/2008
author: nickm
category: blog
tags: ["attack", "md5", "security", "ssl", "tls", "x509"]
---

Today, a team of security researchers and cryptographers gave a talk at the [25th Chaos Communication Congress (25C3)](http://events.ccc.de/congress/2008/), about a [nifty attack against X.509 certificates generated using the MD5 digest algorithm](http://www.win.tue.nl/hashclash/rogue-ca/). We figured that people will ask us about how this attack affects Tor, so I'm writing an answer in advance.

**The short version:** This attack doesn't affect Tor.

**The medium version:** This attack doesn't affect Tor, since Tor doesn't ever use MD5 certificates, and since Tor doesn't care what certificate authorities say. On the other hand, this attack probably _does_ affect your browser. Check your browser vendor for updates over the next few days and weeks, and make sure you install them.

**The long version:** To understand the attack, first you've got to understand certificates. When your browser makes a connection to a "secure" website, it uses a protocol called [SSL (or sometimes TLS)](http://en.wikipedia.org/wiki/Transport_layer_security) to see who it's talking to and encrypt the connection with them. In SSL, parties are identified using [X.509 certificates](http://en.wikipedia.org/wiki/X.509), which are issued to them by certificate authorities, or "CA"s. Your browser comes with [a big list of certificate authorities](http://www.mozilla.org/projects/security/certs/included/). When your browser sees a certificate that was signed by a certificate authority it recognizes, it knows it's talking to the right website.

Certificates, like nearly anything of interest, are too big to sign as-is, so the CA uses a [cryptographic "digest" algorithm](http://en.wikipedia.org/wiki/Cryptographic_hash_function) to derive a short "hash" of the certificate that it can sign. The digest algorithm is supposed to be "collision resistant", so that nobody can find two different certificates that produce the same hash. Such a collision would be bad, since somebody who could produce two such certificates could get a CA to sign one of them, and then use that signature on the other one. Since the hash values would be the same, nobody would be able to tell that the CA had not really signed the second certificate.

With me so far? Good. Let's talk about MD5. There is an old broken hash algorithm called [MD5](http://en.wikipedia.org/wiki/MD5). How old and broken? Cryptographers have considered it weak since 1996 or so, and there have been known real collisions in it since 2004. In 2007, researchers published a method for generating MD5 collisions that could be used against X.509 certificates. In other words, the writing has been on the wall since at least 1996 (arguably 1993), and the writing has been getting bigger year after year. You'd have to be pretty oblivious to still use MD5 for signing certificates in 2008!

Unfortunately, some brave CAs still use MD5 for signing certificates in 2008. And so we come to the attack.

Using a method derived from the 2007 paper, and a cluster of 200 Playstation 3s, the researchers generated two certificates that would produce an MD5 collision: one innocuous one, and one CA certificate. They got a CA to sign the first one, and then transferred this signature to the second. Since the second certificate was for a CA, they now had a certificate that let them generate their _own_ certificates, and make any phony claims they wanted about the identity of any website. If your browser saw one of these phony certificates, it would believe it, since it was ultimately signed by a CA it recognized.

For more information on the attack, with a lot of complicated tricky bits I didn't mention, see [the authors' writeup](http://www.win.tue.nl/hashclash/rogue-ca/).

The good news is that **Tor itself is not affected** . Tor doesn't use MD5 for anything[\*]. Tor doesn't use commercial CAs. Tor doesn't sign certificates for others, and everything in Tor that is signed is signed using SHA-1, not MD5.[\*\*]

The bad news is that your browser probably does have some of the affected CAs listed. As how-to guides for securing your browser become available, we'll post links to them here.

Finally: Happy new year! And best wishes to any programmers who get stuck working all night on New Year's Eve to remove MD5 from their system.

Footnotes:

[\*] The fine print: Tor uses the TLS protocol, which uses MD5 in a couple of places. But TLS uses in tandem with SHA-1, so an attacker will need to break SHA-1 and MD5 at the same time to harm TLS's security. Read RFC2246 for the ugly ugly details.

[\*\*] Yes, I know that SHA-1 is showing its age too. Unfortunately, the SHA-2 algorithms aren't _that_ much better, and nothing else has seen the same amount of analysis. Once the [NIST hash function competition](http://en.wikipedia.org/wiki/NIST_hash_function_competition) has picked a SHA-3 candidate, we'll switch to that. In the mean time, I'll be launching some design work on or-dev to make it easier for Tor to switch to a better hash algorithm, once we've got one, or in case we need to jump off SHA-1 in a hurry.

