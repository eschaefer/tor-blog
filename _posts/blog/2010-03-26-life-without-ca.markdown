---
layout: post
title: "Life without a CA"
permalink: life-without-ca
date: 2010-03-26
author: phobos
category: blog
tags: ["certificate authority", "certificate fingerprints", "distributed trust", "firefox", "ssl errors"]
---

At [Libreplanet 2010](http://libreplanet.org/), I was in a discussion with the [MonkeySphere](https://web.monkeysphere.info/) and [EFF](https://www.eff.org/) folks about how to encourage every website to offer ssl by default. The general idea is to stop local traffic snooping and provide more security by default. During the discussion, it came up that I disable all of the [Certificate Authorities](http://en.wikipedia.org/wiki/Certificate_authority) in my systems and selectively trust the ssl certificates from individual websites. I've been doing this for years. Apparently my admission was a shocking statement to many. The group asked me to document my Firefox setup and what life is like without any trusted CAs. Seth from the EFF has a [quick post](https://www.eff.org/deeplinks/2010/03/researchers-reveal-likelihood-governments-fake-ssl) about possible concerns over the CAs in your browser. I used to rely on the [Certificate Patrol](https://addons.mozilla.org/en-US/firefox/addon/6415) Firefox Extension to monitor changing certs.

I generally use FreeBSD and Debian-based linux distributions for my operating systems. After I install firefox, I rename libnssckbi.so to something else (like libnssckbi.so.saved). Restart Firefox (see below for option two). Firefox should no longer validate ssl certs automatically.

Browse to a secure website, like [https://torproject.org/](https://torproject.org/ "https://torproject.org/"). You should get the intentionally scary "This Connection is Untrusted" certificate error page. However, you should expect this error as there are no more CAs to validate against. Click "I Understand the Risks". Click "Add Exception". Firefox should retrieve the certificate. Click "View". This is where it gets interesting.

How do you validate the certificate? It depends on the other end. For sites I worry about, like my bank or favorite shopping stores, I call support and ask for the SSL fingerprint and serial number. Sometimes the support person even knows what I'm talking about. I suspect they just open their browser, click on the lock icon and read me the information. Generally, it takes some work to get the information. Further, I'll compare the cert received through Tor and through non-Tor ssh tunnels on disparate hosts. However, you only have to do this checking once per cert. Once you have it, Firefox stores it as an exception and, if the cert doesn't change between visits, doesn't interrupt you with the cert error page.

Am I too paranoid or dis-trusting of CAs? Probably. I have a few concerns about this process, too. Does the list of certs in my browser open me up to unique fingerprinting in some way? Would I notice if a [Packet Forensics](http://www.wired.com/threatlevel/2010/03/packet-forensics/) device was used? Unless someone screwed up, I doubt it. And a seldom asked question is, have I ever caught ssl certs being faked or changed by a man-in-the-middle? Yes I have.

What would I like to see rather than implicitly trusting centralized CAs? I very much like the model used by gpg and [the web of trust](http://en.wikipedia.org/wiki/Web_of_trust). I think it's completely infeasible right now for the vast majority of people using the Internet today. However, using computers was infeasible for the vast majority of people merely a decade ago. Progress happens quickly.

(option two)  
 I generally remove all of the CAs as well, even though I think it's just a display issue at this point. To do so, go into Preferences, Advanced, Encryption tab, click View Certificates. Then just manually cycle through the remaining CAs and delete them all. I started writing a script to do this automatically, but it seems to change in each version of Firefox. If someone has a better/more automatic way to do this, I'd like to hear about it. Now you have no CAs.

