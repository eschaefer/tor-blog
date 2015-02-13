---
layout: post
title: "PRISM vs Tor"
permalink: prism-vs-tor
date: 2013-06-08 18:59:22
author: mikeperry
category: blog
status: closed
tags: ["decentralization", "hidden-services", "National Insecurity Agency", "nsa", "surveillance", "ya-basta"]
---

By now, just about everybody has heard about the [PRISM surveillance program](https://en.wikipedia.org/wiki/PRISM_%28surveillance_program%29), and many are beginning to speculate on its impact on Tor.

Unfortunately, there still are a lot of gaps to fill in terms of understanding what is really going on, especially in the face of conflicting information between the [primary source material](http://www.washingtonpost.com/wp-srv/special/politics/prism-collection-documents/) and Google, Facebook, and Apple's claims of non-involvement.

This apparent conflict means that it is still hard to pin down exactly how the program impacts Tor, and is leading many to assume worst-case scenarios.

For example, some of the worst-case scenarios include the NSA using [weaponized exploits](http://www.reuters.com/article/2013/05/10/us-usa-cyberweapons-specialreport-idUSBRE9490EL20130510) to compromise datacenter equipment at these firms. Less severe, but still extremely worrying possibilities include issuing gag orders to mid or low-level datacenter staff to install backdoors or monitoring equipment without any interaction what-so-ever with the legal and executive staff of the firms themselves.

We're going to save analysis of those speculative and invasive scenarios for when more information becomes available (though we may independently write a future blog post on [the dangers](http://www.thebulletin.org/web-edition/op-eds/cyberweapons-bold-steps-digital-darkness) of the government use of weaponized exploits).

For now, let's review what Tor can do, what tools go well with Tor to give you defense-in-depth for your communications, and what work needs to be done so we can make it easier to protect communications from instances where the existing centralized communications infrastructure is compromised by the NSA, China, Iran, or by anyone else who manages to get ahold of the keys to the kingdom.

  
The core Tor software's job is to conceal your identity from your recipient, and to conceal your recipient and your content from observers on your end. By itself, Tor does not protect the actual communications content once it leaves the Tor network. This can make it useful against some forms of metadata analysis, but this also means Tor is best used in combination with other tools.

Through the use of [HTTPS-Everywhere](https://www.eff.org/https-everywhere) in [Tor Browser](https://www.torproject.org/download/download-easy.html), in many cases we can protect your communications content where parts of the Tor network and/or your recipients' infrastructure are compromised or under surveillance. The EFF has created an [excellent interactive graphic](https://www.eff.org/pages/tor-and-https) to help illustrate and clarify these combined properties.

Through the use of combinations of additional software like [TorBirdy](https://addons.mozilla.org/en-us/thunderbird/addon/torbirdy/) and [Enigmail](http://www.enigmail.net/home/index.php), [OTR](https://en.wikipedia.org/wiki/Off-the-Record_Messaging#Client_support), and [Diaspora](https://joindiaspora.com/), Tor can also protect your communications content in cases where the communications infrastructure (Google/Facebook) is compromised.

  
However, the real interesting use cases for Tor in the face of dragnet surveillance like this is not that Tor can protect your gmail/facebook accounts from analysis (in fact, Tor could never really protect account usage metadata), but that Tor and hidden services are actually a key building block to build systems where it is no longer possible to go to a single party and obtain the full metadata, communications frequency, \*or\* contents.

Tor hidden services are arbitrary communications endpoints that are resistant to both metadata analysis and surveillance.

A simple (to deploy) example of a hidden service based mechanism to significantly hinder exactly this type of surveillance is an [XMPP](https://en.wikipedia.org/wiki/Xmpp) client that also ships with an XMPP server and a Tor hidden service. Such a P2P communication system (where the clients are themselves the servers) is both end-to-end secure, and does \*not\* have a single central server where metadata is available. This communication is private, pseudonymous, and does not have involve any single central party or intermediary.

More complex examples would include the use of [Diaspora](https://en.wikipedia.org/wiki/Diaspora_%28software%29) and other [decentralized social network protocols](https://en.wikipedia.org/wiki/Comparison_of_software_and_protocols_for_distributed_social_networking) with hidden service endpoints.

  
Despite these compelling use cases and powerful tool combination possibilities, the Tor Project is under no illusion that these more sophisticated configurations are easy, usable, or accessible by the general public.

We recognize that a lot of work needs to be done even for the basic tools like Tor Browser, TorBirdy, EnigMail, and OTR to work seamlessly and securely for most users, let alone complex combinations like XMPP or Diaspora with Hidden Services.

Additionally, hidden services themselves are in need of [quite a bit of development assistance](https://blog.torproject.org/blog/hidden-services-need-some-love) just to maintain their originally designed level of security, let alone scaling to support large numbers of endpoints.

Being an Open Source project with limited resources, we welcome contributions from the community to make any of this software work better with Tor, or to help improve the Tor software itself.

If you're not a developer, but you would still like to help us succeed in our mission of securing the world's communications, [please donate!](https://www.torproject.org/donate/donate.html.en) It is a rather big job, after all.

  
We will keep you updated as we learn more about the exact capabilities of this program.
