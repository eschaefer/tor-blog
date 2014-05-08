---
layout: post
title: "Tor Weekly News — April 23rd, 2014"
permalink: tor-weekly-news-%E2%80%94-april-23rd-2014
date: 04/23/2014
author: harmony
category: blog
tags: ["tor weekly news"]
---

Welcome to the sixteenth issue of Tor Weekly News in 2014, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what is happening in the Tor community.

# Cutting out relays running version 0.2.2.x

Tor relays running the now ancient Tor 0.2.2.x are scheduled to be [removed from the consensus](https://bugs.torproject.org/11149). The change has already been merged in the master branch and will be out with the next Tor 0.2.5 alpha.

Even if most relay operators have been warned, the change has not yet been widely announced. But as three directory authorities are already not voting for the deprecated versions, the downtime of two others while cleaning up after the OpenSSL “Heartbleed” issue was sufficient to get these relays removed from the consensus [for a couple of days](https://metrics.torproject.org/network.html?graph=versions&start=2014-04-01&end=2014-04-23#versions), as Roger Dingledine [explained](https://lists.torproject.org/pipermail/tor-relays/2014-April/004422.html).

Eventually relays running versions prior to 0.2.3.16-alpha might also be removed from the consensus. “I think 0.2.3.16-alpha’s fix of #6033 makes that one a plausible ’not below this one’ cutoff”, Roger writes in the [relevant Trac entry](https://bugs.torproject.org/11149#comment:7).

Relay operators should always make sure to run a [recommended Tor version](https://consensus-health.torproject.org/#recommendedversions). The [Tor Weather service](https://weather.torproject.org/subscribe/) can be used by relay operators to get email notifications if an outdated version is detected.

# Miscellaneous news

Nathan Freitas [announced](https://lists.mayfirst.org/pipermail/guardian-dev/2014-April/003436.html) the third (and probably final) release candidate for Orbot 13.0.6: “The big improvements in this build are a fix for the disconnected UI/activity (Tor is on, but UI shows off), and improvements to the transparent proxying iptables scripts”.

The Tails developers put out two calls for testing: the [first](https://tails.boum.org/news/test_1.0-rc1/index.en.html) is for the first release candidate of Tails 1.0; while the [second](https://tails.boum.org/news/test_UEFI/index.en.html) is for UEFI support, which “allows you to start Tails using a USB stick on recent hardware, and especially on Mac”. “Test wildly”, and report any bugs you find!

Andrea Shepard [sent](https://lists.torproject.org/pipermail/tor-relays/2014-April/004340.html) a list of 1777 fingerprints for relays “which have ever turned up as potentially exposed by Heartbleed”. It appears that enough directory authority operators now [reject relays known to be problematic](https://lists.torproject.org/pipermail/tor-relays/2014-April/004362.html): sssheep [reported](https://lists.torproject.org/pipermail/tor-talk/2014-April/032762.html) that the still-vulnerable section of the network was down to 0.01% of the consensus weight.

Mick [drew attention](https://lists.torproject.org/pipermail/tor-relays/2014-April/004414.html) to the fact that in its current state, [arm](https://www.atagar.com/arm/) — the command-line relay status monitor — wrongly advises relay operators to run it with the same user as Tor, in order to access information about the relay’s connections. This is in fact a very bad idea, and a [ticket](https://bugs.torproject.org/10702) is already open to address this issue. Lunar [detailed](https://lists.torproject.org/pipermail/tor-relays/2014-April/004412.html) the correct method of doing this, which is also explained in the ticket.

On the tor-relays mailing list, David Stainton [mentioned](https://lists.torproject.org/pipermail/tor-relays/2014-April/004373.html) his [Tor role](https://github.com/david415/ansible-tor) for the [Ansible automation tool](http://www.ansible.com/). David hoped that “relay operators will find this useful for deploying and maintaining large numbers of Tor relays and bridges”. The documentation specifies that it currently works with Debian and Ubuntu systems, and contains several configuration examples.

David Fifield continued his progress on [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek), a pluggable transport “that routes your traffic through a third-party web service in a way that should be difficult to block”. David sent a [call for wider testing](https://lists.torproject.org/pipermail/tor-dev/2014-April/006718.html) of experimental Tor Browser builds and a call for [reviews of the code](https://lists.torproject.org/pipermail/tor-dev/2014-April/006719.html). “There are a lot of components that make up the meek transport […] This is your chance to get in on the ground floor of a new transport!”

Ximin Luo [raised](https://lists.torproject.org/pipermail/tor-dev/2014-April/006689.html) several points regarding how “indirect” pluggable transports like [flashproxy](http://crypto.stanford.edu/flashproxy/) or meek are currently handled by Tor. Whereas obfs3 or ScrambleSuit connect directly to the specified peer, transforming the data flow along the way, Ximin describes meek and flashproxy as providing “the metaphor of connecting to a global homogeneous service”. The latter being “incompatible with the metaphor of connecting to a specific endpoint”. Solutions on how to make the design, code, and configuration better are up for discussion.

Nicolas Vigier submitted his [status report for March](https://lists.torproject.org/pipermail/tor-reports/2014-April/000510.html).

Philipp Winter [relayed](https://blog.torproject.org/blog/call-papers-foci14-workshop) the call for papers for the [4th USENIX Workshop on Free and Open Communications on the Internet](https://www.usenix.org/conference/foci14/call-for-papers). The workshop will be held on August 18th, and should bring together the wider community of researchers and practitioners interested in Tor and other ways to study, detect, or circumvent censorship. Papers have to be submitted before May 13th.

Fabio Pietrosanti [wondered](https://lists.torproject.org/pipermail/tor-dev/2014-April/006723.html) whether anyone had “ever tried to start Tor from a Python application using Ctypes”, making it possible to “sandbox the Python application using AppArmor without enabling any kind of execve() call”.

# Tor help desk roundup

Many people email the Tor Help Desk from behind restrictive university firewalls that require them to connect using a proxy. Often these firewalls, Cyberoam and Fortiguard are two examples, use Deep Packet Inspection and block Tor traffic. Unfortunately Tor Browser users can’t use a proxy to connect to the internet and also use a pluggable transport. The Tor Browser team plans to include this capability in a [future release](https://bugs.torproject.org/8402).

* * *
This issue of Tor Weekly News has been assembled by Lunar, harmony, Matt Pagan, and an anonymous contributor.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

