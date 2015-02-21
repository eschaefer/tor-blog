---
layout: post
title: "Tor Weekly News — December 17th, 2014"
permalink: tor-weekly-news-—-december-17th-2014
date: 2014-12-17 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the fiftieth issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Solidarity against online harassment
====================================

Following “a sustained campaign of harassment” directed at a core Tor developer over the past few months, the Tor Project published a [statement](https://blog.torproject.org/blog/solidarity-against-online-harassment) in which it declared “support for her, for every member of our organization, and for every member of our community who experiences this harassment”: “In categorically condemning the urge to harass, we mean categorically: we will neither tolerate it in others, nor will we accept it among ourselves. We are dedicated to both protecting our employees and colleagues from violence, and trying to foster more positive and mindful behavior online ourselves… We are working within our community to devise ways to concretely support people who suffer from online harassment; this statement is part of that discussion. We hope it will contribute to the larger public conversation about online harassment and we encourage other organizations to sign on to it or write one of their own.”

As of this writing, there are 448 signatories to the statement, including Tor developers and community members, academics, journalists, lawyers, and many others who are lending their support to this movement in its early stages. If you want to add your name to the list, please send an email to [tor-assistants@lists.torproject.org](mailto:tor-assistants@lists.torproject.org).

Tails 1.2.2 is out
==================

The Tails team [announced](https://tails.boum.org/news/version_1.2.2/) a pointfix release of the amnesic live operating system. The only difference between this version and the recent 1.2.1 release is that the automatic Tails Updater now expects a different certificate authority when checking for a new Tails version. As the team explained, “On January 3rd, the SSL certificate of our website hosting provider, boum.org, will expire. The new certificate will be issued by a different certificate authority […] As a consequence, versions previous to 1.2.2 won’t be able to do the next automatic upgrade to version 1.2.3 and will receive an error message from Tails Upgrader when starting Tails after January 3rd”.

This, along with a [bug](https://labs.riseup.net/code/issues/8449) that prevents automatic updates from 1.2.1 to 1.2.2, means that all Tails users will need to upgrade manually: either to version 1.2.2 before January 3rd or (if for some reason that is not possible) to version 1.2.3 following its release on January 14th. Please see the team’s post for more details and download instructions.

Miscellaneous news
==================

George Kadianakis, Karsten Loesing, Aaron Johnson, and David Goulet [requested feedback](https://lists.torproject.org/pipermail/tor-dev/2014-December/007968.html) on the design and code they have developed for the [Tor branch](https://gitweb.torproject.org/karsten/tor.git/log/?h=task-13192-5) that will enable the collection of statistics on Tor hidden services, hoping to answer the questions “Approximately how many hidden services are there?” and “Approximately how much traffic in the Tor network is going to hidden services?”: “Our plan is that in approximately a week we will ask volunteers to run the branch. Then in a month from now we will use those stats to write a blog post about the approximate size of Tor hidden services network and the approximate traffic it’s pushing.” Please join in with your comments on the relevant [ticket](https://bugs.torproject.org/13192)!

Philipp Winter [announced](https://lists.torproject.org/pipermail/tor-dev/2014-December/007973.html) an early version of “zoossh”, which as the name implies is a speedy parser written in Go that will help to “detect sybils and other anomalies in the Tor network” by examining Tor’s archive of network data. While it is not quite ready for use, “I wanted folks to know that I’m working on that and I’m always happy to get feedback and patches.”

Yawning Angel [announced](https://lists.torproject.org/pipermail/tor-dev/2014-December/007977.html) the existence of “basket”, a “stab at designing something that significantly increases Tor’s resistance to upcoming/future attacks”, combining post-quantum cryptographic primitives with “defenses against website fingerprinting (and possibly end-to-end correlation) attacks”. You can read full details of the cryptographic and other features of “basket” in Yawning’s post, which is replete with warnings against using the software at this stage: “It’s almost at the point where brave members of the general public should be aware that it exists as a potential option in the privacy toolbox… [but] seriously, unless you are a developer or researcher, you REALLY SHOULD NOT use ‘basket’.” If you are gifted or foolhardy enough to ignore Yawning’s advice and test “basket” for yourself, please let the [tor-dev mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-dev) know what you find.

Sukhbir Singh and Arlo Breault [requested feedback](https://lists.torproject.org/pipermail/tor-dev/2014-December/007981.html) on an alpha version of Tor Messenger. It is an instant messaging client currently under development that intends to send all traffic over Tor, use Off-the-Record (OTR) encryption of conversations by default, work with a wide variety of chat networks, and have an easy-to-use graphical user interface localized into multiple languages.

TheCthulhu announced that his mirrors of two Tor network tools are now [available over Tor hidden services](https://lists.torproject.org/pipermail/tor-talk/2014-December/035982.html). [Globe](https://globe.thecthulhu.com) can be accessed via [http://globe223ezvh6bps.onion](http://globe223ezvh6bps.onion "http://globe223ezvh6bps.onion") and [Atlas](https://atlas.thecthulhu.com) via [http://atlas777hhh7mcs7.onion](http://atlas777hhh7mcs7.onion "http://atlas777hhh7mcs7.onion"). The mirrors provided by the Cthulhu run on their own instance of Onionoo, so in the event that the primary sites hosted by Tor Project are offline, both of these new mirrors should still be available for use either through the new hidden services or through regular clearnet access.

The Tails team [published](https://mailman.boum.org/pipermail/tails-dev/2014-December/007632.html) a signed list of SHA256 hashes for every version of Tails (and its predecessor, amnesia) that it had either built or verified at the time of release.

Vlad Tsyrklevich [raised](https://lists.torproject.org/pipermail/tor-dev/2014-December/007957.html) the issue of the discoverability risk posed to Tor bridges by the default setting of their ORPorts to 443 or 9001. Using data from Onionoo and internet-wide scans, Vlad found that “there are 4267 bridges, of which 1819 serve their ORPort on port 443 and 383 serve on port 9001. That’s 52% of tor bridges. There are 1926 pluggable-transports enabled bridges, 316 with ORPort 443 and 33 with ORPort 9001. That’s 18% of Tor bridges… I realized I was also discovering a fair amount of private bridges not included in the Onionoo data set.” Vlad recommended that operators be warned to change their ORPorts away from the default; Aaron Johnson [suggested](https://lists.torproject.org/pipermail/tor-dev/2014-December/007959.html) possible alternative solutions, and Philipp Winter [remarked](https://lists.torproject.org/pipermail/tor-dev/2014-December/007963.html) that while bridges on port 443 “would easily fall prey to Internet-wide scanning”, “they would still be useful for users behind captive portals” and other adversaries that restrict connections to a limited range of ports.

Alden Page [announced](https://lists.torproject.org/pipermail/tor-talk/2014-December/035989.html) that development will soon begin on a free-software tool to counteract “stylometry” attacks, which attempt to deanonymize the author of a piece of text based on their writing style alone. “I hope you will all agree that this poses a significant threat to the preservation of the anonymity of Tor users”, wrote Alden. “In the spirit of meeting the needs of the privacy community, I am interested in hearing what potential users might have to say about the design of such a tool.” Please see Alden’s post for further discussion of stylometry attacks and the proposed countermeasures, and feel free to respond with your comments or questions.

Tor help desk roundup
=====================

Because Tor Browser prevents users from running it as root, Kali Linux users starting Tor Browser will see an error message saying Tor should not be run as root.

In Kali, all userspace software runs as root by default. To run Tor Browser in Kali Linux, create a new user account just for using Tor Browser. Unpack Tor Browser and chown -R your whole Tor Browser directory. Run Tor Browser as your created Tor Browser user account.

* * * * *

This issue of Tor Weekly News has been assembled by Harmony, TheCthulhu, Matt Pagan, Arlo Breault, and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
