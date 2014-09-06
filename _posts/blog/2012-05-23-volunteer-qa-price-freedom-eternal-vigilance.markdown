---
layout: post
title: "Volunteer QA: The Price of Freedom is Eternal Vigilance"
permalink: blog/volunteer-qa-price-freedom-eternal-vigilance
date: 2012-05-23
author: mikeperry
category: blog
tags: ["qa", "security", "tbb"]
---

We have a dream. We believe it is possible to produce free, secure privacy software that is regularly used by many millions of ordinary people all over the world. They will use it to inform themselves, explore new and controversial ideas, communicate with one another, and safely share things about their lives. They will do so with confidence that so long as the software rests upon a secure foundation, it will not betray them; in fact it \*cannot\* betray them, by design.

Tor Browser Bundle can be that software. Sadly, we know that it is not yet that software. We're aware that many aspects of the Bundle are either imperfect, incomplete, or absent entirely. We intend to work as hard as we can to improve this situation.

However, we also know that even the keystone of true security is not yet properly in place. We know that we must properly deploy this keystone, or we risk the collapse of everything we have built so far.

That keystone is the community that reviews our designs. It is the community that audits our source code. It is the community that tests the binaries produced from that source code. It is the community that will verify that the binaries that we distribute are produced from that source code and nothing else.

It is time to organize our community into place to serve as that keystone. We cannot have true security without it.

Our plan is to start small, with manual testing and manual analysis of each build. We will use that to incrementally work towards full automation available to be run on any of the arbitrary platform configurations available to the community. Runa Sandvik will begin coordinating these releases.

We expect the process to be bumpy at first. To start, Runa will simply give interested people a url to a release candidate with a [grab bag of urls](https://trac.torproject.org/projects/tor/ticket/5292) along with some basic tests to perform within some time limit before the build is to be released. These urls will initially come from arbitrary pages around the web, but hopefully we'll eventually distill them into our own collection of minimal test cases for which testing is fully automated. Until that point, test pages will need to come with a description of expected behavior and results. We're hoping that the community will also seek out new and useful test urls and write up result descriptions for them.

We will soon be switching to the 10.x-ESR Firefox branch for our stable TBBs, while concurrently maintaining an alpha series based on Rapid Release. To minimize the incidence of surprise issues in the stable TBB when ESR undergoes major upgrades, we will need people devoted to testing both branches on multiple platforms. We will also need people running [auditing systems that verify the TBB they test is well behaved](https://trac.torproject.org/projects/tor/ticket/5791).

To participate, please inform Runa via email (runa at torproject.org) which TBB branch or branches you intend to test on which platform (Operating System and CPU). Bonus points if you have a unique configuration such as AntiVirus software, and/or are able to analyze TBB in an auditing sandbox framework such as Seatbelt, AppArmor, SELinux, a firewall that will log proxy bypass attempts, or simply with Wireshark or any other network analyzer. Extra bonus points if you [document your setup for others to use](https://trac.torproject.org/projects/tor/ticket/5767).

Independent from the group Runa will coordinate, we also need people [analyzing our builds](https://trac.torproject.org/projects/tor/ticket/5837), to ensure against tampering at the build machines themselves. We need to use the differences uncovered by this analysis to work towards the ability to [produce identical binaries on multiple, clean instances of build platforms](https://trac.torproject.org/projects/tor/ticket/3688) which can be brought up from scratch anywhere around the world.

To help us get started, we will also need people who simply create independent builds for others to compare against our official builds. I suspect that many reversers and hobbyists interested in learning reversing may find devoting the system resources and time to build their own TBB binaries a prohibitive barrier.

Basically, everyone should try to help eliminate the need for duplicate work done by others at each step of both the QA and build inspection processes. Similarly, we should be constantly looking to refine our testing and analysis processes to eliminate manual labor.

Thank you all for you willingness to help. Let's work together to build the world we want to live in.

