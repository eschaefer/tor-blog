---
layout: post
title: "DigiNotar Damage Disclosure"
permalink: diginotar-damage-disclosure
date: 2011-09-04 11:30:38
author: ioerror
category: blog
status: closed
tags: ["ca certificates", "https", "ohdiginotaryoudidnt", "ssl certifications", "tor client safety", "tor network safety", "tor project website"]
---

About an hour ago I was contacted by the Dutch Government with more details about the [DigiNotar Debacle](https://blog.torproject.org/blog/diginotar-debacle-and-what-you-should-do-about-it). It seems that they're doing a great job keeping on top of things and doing the job that DigiNotar should've done in July. They sent a spreadsheet with a list of 531 entries on the currently known bad DigiNotar related certificates.

The list isn't pretty and I've decided that in the interest of defenders everywhere without special connections, I'm going to disclose it. The people that I have spoken with in the Dutch Government agree with this course of action.

This disclosure will absolutely not help any attacker as it does not contain the raw certificates; it is merely metadata about the certificates that were issued. It includes who we should not trust in the future going forward and it shows what is missing at the moment. This is an incomplete list because DigiNotar's audit trail is incomplete.

This is the list of CA roots that should probably never be trusted again:

DigiNotar Cyber CA  
 DigiNotar Extended Validation CA  
 DigiNotar Public CA 2025  
 DigiNotar Public CA - G2  
 Koninklijke Notariele Beroepsorganisatie CA  
 Stichting TTP Infos CA

The most egregious certs issued were for \*.\*.com and \*.\*.org while certificates for Windows Update and certificates for other hosts are of limited harm by comparison. The attackers also issued certificates in the names of other certificate authorities such as "VeriSign Root CA" and "Thawte Root CA" as we witnessed with [ComodoGate](https://blog.torproject.org/blog/detecting-certificate-authority-compromises-and-web-browser-collusion), although we cannot determine whether they succeeded in creating any intermediate CA certs. That's really saying something about the amount of damage a single compromised CA might inflict with poor security practices and regular internet luck.

Of particular note is this certificate:  
 CN=\*.RamzShekaneBozorg.com,SN=PK000229200006593,OU=Sare Toro Ham Mishkanam,L=Tehran,O=Hameye Ramzaro Mishkanam,C=IR

The text here appears to be be an entry like any other but it is infact a calling card from a Farsi speaker. RamzShekaneBozorg.com is not a valid domain as of this writing.

Thanks to an anonymous Farsi speaker, I now understand that the above certificate is actually a comment to anyone who bothers to read between the lines:  
 "RamzShekaneBozorg" is "great cracker"  
 "Hameyeh Ramzaro Mishkanam" translates to "I will crack all encryption"  
 "Sare Toro Ham Mishkanam" translates to "i hate/break your head"

Without any further delay, I've uploaded [the original spreadsheet](https://blog.torproject.org/files/rogue-certs-2011-09-04.xlsx) and [a CSV text file](https://blog.torproject.org/files/rogue-certs-2011-09-04.csv) for people who don't trust spreadsheets. The information contained in both files should be the same. Hopefully this information will help people to mitigate certain harm from the [DigiNotar Debacle](https://blog.torproject.org/blog/diginotar-debacle-and-what-you-should-do-about-it).
