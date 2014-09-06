---
layout: post
title: "The DigiNotar Debacle, and what you should do about it"
permalink: blog/diginotar-debacle-and-what-you-should-do-about-it
date: 2011-09-01
author: ioerror
category: blog
tags: ["ca certificates", "https", "ohdiginotaryoudidnt", "ssl certifications", "tor client safety", "tor network safety", "tor project website"]
---

Recently it has come to the attention of, well, nearly the entire world that the Dutch Certificate Authority DigiNotar incorrectly issued certificates to a malicious party or parties. Even more recently, it's come to light that they were apparently compromised months ago or [perhaps even in May of 2009](http://www.f-secure.com/weblog/archives/00002228.html) if not earlier.

This is pretty unfortunate, since correctly issuing certificates is exactly the function that a certificate authority (CA) is supposed to perform. By comparison, [ComodoGate](https://blog.torproject.org/blog/detecting-certificate-authority-compromises-and-web-browser-collusion) looks fairly minor.

**This incident doesn't affect the functionality of Tor clients or the Tor Network itself, since Tor doesn't use the flawed CA system.** The Tor network uses a much simpler and flatter [trust design](https://www.torproject.org/docs/faq#KeyManagement) that protects us from many of these CA issues. Further, Tor's [distributed-trust](https://www.torproject.org/images/htw2.png) design limits the damage from compromise of any given network component.

But the incident _does_ affect users that are attempting to reach The Tor Project's infrastructure: with one of these bogus certificates, an attacker could convince your browser that you were talking to The Tor Project website, when really you were talking to the attacker.

We have taken direct action in an attempt to stop this kind of attack in the future with two major browser vendors and we hope to integrate a fix with all other willing browsers. Please contact us if you ship a browser and you'd like to help your users to be proactively secure when visiting our sites. TorBrowser users should upgrade to our latest release and [verify signatures](https://www.torproject.org/docs/verifying-signatures.html.en) for all downloaded files. All Tor Browser Bundles have been updated to Firefox 6 with a patch to stop trusting the offending CA, and users are encouraged to upgrade. Below, we describe what we found out, what we're doing about it, and what you should do to keep yourself safe.

**The attack**

In the last seventy-two hours we were working to find positive confirmation that The Tor Project was one of the targeted groups. It was originally disclosed that at least [one](http://pastebin.com/ff7Yg663) [certificate](https://blog.torproject.org/files/google.com_.crt_.txt) was issued for '\*.google.com' and that it was being used [to actively Man-In-The-Middle](https://www.google.com/support/forum/p/gmail/thread?tid=2da6158b094b225a&hl=en) SSL and TLS connections. Quite quickly we found a similar pattern to the [ComodoGate fiasco](https://blog.torproject.org/blog/detecting-certificate-authority-compromises-and-web-browser-collusion). It appears likely that the Mozilla Addons site, Yahoo, Facebook, Twitter, and a few other major players were targeted. We do not have an authoritative list but I personally believe those targets to be accurate; time will tell. Additionally, we heard rumors that [we had graduated to the big leagues](http://www.nu.nl/internet/2603449/mogelijk-nepsoftware-verspreid-naast-aftappen-gmail.html) and we had also heard that DigiNotar had reached out to the major browser vendors. We did not receive any proactive contact from DigiNotar as a browser vendor and this worried us greatly when compounded with the rumor of being one of the targets as well.

We ship a [rather specific and special browser](https://www.torproject.org/projects/torbrowser.html) and it appeared that all of our sites are specifically in the attacker's target list. Having received no contact from DigiNotar, we reached out to DigiNotar by email and by telephone.

I spoke on the telephone with a rather nice but obviously overworked DigiNotar point of contact who will remain anonymous. He was guarded and careful in what he said but was clearly sympathetic to the severity of the matter at hand. It seemed quite clear that he repeated similar information to other impacted callers:

"What I can say is the following " ... "Any fraudulent torproject.org certificate that has been requested has been revoked. Any serial numbers that we know about have been revoked. All serial numbers have been communicated to the major browsers vendors." ... "Any certificate that we know of is revoked by OCSP server."

We emailed quite a bit back and forth after the phone call. A few hours later that same point of contact from DigiNotar sent [a list of all of the certificates in a spreadsheet](https://blog.torproject.org/files/DigiNotar-Tor-serial-list.xls). It appears that the attackers requested twelve certificates, and each certificate was for '\*.torproject.org'. The first batch of six certificates was issued on July 18th and the second batch of six certificates was issued on July 20th. According to the spreadsheet, the first six of the certificates expired on August 17th, 2011 and second batch of six certificates expired on August 19th, 2011. According to the information disclosed by DigiNotar the certificates in question should all have expired. The contact at DigiNotar stressed that there was no confirmation about the attacker(s) receiving the certificates. I have no reason to believe that these certificates would have any more trouble reaching the requesting party than the Google certificate used in the wild.

This is the current list of serial numbers for all twelve Tor Project certificates as disclosed to us by DigiNotar:

899AE120CD44FCEC0FFCD62F6FC4BB81
 7DD16C03DF0438B2BE5FC1D3E19F138B
 5432FC98141883F780897BC829EB9080
 73024E7C998B3DDD244CFD313D5E43B6
 B01D8C6F2D5373EABF0C00319E92AE95
 FF789632B8D4AECD94A0AAB33074A058
 86633B957280BC65A5ADFD1D153BDE52
 E7F58683066112DC5EB244FCF208E850
 1A07D8D6DDC7E623E71205074A05CEA2
 79C8E8B7DE36539FFC4B2B5825305324
 06CBB1CC51156C6D465F14829453DD68
 ED1A1008190A5D1654D138EB8FD1154A

DigiNotar has not provided us with a copy of any of the certificates that they issued. We are not sure that they have copies nor if they are willing to disclose any copies they may or may not have. This point is extremely disconcerting as the CRL/OCSP revocation process is essentially worthless. Mere serial numbers are simply not enough in some cases — especially when a full list of all likely compromised serial numbers has not been disclosed as happens to currently be the case.

To the best of our knowledge and by analyzing the CRLs for DigiNotar, we do not believe that any of the fraudulently issued '\*.torproject.org' certificates have been revoked at the time of this writing. It may be the case that they are simply not in the business of revoking certificates after they have expired. There is no evidence to support revocation during the time that these certificates were perfectly valid.

I believe that you can clearly see the [MITM attack in action](http://pastebin.com/rqwnJvn4) around the tenth hop of [this traceroute](https://blog.torproject.org/files/traceroutes-inside-iran.txt) thanks to an anonymous person in Iran:

1 3 ms 14 ms 2 ms 192.168.1.1
 2 67 ms 67 ms 65 ms 91.99.\*\*\*.\*\*\*.parsonline.net [91.99.\*\*\*.\*\*\*]
 3 65 ms 67 ms 93 ms 10.220.1.2
 4 67 ms 72 ms 66 ms 2.180.2.1
 5 66 ms 64 ms 64 ms 217.219.64.115
############### [MORE Nodes] #################
 6 451 ms 195 ms 154 ms 78.38.245.6
 7 626 ms 231 ms 88 ms 78.38.245.5
 8 93 ms 91 ms 96 ms 78.38.244.242
 9 88 ms 94 ms 120 ms 78.38.244.241
################### [MORE] ###################
 10 88 ms 88 ms 88 ms 10.10.53.33 ####DIfferent IP (0.0.0.33)

#### [OUT OF IRAN] ####
 11 340 ms \* \* pos3-1.palermo5.pal.seabone.net [195.22.198.77]

To quote someone I respect greatly: "That's not dodgy at all!"

Early statements By DigiNotar translated [by](http://pastebin.com/JTpA1tJ6) [someone](https://blog.torproject.org/files/translation-of-press-release.txt) and [mentioned by a friendly Dutch man](https://twitter.com/#!/rop_g/status/108643861697531904) lead us to believe that DigiNotar and their parent company are in damage-control mode. It would be unsurprising to hear that the Dutch Government is similarly in the dark about the scope of the compromise, as it appears DigiNotar does not control a canonical list for all certificates issued. While some Browser vendors have received a list, I do not have confidence that this list actually contains all malicious certificates that have been issued: rather it appears to be a subset that did not even include the Google certificate that was being used in the wild. We hope that DigiNotar will fully disclose whatever information they have and explain what information they honestly lack.

**The defense**

Modern versions of Chrome (13) were able to [prevent MITM attacks](https://blog.torproject.org/files/gmail_certificate_error.jpg) against most, if not all of the Google sites where they had [certificate pinning](http://www.imperialviolet.org/2011/05/04/pinning.html) and where [HSTS was enabled](https://secure.wikimedia.org/wikipedia/en/wiki/HTTP_Strict_Transport_Security). Google has also [announced the attacks](http://googleonlinesecurity.blogspot.com/2011/08/update-on-attempted-man-in-middle.html) and updated information about it. Additionally, they have [distrusted DigiNotar in Chrome](http://codereview.chromium.org/7795014).

We've sent a request to Google that they enable HSTS and pin certificates for some of the critical Tor sites and that [patch](http://codereview.chromium.org/7818002) [is](http://codereview.chromium.org/7818002/patch/1/3) [pending](http://codereview.chromium.org/7818002/patch/1/2). Google has been very good about all of this and I can't thank them enough for their help.

As it stands, Chrome appears to have shipped a fix that distrusts DigiNotar and it appears to treat [hundreds of certificates](http://codereview.chromium.org/7791032/diff/2001/net/base/x509_certificate.cc) as if they are specifically known to be malicious or hostile. Mozilla and others have shipped a fix as well. Sadly, it appears that the Dutch Government asked various browser vendors to create an exemption for certain trust chains as some kind of compromise. However, we were not party to any of the discussions, and we don't understand the core concerns for such a compromise. We're not willing to take a leap of faith for a Certificate Authority that did not contact us when they first noticed this problem. Right now, if we found a DigiNotar-issued certificate certifying that water was wet, we wouldn't believe it without checking for ourselves. Twice.

We have [proactively given](https://gitweb.torproject.org/torbrowser.git/commit/0be3b043afa0e54d207f603a3bf3716f6165caa1) DigiNotar an "Internet Death Sentence" in the Tor Browser. The direct impact of removing DigiNotar should be on the order of around seven hundred certificates according to some [cursory queries](https://twitter.com/#!/nocombat/status/108951156377661441) run against the EFF's [SSL Observatory](https://www.eff.org/observatory). I believe that the number of certificates revoked is nearing parity with the number of possibly legitimate still-valid certificates issued by DigiNotar. That's a sad state of affairs.

We do not currently have evidence of any tampering with Tor downloads, but we're looking. If an attacker can successfully perform a MITM attack, there is nothing to prevent them from giving you a bogus package instead of the software you were actually looking for — if you're not checking package signatures, there's no easy way to tell good software from bad.

**What you should do**

**First of all, upgrade your browser(s).** See [this blog post](http://blog.torproject.org/blog/new-tor-browser-bundles-4) announcing the new Tor Browser Bundles with Firefox 6.

Note that verifying the signatures on Tor packages prevents attackers like this from causing you to install a possibly backdoored version of Tor. You should always verify the signature of any software you download. We encourage you to [learn more about secure signature verification](https://www.torproject.org/docs/verifying-signatures.html.en).

If you have downloaded copies of any Tor software in the past few months, and you did it over any network that you don't trust, please help us check to see whether there was any attempt to alter them. We don't expect you'll find anything, but if you do, we really want to know about it. In any case, it will be good practice for checking signatures.

If you have any information about certificates that you believe to be false, please do send us the certificates and we'll take a look.

The Certificate Authority system as it stands today is a house of cards and we're witnessing in public what many have known for years in private. The entire system is soaked in petrol and waiting for a light. There are some new directions for trust in the works such as [Convergence](http://convergence.io/details.html) and various ways to do [DNSSEC authenticated HTTPS](http://www.imperialviolet.org/2011/06/16/dnssecchrome.html) as well as other hacks. Still, nothing is set in stone or standardized and this is why we need to remain vigilant. We're hoping to detect these kinds of attacks in the future with our [distributed SSL Observatory](https://trac.torproject.org/projects/tor/wiki/doc/HTTPSEverywhere/SSLObservatorySubmission) and we hope that you'll join us.

I'd like to end on a [positive note](http://www.crypto.com/blog/spycerts/) and quote a personal hero and friend, Matt Blaze: "A decade ago, I observed that commercial certificate authorities protect you from anyone from whom they are unwilling to take money. That turns out to be wrong; they don't even do that much."

<thead><tr>
<th>Attachment</th>
<th>Size</th> </tr></thead><tbody>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/traceroutes-inside-iran.txt">traceroutes-inside-iran.txt</a></td>
<td>4.28 KB</td> </tr>
 <tr class="even">
<td><a href="https://blog.torproject.org/files/translation-of-press-release.txt">translation-of-press-release.txt</a></td>
<td>3.4 KB</td> </tr>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/google.com_.crt_.txt">google.com_.crt_.txt</a></td>
<td>1.81 KB</td> </tr>
 <tr class="even">
<td><a href="https://blog.torproject.org/files/gmail_certificate_error.jpg">gmail_certificate_error.jpg</a></td>
<td>141.84 KB</td> </tr>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/DigiNotar-Tor-serial-list.xls">DigiNotar-Tor-serial-list.xls</a></td>
<td>8.94 KB</td> </tr>
</tbody>

