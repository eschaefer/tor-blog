---
layout: post
title: "AntiVir, Tor Browser Bundle, and trojan Dropper.Gen false positive"
permalink: blog/antivir-tor-browser-bundle-and-trojan-droppergen-false-positive
date: 2009-04-07
author: phobos
category: blog
tags: ["anti-virus", "false positive", "tor browser bundle"]
---

A number of people are reporting that AntiVir's latest update is reporting trojan Dropper.Gen in the Tor Browser Bundle version 1.1.11, specifically the "Start Tor Browser.exe" program.

This appears to be a false positive from AntiVir. No one has confirmed they've checked the pgp signature with their download of TBB. You may want to confirm you've actually downloaded our package, [https://www.torproject.org/verifying-signatures](https://www.torproject.org/verifying-signatures "https://www.torproject.org/verifying-signatures").

False positives occurs often enough we have a FAQ entry about it, [https://www.torproject.org/faq#VirusFalsePositives](https://www.torproject.org/faq#VirusFalsePositives "https://www.torproject.org/faq#VirusFalsePositives")

You can read more about the trojan at [http://www.avira.ro/en/threats/section/details/id\_vir/3647/tr\_dropper.ge...](http://www.avira.ro/en/threats/section/details/id_vir/3647/tr_dropper.gen.html "http://www.avira.ro/en/threats/section/details/id\_vir/3647/tr\_dropper.gen.html")

I'm building a VM to specifically test this AntiVir version against Start Tor Browser.exe to see what inside the executable is triggering the false positive.

