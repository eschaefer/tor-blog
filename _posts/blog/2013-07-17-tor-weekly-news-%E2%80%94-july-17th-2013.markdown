---
layout: post
title: "Tor Weekly News — July, 17th 2013"
permalink: tor-weekly-news-%E2%80%94-july-17th-2013
date: 2013-07-17
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the third issue of Tor Weekly News, the weekly newsletter meant to cover what is happening in the amazing Tor community.

# Last call for testing Tor 0.2.4 branch

[Roger Dingledine notified tor-talk](https://lists.torproject.org/pipermail/tor-talk/2013-July/028934.html) that there are [new versions of the Tor Browser Bundle](https://www.torproject.org/projects/torbrowser.html.en#Download-torbrowserbundlealpha), dubbed 2.4.15-beta-1, that are ready to be tested: “If all goes well, we‘ll be calling the Tor 0.2.4 branch stable very soon. So now is the perfect time to let us know that it broke for you.”

He also added “to be clear, it is the Tor part of the Tor Browser Bundle that needs testing. We know there are a growing pile of bugs in Vidalia, as well as a set of issues in Torbutton. Both of these should improve with the TBB 3.0 release. But that is a separate thread.”

# Tor Hack Day, Munich, Germany

Meet the people who spend their day making Tor a reality. Join them for a [public hack day](https://blog.torproject.org/blog/join-us-tor-hack-day-munich-germany) on Friday, July 26, 2013 in Munich, Germany at the [Technische Universität München](http://www.tum.de/).

The agenda and conversations will be determined by you and Tor‘s team of developers and researchers — so bring your ideas, questions, projects, and technical expertise with you!

# 13<sup>th</sup> Privacy Enhancing Technologies Symposium

Many academic researchers and students interested in anonymity are already working with Tor. They also are part of a broader community of academics that gather every year during the [Privacy Enhancing Technologies Symposium](http://petsymposium.org/). [The 13<sup>th</sup> edition](http://petsymposium.org/2013/program.php) was held in Bloomington, Indiana, USA and was again well attended.

Several Tor developers were among the crowd of around 130 attendees (this makes it a new record or very close). On the first day, the first workshop on [Privacy Enhancing Tools (PETools)](http://petools.soic.indiana.edu/) was held, in which Roger Dingledine was invited to talk about “Lessons from Tor: How to Help Developers and Researchers Improve your Privacy Tool.”

During the next two days, researchers presented the selected papers. Two of them are directly relevant to the development of the Tor network:

Mashael Alsabah, Kevin Bauer, Tariq Elahi, and Ian Goldberg presented [Conflux](http://freehaven.net/anonbib/papers/pets2013/paper_65.pdf), “a dynamic traffic-splitting approach that assigns traffic to an overlay path based on its measured latency. […] Conflux considerably increases performance for clients using low-bandwidth bridges.” [A thread on tor-talk](https://lists.torproject.org/pipermail/tor-talk/2013-July/028950.html) discusses effects of Conflux on website fingerprinting.

John Geddes, Rob Jansen, and Nicholas Hopper studied [balancing performance with anonymity in Tor](http://freehaven.net/anonbib/papers/pets2013/paper_80.pdf). They have “investigated the effects of proposed [performance enhancing] modifications on attacks that rely on network measurements as a side channel.” The paper concluded with “an analysis of the total reduction in anonymity that clients face due to  
each proposed mechanism.”

Other papers are relevant to the wider set of Tor problems:

David Fifield, Gabi Nakibly, and Dan Boneh have looked at [web-based online scanning service […] that can be covertly used as proxies in a censorship circumvention system](http://freehaven.net/anonbib/papers/pets2013/paper_29.pdf) The system they describe is already “available as an experimental rendezvous for the [flash proxy system](https://crypto.stanford.edu/flashproxy/) and is part of [Tor’s pluggable-transports web browser bundles](https://www.torproject.org/projects/obfsproxy.html#download) starting with the 2.4.11-alpha-1 release.”

Amir Houmansadr and Nikita Borisov presented an analysis of how practical it is to [reliably fingerprint millions of network flows by tagging only as few as tens of packets from each flow](http://freehaven.net/anonbib/papers/pets2013/paper_71.pdf).

An extra day was dedicated to the HotPETs workshop, intended to “foster new ideas, spirited debates, and controversial perspectives on privacy (and lack thereof).” Among other interesting submissions, Wenxuan Zhou, Amir Houmansadr, Matthew Caesar, and Nikita Borisov presented [SWEET](http://petsymposium.org/2013/papers/zhou-censorship.pdf), a way to encapsulate “a censored user’s traffic inside email messages that are carried over by typical email service providers.”

All papers presented during the conference are available for download from the program page.

The next edition of PETS will be help July 16-18, 2014, in Amsterdam.

# Hardware for high bandwidth relay

[Andreas Fink asked for hints on hardware](https://lists.torproject.org/pipermail/tor-relays/2013-July/002239.html) that could support “big fat tor exit nodes connected with multiple 1gbps or 10gps links.”

[Andy Isaacson answered](https://lists.torproject.org/pipermail/tor-relays/2013-July/002241.html) that [Noisetor](http://noisetor.net/) uses “most of a 4-core X3350 2.6 GHz to push ~500 Mbps symmetric. That‘s without AES-NI.” Mike Perry and Moritz Bartl then both confirmed that modern Intel Xeon CPUs with AES-NI could do 300 Mbit/s per core.

# Blocking GFW probes on the firewall

Marek Majkowski suggests how to resist [Chinese effort to scan Tor relays and bridges](http://www.cs.kau.se/philwint/pdf/foci2012.pdf) using a firewall. Somewhere in the past month the Great Firewall of China started to actively probe the destination of any traffic that looked like a Tor bridge, plain or obfs2. If a handshake is successful, the connection is reset and the bridge address put on a blacklist.

As the probe sequence is static, Marek identified the incoming connection and gave [rules for the netfilter Linux firewall to filter them out](https://lists.torproject.org/pipermail/tor-talk/2013-July/028897.html).

If you run a bridge under Linux, please give them a try!

# Is it worth running a relay on a home broadband connection?

[Nick asked on the tor-relays mailing-list](https://lists.torproject.org/pipermail/tor-relays/2013-July/002240.html): “I have a reasonable ADSL connection, and a little always-on server. The bandwidth is in the region of 2Mib/s down, something less up (maybe 256Kib/s). Is it useful for me to run a tor relay with this bandwidth?”

[Lunar pointed out](https://lists.torproject.org/pipermail/tor-relays/2013-July/002249.html) that a relay with this capacity was “likely to be selected as a middle node 1 time out of 10000 circuits, if not less…”

[Roger Dingledine drew the cut](https://lists.torproject.org/pipermail/tor-relays/2013-July/002255.html): “at this point if you‘re at least 800kbit (100KBytes/s) each way, it‘s useful to be a relay.” He also detailed the current thresholds for the Stable and Guard flags.

Roger mentioned connections can still be of use though: ”a bridge is a fine thing to run on a connection with 250KBytes down and 32KBytes up.” And maybe even more in the future as “we might end up with a system like [Conflux](http://freehaven.net/anonbib/papers/pets2013/paper_65.pdf) to let you glue together two slow bridges and get better throughput.”

# Using Mumble with Tor

David H. wrote a [tutorial on how to configure Mumble to use the Tor network on Ubuntu](http://huertanix.tumblr.com/post/55261352264/location-anonymous-voice-communication-a-step-by-step). This tutorial includes setting up a server using Amazon EC2. During the discussion, adrelanos came up with his own [tutorial on anonymous VoIP which focuses on installing Mumble on Whonix](https://whonix.org/wiki/Voip) behind an hidden service.

Feel free to [follow the discussion on tor-talk](https://lists.torproject.org/pipermail/tor-talk/2013-July/028939.html).

# Miscellaneous development news

OONI has published a [detailed report](https://ooni.torproject.org/zambia-a-country-under-deep-packet-inspection.html) on how Zambia is currently censoring the grass roots online newspaper [Zambian Watchdog](https://zambianwatchdog.com/).

Nick Mathewson merged a way to mock C functions in tor unit tests. The “mocking methodology” has been [described](https://trac.torproject.org/projects/tor/ticket/8949#comment:1) as “the simplest thing that could work — it‘s one of the ones that festoon the code with macro salad, and uglifies the declarations of functions that are going to get mocked. It has the advantage of being portable, robust, and comprehensible.”

[Runa A. Sandvik announced](https://lists.torproject.org/pipermail/tor-dev/2013-July/005129.html) that she has disabled translations for Vidalia on Transifex as “translators should not work on resources which are currently not being maintained by a developer.”

Three GSoC students have sent updates: Johannes Fürmann on the [EvilGenius censorship simulation project](https://lists.torproject.org/pipermail/tor-dev/2013-July/005140.html), Robert on [Tor path generation and Stream-RTT probing](https://lists.torproject.org/pipermail/tor-dev/2013-July/005141.html), and Hareesan on the [steganography browser addon](https://lists.torproject.org/pipermail/tor-dev/2013-July/005143.html).

* * *

This issue of Tor Weekly News has been assembled by Lunar, luttigdev, dope457, whabib, Karsten Loesing, and Roger Dingledine.

Want to continue reading TWN? Please help us create this newsletter. We really need more volunteer writers who watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews) and write down your name if you want to get involved!

