---
layout: post
title: "Ultrasurf: the definitive review"
permalink: ultrasurf-definitive-review
date: 2012-04-16
author: ioerror
category: blog
tags: ["research", "reverse engineering", "snakeoil", "ultrasurf"]
---

In the summer of 2011, I spent a few months learning how to effectively reverse engineer Windows software. I'm still learning and while I have a lifetime of learning to do on the topic, I chose to audit Ultrasurf as a challenge. This research was performed as a labor of love and it was funded work. My interest in reverse engineering Ultrasurf comes entirely because I have seen people promoting it without also offering evidence that it is safe. Additionally, a few people had asked me what I thought of the software and in order to form an opinion, I decided to dig deeper.

Ultrasurf is software produced by the UltraReach company for censorship circumvention, privacy, security and anonymity. Unfortunately for them, I found their claims to be overstated and I found a number of serious problems with Ultrasurf.

My report is available for download from the following link: [https://media.torproject.org/misc/2012-04-16-ultrasurf-analysis.pdf](https://media.torproject.org/misc/2012-04-16-ultrasurf-analysis.pdf)

Most of [my research](https://media.torproject.org/misc/2012-04-16-ultrasurf-analysis.pdf) was done while traveling in Brazil, Canada, Germany, and very small amount of it was performed in the US. Additionally, a number of interesting data points in my research paper came from interception devices in Syria. As of early April 2012, an independent tester confirmed many of my findings from China; the versions of Ultrasurf tested did directly connect to blocked addresses and did not in-fact work at all. Newer versions appear to have different, not yet blocked, addresses baked into the program.

I believe that coordinated disclosure is reasonable in most cases and I ensured that Ultrasurf was notified long before the publication of this blog post. I had a face to face meeting in early December of 2011 to discuss my findings with the lead developer of Ultrasurf and to give them time to fix the problems that I discovered. Ultrasurf updated their website to change a number of their security, privacy and anonymity claims; they did not actually remove all of the bogus claims, merely the most egregious statements. Our meeting was overall quite positive and in fact led me to write notes that may become a second paper.

However, for various reasons, I've had to sit silently on this report for nearly four full months after our December meeting. I believe it is important to ensure that the issues discovered and discussed in my paper are resolved and that users are not kept in harm's way. I have serious concerns about ongoing security issues for the users of Ultrasurf and that is my primary reason for wishing to perform and release this research for all to see.

Here's the abstract of the paper:  
_Ultrasurf is a proxy-based program promoted for Internet censorship circumvention. This report gives a technical analysis of the Ultrasurf software and network. We present the results of reverse engineering the Ultrasurf client program, give an in-depth study of the known Ultrasurf network, especially those portions that interface in some way with the client or the Internet, and discuss network signatures that would allow an adversary to detect its use on a network. We cover client bootstrapping methods, censorship and censorship resistance, anonymity, user tagging by Ultrasurf and other parties, cryptographic internals and other previously unknown or undiscovered details about the Ultrasurf client and the Ultrasurf network. We find that it is possible to monitor and block the use of Ultrasurf using commercial off-the-shelf software. In particular, BlueCoat sells software and hardware solutions with such capabilities that have been deployed in Syria and other countries._

The vulnerabilities presented in this paper are not merely theoretical in nature; they may present life-threatening danger in hostile situations. We recommend against the use of Ultrasurf for anonymity, security, privacy and Internet censorship circumvention.

The main substance of the paper takes the time to refute nearly all of the claims that UltraReach makes on their website about their software Ultrasurf:  
_This paper addresses the following claims by UltraReach and other Ultrasurf advocates about the Ultrasurf client and Ultrasurf network:_

1. “Ultrasurf enables users to browse any website freely” — refuted in Section 3.1
2. “employs a decoying mechanism to thwart any tracing effort of its communication with its infrastructure.” — refuted in Section 5.13
3. “Protect your privacy online with anonymous surfing and browsing. Ultrasurf hides your IP address, clears  
browsing history, cookies, and more.” — refuted in Section 6.2 and Section 6.3.
4. “change IP addresses a million times an hour” — refuted in Section 6.1
5. “Untraceable” — refuted in Section 6.10
6. “Unblockable: Client uses wide array of discovery mechanisms to find an available proxy server and, when necessary, to switch/hop to avoid tracking/blocking” — refuted in Section 6.8
7. “Invisible: Leaves no traces on the user’s computer, and its traffic is indistinguishable from normal access to HTTPS sites” — refuted in Section 5.12
8. “Anonymous: No registration is requires [sic], and no personally identifying information collected” — refuted in Section 6.10
9. “Tamperproof: Using privately-signed SSL certificates which dont depend on external, potentially compromised CAs (thus preempting MITM attacks), Ultrasurf proactively detects attempts by censors to reverse-engineer, sabotage, or otherwise interfere in the secure operation of the tool” — refuted in Section 5.8.

We conclude that each of these claims is false, incorrect, or misleading.

The issues involved in the writing, discussion and publication of this report are the stuff of movies. It has taken ages to publish this report and attempts at coordinated disclosure have been time consuming, largely fruitless and extremely frustrating. While some of the issues I have identified have been fixed, to the best of my knowledge the most important issues, such as a lack of forward secrecy, remain serious outstanding security issues. Ultrasurf often boasts of their decade long fight against censorship and while I respect the spirit of their efforts, I have a hard time respecting the technical implementation. I'm afraid that they've not had forward secrecy in their cryptographic protocol for that entire decade. Ultrasurf also often boasts of being untraceable when in fact they admitted to logging and disclosing user identifying logs to law enforcement when the data was requested. These kinds of security failures, both social and technical, are simply negligent and it means that users have been and are likely still in harm's way.

I firmly believe that Ultrasurf must publish their full technical specifications, peer review their designs of both obfuscation and cryptography, open their source code for the world to review and they must absolutely discontinue **all** data retention without exception.

I hope you'll enjoy the research presented in [the paper](https://media.torproject.org/misc/2012-04-16-ultrasurf-analysis.pdf) and that it will help everyone to move towards building a more secure set of options for users.

**Update:**  
UltraReach/Ultrasurf have released [a response document](http://ultrasurf.us/Ultrasurf-response-to-Tor-definitive-review.pdf) and [a response page](http://ultrasurf.us/Ultrasurf-response-to-Tor-definitive-review.html) that confirms a number of my claims, side steps a large swath of them and then attacks me, Tor and others for the report. They specifically claim that what is true in my paper is for older versions of Ultrasurf. They do not disclose which versions or when the fixes were released. This is a typical vendor tactic considering that they pressured me not to release the report until they felt they were given enough time to fix the issues involved. They also believe that I claim that Ultrasurf was broken but at no time did I ever claim it was broken; rather, I said it has problems. The claims they made and make do not live up to the implementation of policies or technical capabilities. This I think is quite reasonable because their claims were, frankly, entirely unreasonable.

I put a great deal of time and effort into disclosing these report findings to Ultrasurf - both what would be considered responsible and coordinated - it's too bad that they've decided to ignore most of the findings and to attack me over the undefendable issues.

**Another Update:** Collin Anderson has written up [his view of the disclosure process](http://b.averysmallbird.com/entries/the-need-for-community-participation-and-clear-disclosure-processes-in-the-case-of-ultrasurf). He is an independently involved third party that attempted to mediate our disclosure, solutions and a reasonable time frame for all parties involved.

