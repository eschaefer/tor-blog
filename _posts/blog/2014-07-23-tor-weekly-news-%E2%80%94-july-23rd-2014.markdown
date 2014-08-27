---
layout: post
title: "Tor Weekly News — July 23rd, 2014"
permalink: tor-weekly-news-%E2%80%94-july-23rd-2014
date: 2014-07-23
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the twenty-ninth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Tails 1.1 is out!

Tails, the Debian-based live system that protects its users’ communications by ensuring they are all sent through the Tor network, has been updated. This [new 1.1 release](https://tails.boum.org/news/version_1.1/) reminds Tails users of the [distribution’s roots in Debian](https://tails.boum.org/contribute/relationship_with_upstream/): Tails is now based on the current stable version of Debian, dubbed “Wheezy”.

This means that almost all software components have been updated. One noticeable example is the desktop environment. The user experience of the GNOME 3 in fallback mode should be similar to previous Tails versions, but things will look a bit differently than they used to.

One of the most keenly-awaited features of this new version is the support for UEFI firmware. Mac users now have only to [press the Alt key](https://tails.boum.org/doc/first_steps/start_tails/#usb-mac) while booting their computer to start Tails from a DVD or USB stick. The same goes for owners of computers displaying “Windows 8” stickers. And, talking of Windows 8, the [camouflage mode](https://tails.boum.org/doc/first_steps/startup_options/windows_camouflage/) has been updated to look more like it, instead of the now discontinued XP.

This new release also contains [security fixes](https://tails.boum.org/security/Numerous_security_holes_in_1.0.1), and minor tweaks over the previous versions.

Because of the newly-introduced support for UEFI and the amount of upgraded software, incremental upgrades will not be offered for Tails 1.1. A full upgrade is needed through the Tails Installer. The safest method for upgrading Tails sticks is to go through a freshly burned DVD. Be sure to have a look at the list of [known issues](https://tails.boum.org/news/version_1.1/#index2h1) to learn about other oddities that might happen in the process.

# PETS 2014

The fourteenth Privacy Enhancing Technologies Symposium was held in Amsterdam, Netherlands, July 16-18, 2014. A wide range of research in privacy enhancing technologies was presented, with many of relevance to Tor. Keynotes were given by Martin Ortlieb, Senior User Experience Researcher in Privacy at Google, and William Binney, a former NSA employee.

Some papers focusing on Tor include:

- [Spoiled Onions: Exposing Malicious Tor Exit Relays](https://petsymposium.org/2014/papers/Winter.pdf) by Philipp Winter, Richard Köwer, Martin Mulazzani, Markus Huber, Sebastian Schrittwieser, Stefan Lindskog, and Edgar Weippl
- [One Fast Guard for Life (or 9 months)](https://petsymposium.org/2014/papers/Dingledine.pdf) by Roger Dingledine, Nicholas Hopper, George Kadianakis, and Nick Mathewson
- [From Onions to Shallots: Rewarding Tor Relays with TEARS](https://petsymposium.org/2014/papers/Jansen.pdf) by Rob Jansen, Andrew Miller, Paul Syverson, and Bryan Ford
- [A TorPath to TorCoin: Proof-of-Bandwidth Altcoins for Compensating Relays](https://petsymposium.org/2014/papers/Ghosh.pdf) by Mainak Ghosh, Miles Richardson, Bryan Ford, and Rob Jansen
- [Measuring the Leakage of Onion at the Root, A measurement of Tor’s .onion pseudo-top-level domain in the global domain name system](https://petsymposium.org/2014/papers/Thomas.pdf) by Matthew Thomas and Aziz Mohaisen

Also announced at PETS was the 2014 PET Award for Outstanding Research in Privacy Enhancing Technologies, for [A Scanner Darkly: Protecting User Privacy From Perceptual Applications](https://freedom-to-tinker.com/blog/shmat/a-scanner-darkly-protecting-user-privacy-from-perceptual-applications/) by Suman Jana, Arvind Narayanan†, and Vitaly Shmatikov. The winner of the best student paper at PETS was [I Know Why You Went to the Clinic: Risks and Realization of HTTPS Traffic Analysis](https://petsymposium.org/2014/papers/Miller.pdf) by Brad Miller, Ling Huang, A. D. Joseph and J. D. Tygar .

Prior to PETS, there was a Tor meet-up which Moritz Bartl reported as a [great success](https://lists.torproject.org/pipermail/tor-talk/2014-July/033936.html). Hopefully there will also be such an event at the 2015 PETS, to be held in Philadelphia, US, in the week of June 29, 2015.

# Miscellaneous news

[txtorcon](https://pypi.python.org/pypi/txtorcon), the Tor control protocol implementation for the [Twisted framework](https://twistedmatrix.com/), received a [new minor release](https://lists.torproject.org/pipermail/tor-dev/2014-July/007166.html). Version 0.10.1 fixes “a couple bugs introduced along with the endpoints feature in 0.10.0”.

Roger Dingledine [posted](https://blog.torproject.org/blog/recent-black-hat-2014-talk-cancellation) an official reaction to the cancellation of a proposed talk at the upcoming Blackhat2014 conference dealing with possible deanonymization attacks on Tor users and hidden services.

Tor ships with a [sample webpage](https://gitweb.torproject.org/tor.git/blob_plain/HEAD:/contrib/operator-tools/tor-exit-notice.html) that can be used by exit node operators to identify their system as such to anyone wishing to identify the source of Tor traffic. Operators most often copy and adapt this template to the local situation. Mick Morgan discovered than his version was [out of sync](https://lists.torproject.org/pipermail/tor-relays/2014-July/004982.html) and contained broken links. “If other operators are similarly using a page based on the old template, they may wish to update”, Mick advised.

Michael Rogers, one of the developers of [Briar](https://briarproject.org/), [announced](https://lists.torproject.org/pipermail/tor-dev/2014-July/007161.html) a [new mailing list](https://fulpool.org/cgi-bin/mailman/listinfo/hidden-services) for discussing peer-to-peer-based communication systems based on Tor hidden services. As Briar and other systems might be “running into similar issues”, a shared place to discuss them seemed worthwhile.

Karsten Loesing and Philipp Winter are [looking for front-end web developers](https://blog.torproject.org/blog/looking-front-end-web-developers-network-status-websites-atlas-and-globe): “We are looking for somebody to fork and extend one of the two main Tor network status websites [Atlas](https://atlas.torproject.org/) or [Globe](https://globe.torproject.org/)” writes Karsten. Both websites currently need love and new maintainers. Please reach out if you want to help!

The database which holds Tor bridges, usually called [BridgeDB](https://gitweb.torproject.org/bridgedb.git), is able to give out bridge addresses through email. This feature was recently extended to make the email autoresponder support more bridge types, which required introducing new keywords that must be used in the initial request. Matthew Finkel is looking for [feedback](https://lists.torproject.org/pipermail/tor-dev/2014-July/007164.html) on the current set of commands and how they could be improved.

Lunar wrote a [detailed report](https://lists.torproject.org/pipermail/tor-reports/2014-July/000593.html) on his week at the Libre Software Meeting in Montpellier, France. The report covers the booth jointly held with [Nos Oignons](https://nos-oignons.net/), his talk in the security track, and several contacts made with other free software projects.

Here’s another round of reports from Google Summer of Code students: the mid-term: Amogh Pradeep on [Orbot and Orfox improvements](https://lists.torproject.org/pipermail/tor-dev/2014-July/007152.html), Israel Leiva on the [GetTor revamp](https://lists.torproject.org/pipermail/tor-dev/2014-July/007156.html), Quinn Jarrell on the [pluggable transport combiner](https://lists.torproject.org/pipermail/tor-dev/2014-July/007157.html), Juha Nurmi on the [ahmia.fi project](https://lists.torproject.org/pipermail/tor-reports/2014-July/000594.html), Marc Juarez on [website fingerprinting defenses](https://lists.torproject.org/pipermail/tor-reports/2014-July/000595.html), and Daniel Martí on [incremental updates to consensus documents](https://lists.torproject.org/pipermail/tor-dev/2014-July/007163.html).

Tim Retout [announced](http://retout.co.uk/blog/2014/07/21/apt-transport-tor) that [apt-transport-tor](https://tracker.debian.org/pkg/apt-transport-tor) 0.2.1 has entered Debian unstable. This package enables APT to download Debian packages through Tor.

[Atlas](https://atlas.torproject.org/) can now also be used to search for Tor bridges. In the past, Atlas was only able to search for relays. This was made possible thanks to [a patch](https://bugs.torproject.org/6320) developed by Dmitry Eremin-Solenikov.

Thanks to [Tim Semeijn](https://lists.torproject.org/pipermail/tor-mirrors/2014-July/000642.html) and [Tobias Bauer](https://lists.torproject.org/pipermail/tor-mirrors/2014-July/000646.html) for setting up new mirrors of the Tor Project’s website and its software.

# Tor help desk roundup

Some Linux users have experienced missing dependency errors when trying to install Tor Browser from their operating system’s software repositories. Tor Browser should only be installed from the Tor Project’s website, and never from a software repository. In other words, using apt-get or yum to install Tor Browser is discouraged. Downloading and verifying Tor Browser from the Tor Project website allows users to keep up with important security updates as they are released.

# News from Tor StackExchange

user3224 wants to log in to its Google, Microsoft etc. accounts and wonders [if they will know the real name and other personal information](https://tor.stackexchange.com/q/3603/88). Roya and mirimir explained that if someone logs into an already personalized account Tor can’t anonymize this user. Instead it might be wise to use Tor to register a pseudonym and also use an anonymous operating system like Tails or Whonix.

escapologybb has set up a Raspberry Pi. It serves as SOCKS proxy for the internal network. While everyone can use it, escapologybb asks what the security implications are and [if this lowers the overall anonymity](https://tor.stackexchange.com/q/3596/88). If you know a good answer please share your knowledge with the users of Tor StackExchange.

* * *

This issue of Tor Weekly News has been assembled by Lunar, Steven Murdoch, harmony, Philipp Winter, Matt Pagan, qbi, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

