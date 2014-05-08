---
layout: post
title: "Tor Weekly News — April 16th, 2014"
permalink: tor-weekly-news-%E2%80%94-april-16th-2014
date: 04/16/2014
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the fifteenth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# New beta version of Tor Browser 3.6

The [second beta version of the next major Tor Browser release](https://blog.torproject.org/blog/tor-browser-36-beta-2-released) is out. Version 3.6 main highlight is the seamless integration of [pluggable transports](https://www.torproject.org/docs/pluggable-transports.html) in the browser.

The update is important to users already using version 3.6-beta1 as it contains an updated OpenSSL to address potential client-side vectors for [CVE-2014-0160](https://blog.torproject.org/blog/openssl-bug-cve-2014-0160) (also known as “Heartbleed”).

The new beta also features “a Turkish language bundle, experimental Javascript hardening options, fixes for pluggable transport issues, and a fix for improper update notification while extracting the bundle over an already existing copy.”

Jump to the release announcement to know more. Enjoy the [update](https://www.torproject.org/dist/torbrowser/3.6-beta-2/) and report any bug you may find.

# Key rotation at every level

The “Heartbleed” issue forces system administrators to consider private keys of network-facing applications affected by the bug as compromised. As Tor has no shortage of private keys in [its design](https://gitweb.torproject.org/torspec.git), a serious number of new keys has to be generated.

Roger Dingledine [prompted](https://lists.torproject.org/pipermail/tor-relays/2014-April/004256.html) relay operators to get new identity keys, “especially from the big relays, and we’ll be happier tolerating a couple of bumpy days while the network recovers”. Switching to a new relay identity key means that the relay is [seen as new](https://blog.torproject.org/blog/lifecycle-of-a-new-relay) to the authorities again: they will lose their Guard status and bandwidth measurement. It seems that a number of operators followed the advice, as [the network lost around 1 Gbit/s of advertised capacity between April 7th and April 10th](https://metrics.torproject.org/network.html?graph=bandwidth&start=2014-04-01&end=2014-04-15#bandwidth).

For a brighter future if such massive RSA1024 relay key migration is ever again in order, Nick Mathewson wrote [proposal 230](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/230-rsa1024-relay-id-migration.txt). The proposal describes a mechanism for relays to advertise their old identity to directory authorities and clients.

Directory authorities can currently tie a relay’s nickname to its identity key with the Named flag. That feature proved to be less helpful than it seemed, and can subject its users to impersonation attacks. As relays switch to new identity keys, those who keep the same name will lose their Named flag for the next six months. So now [seems](https://lists.torproject.org/pipermail/tor-relays/2014-April/004254.html) a good time to “throw out the Named and Unnamed flags entirely”. Sebastian Hahn acted on the idea and [started a draft proposal](https://lists.torproject.org/pipermail/tor-dev/2014-April/006671.html).

How should potentially compromised relays which have not switched to a new key be handled? On April 8th, grarpamp [observed](https://lists.torproject.org/pipermail/tor-relays/2014-April/004259.html) that more than 3000 relays had been restarted — hopefully to use the fixed version of OpenSSL. It is unknown how many of those relays have switched to a new key since. Andrea Shepard has been working on a [survey](http://charon.persephoneslair.org/~andrea/private/tor-heartbleed-survey/) to identify them. What is known though are relays that are unfortunately still vulnerable. Sina Rabbani has set up a [visible list for guards and exits](https://encrypted.redteam.net/bleeding_edges/). To protect Tor users, directory authority operators have started to [reject descriptors for vulnerable relays](https://lists.torproject.org/pipermail/tor-relays/2014-April/004336.html).

The identity keys for directory authorities are kept offline. But they are used to certify medium-term signing keys. Roger Dingledine’s  
 [analysis](https://lists.torproject.org/pipermail/tor-dev/2014-April/006663.html) reports “two (moria1 and urras) of the directory authorities were unaffected by the openssl bug, and seven were affected”.

At the time of writing, five of the seven affected authorities had new signing keys. In the meantime, Nick and Andrea have been busy writing code to [prevent the old keys from being accepted by Tor clients](https://bugs.torproject.org/11464).

Changing the relay identity keys of the directory authorities has not been done so far “because current clients expect them to be at their current IP:port:fingerprint and would scream in their logs and refuse to connect if the relay identity key changes”. The specification of the missing piece of code to allow a smoother transition has been written by Nick Mathewson in [proposal 231](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/231-migrate-authority-rsa1024-ids.txt).

Finally, [hidden service operators are also generating new keys](https://twitter.com/freenodestaff/status/455425032203022337). Unfortunately, this forces every user of the service to update the address in their bookmarks or configuration.

As Roger summarized it: “fun times”.

# More monthly status reports for March 2014

The wave of regular monthly reports from Tor project members for the month of March continued, with submissions from [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2014-April/000505.html), [Roger Dingledine](https://lists.torproject.org/pipermail/tor-reports/2014-April/000507.html), and [Kelley Misata](https://lists.torproject.org/pipermail/tor-reports/2014-April/000508.html).

Roger also sent out the [report for SponsorF](https://lists.torproject.org/pipermail/tor-reports/2014-April/000506.html), and the Tails team reported on [its progress](https://tails.boum.org/news/report_2014_03/).

# Miscellaneous news

CVE-2014-0160 prompted Anthony Basile to [release version 20140409](https://lists.torproject.org/pipermail/tor-talk/2014-April/032642.html) of Tor-ramdisk. OpenSSL has been updated and so has the kernel. Upgrading is strongly recommended.

David Fifield [released new browser bundles configured to use the meek](https://lists.torproject.org/pipermail/tor-qa/2014-April/000390.html) transport automatically. These bundles “use a web browser extension to make the HTTPS requests, so that the TLS layer looks like Firefox” — [because it is Firefox](https://lists.torproject.org/pipermail/tor-dev/2014-April/006662.html). Meek is a promising censorship circumvention solution, so please try them!

The Tails developers [announced](https://tails.boum.org/news/and_the_winner_is/) that Tchou’s proposal is the winner of the recent Tails logo contest: “in the coming days we will keep on fine-tuning it and integrating it in time for Tails 1.0. So don’t hesitate to comment on it.”

Andrew Lewman [reported on his week in Stockholm](https://lists.torproject.org/pipermail/tor-reports/2014-April/000504.html) for the [Civil Rights Defender’s](https://www.civilrightsdefenders.org/) Defender’s Days where he trained activists and “learned more about the situation in Moldova, Transnistria, Burma, Vietnam, and Bahrain”.

Andrew also [updated the instructions for mirror operators](https://lists.torproject.org/pipermail/tor-mirrors/2014-April/000534.html) wishing to have their sites listed on the Tor Project website. Thanks to [Andreas Reich](https://lists.torproject.org/pipermail/tor-mirrors/2014-April/000536.html), [Sebastian M. Bobrecki](https://lists.torproject.org/pipermail/tor-mirrors/2014-April/000537.html), and [Jeremy L. Gaddis ](https://lists.torproject.org/pipermail/tor-mirrors/2014-April/000541.html) for running new mirrors!

Arlo Breault [announced](https://lists.torproject.org/pipermail/tor-dev/2014-April/006661.html) the release of [Bulb](https://github.com/arlolra/bulb), a Tor relay web status dashboard. “There’s not much to it yet, but I thought I’d share […] Contributions welcome!”

Alan Shreve [requested](https://lists.torproject.org/pipermail/tor-dev/2014-April/006657.html) feedback on “Shroud”, a proposal for “a new system to provide public hidden services […] whose network location cannot be determined (like Tor hidden services) but are accessible by any client on the internet”.

# Tor help desk roundup

Users often ask for steps they can take to maximize their anonymity while using Tor. Tips for staying anonymous when using Tor are visible on the [download page](https://www.torproject.org/download/download#warning).

# News from Tor StackExchange

Jack Gundo uses Windows 7 with the built-in firewall and wants to [block all traffic except Tor traffic](https://tor.stackexchange.com/q/1882/88). Guest suggested that on a closed-source system one can never be sure that all traffic really is blocked, so the original poster might be better off using a router which does the job. Another possible solution is PeerBlock, which also allows you to block all traffic from a machine.

Broot uses obfs3 to route OpenVPN traffic and [can’t get obfsproxy running](https://tor.stackexchange.com/q/693/88) because the latest version only implements SOCKS4. Yawning Angel answered that version 0.2.7 of obfsproxy uses SOCKS5 and works with OpenVPN. However there is [a bug that needs to be worked around](https://lists.torproject.org/pipermail/tor-dev/2014-March/006427.html).

* * *

This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, qbi, Roger Dingledine, Karsten Loesing and the Tails team.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

