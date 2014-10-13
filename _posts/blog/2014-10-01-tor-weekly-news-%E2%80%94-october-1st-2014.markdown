---
layout: post
title: "Tor Weekly News — October 1st, 2014"
permalink: tor-weekly-news-%E2%80%94-october-1st-2014
date: 2014-10-01
author: harmony
category: blog
tags: ["tor weekly news"]
---

Welcome to the thirty-ninth issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

# Tor 0.2.4.24 and 0.2.5.8-rc are out

Roger Dingledine [announced](https://lists.torproject.org/pipermail/tor-talk/2014-September/034937.html) new releases in both the stable and the alpha branches of the core Tor software. Clients accessing hidden services should experience faster and more robust connections as they will now send the correct rendezvous point address. “They used to send the wrong address, which would still work some of the time because they also sent the identity digest of the rendezvous point, and if the hidden service happened to try connecting to the rendezvous point from a relay that already had a connection open to it, the relay would reuse that connection”. This fix also prevents the [endianness](https://en.wikipedia.org/wiki/Endianness) of the client’s system from being leaked to the hidden service.

The only other changes in these releases are an update of the geoip databases and the location of the [gabelmoo directory authority](https://lists.torproject.org/pipermail/tor-talk/2014-September/034898.html). As usual, you can download the source code from the Tor [distribution directory](https://www.torproject.org/dist/).

# Tor Browser 3.6.6 and 4.0-alpha-3 are out

Mike Perry announced two new releases by the Tor Browser team. [Tor Browser 3.6.6](https://blog.torproject.org/blog/tor-browser-366-released) includes a workaround for the [bug](https://bugs.torproject.org/10804) that has sometimes been preventing the browser window from opening after an apparently successful connection to the Tor network; it also stops intermediate SSL certificates from being written to disk. In addition to these fixes, [Tor Browser 4.0-alpha-3](https://blog.torproject.org/blog/tor-browser-40-alpha-3-released) resolves a number of issues to do with the upcoming Tor Browser updater, including the mistaken upgrade of non-English Tor Browsers to the English-language version. As this bug is only fixed in the new release, users upgrading from 4.0-alpha-2 will still experience this issue during the process. Furthermore, “meek transport users will need to restart their browser a second time after upgrade if they use the in-browser updater. We are still trying to get to the bottom of [this issue](https://bugs.torproject.org/13247)”, wrote Mike.

Both releases also include important Firefox security updates, so all users should upgrade as soon as possible. See Mike’s announcements for full details, and get your copy from the [project page](https://www.torproject.org/projects/torbrowser.html) or the [distribution directory](https://www.torproject.org/dist/torbrowser/).

# Tails 1.1.2 is out

The second point release in the Tails 1.1.x series was [put out](https://tails.boum.org/news/version_1.1.2/) by the Tails team, “mainly to fix a serious flaw in the Network Security Services (NSS) library used by Firefox and other products that allows attackers to create forged RSA certificates. Before this release, users on a compromised network could be directed to sites using a fraudulent certificate and mistake them for legitimate sites.”

Other packages affected by recently-disclosed security flaws and updated in this version include APT, bash, and GnuPG, so all Tails users should make sure to upgrade as soon as possible. If you have a running copy of Tails, you can make use of the incremental upgrades system; otherwise, head to the [download page](https://tails.boum.org/download/index) for more information.

# obfs4 is ready for general deployment: bridge operators needed!

[Pluggable transports](https://www.torproject.org/docs/pluggable-transports), the circumvention techniques which allow users to access the Tor network from censored areas by disguising the fact that the Tor protocol is being used, are about to take another step forward with the release of obfs4, and Yawning Angel [sent out](https://lists.torproject.org/pipermail/tor-relays/2014-September/005372.html) a brief discussion of this new protocol.

obfs4 offers a number of developments over the obfs3 and ScrambleSuit protocols, until now the most sophisticated pluggable transports in use on the Tor network. Like ScrambleSuit, obfs4 improves on obfs3 to “ [provide resilience against active attackers and to disguise flow signatures](https://gitweb.torproject.org/pluggable-transports/obfs4.git/blob/refs/heads/master:/doc/obfs4-spec.txt)”, while a safer and more efficient key-exchange process than ScrambleSuit’s should make it impossible for attackers to launch man-in-the-middle attacks based on the client/bridge shared secret.

Like its predecessors in the obfsproxy series, obfs4 is a bridge-based transport, meaning that volunteers are needed to operate relays running an implementation of the new protocol before users can take advantage of it. The current implementation, obfs4proxy, is now available to download either as [source code](https://gitweb.torproject.org/pluggable-transports/obfs4.git) or as a package from Debian’s [unstable repositories](https://packages.debian.org/sid/obfs4proxy). Those who want to try browsing over the new protocol can download Yawning’s [experimental Tor Browsers](https://people.torproject.org/~yawning/volatile/tor-browser-obfs4-20140926/), and if you’re willing to run an obfs4 bridge, please see Yawning’s message for all the relevant details — “questions, comments, and bridges appreciated”!

# Miscellaneous news

Anthony G. Basile [announced](https://lists.torproject.org/pipermail/tor-talk/2014-September/034950.html) the release of version 20140925 of tor-ramdisk, the micro Linux distribution whose only purpose is to host a Tor server in an environment that maximizes security and privacy. This release includes updates to Tor, BusyBox, OpenSSL, and the Linux kernel.

As part of the current push to better understand hidden services and their use on the Tor network, Roger Dingledine [asked](https://lists.torproject.org/pipermail/tor-relays/2014-September/005352.html) relay operators who are “comfortable compiling Tor from git” and who “want to help investigate what fraction of Tor network load comes from hidden service use” to check out the new hs-stats git branch. This version “will collect per-thirty-minute statistics about number of circuits and number of cells your relay sees that have to do with exiting, with hidden services, with circuits where you're not the final hop, and a fourth none-of-the-above category”, which can then be posted to the appropriate [ticket](https://bugs.torproject.org/13192) on the bug tracker or sent to Roger directly.

Yawning Angel [sent](https://lists.torproject.org/pipermail/tor-relays/2014-September/005344.html) a “friendly reminder” to ScrambleSuit bridge operators, asking them to upgrade to tor-0.2.5.x if they haven’t already: “If you are running a ScrambleSuit bridge with tor-0.2.4.x, it is useless. Users that happen to be served your ScrambleSuit bridge will not be able to connect, because the password is missing”.

Mike Perry [asked](https://lists.torproject.org/pipermail/tor-relays/2014-September/005335.html) relay operators, particularly those running exit relays, to contribute information about the “hardware, CPU cores, and uplink” of their servers, and how much these cost per month, in order to “put together some estimates on bounds of the current value and cost of the capacity of the Tor network as it is, and use that to generate some rough guestimates on what it would cost to grow it”.

In response to the possible integration of Tor as a “private browsing mode” by a major browser vendor, Andrew Lewman [kicked off](https://lists.torproject.org/pipermail/tor-dev/2014-September/007533.html) a discussion of ways in which the Tor network might be scaled up to accommodate “hundreds of millions” of extra users.

# Tor help desk roundup

In Firefox, it is possible to drag a URL from the Navigation Toolbar to the Desktop in order to create a shortcut to a website, and the help desk has been asked why this functionality is disabled in Tor Browser. A Desktop shortcut to a URL, when clicked, would be opened by the operating system’s default browser, not by Tor Browser. Permitting this behavior would open the door to confusion as to whether or not a user was visiting a link over Tor, and would violate the “Proxy Obedience” requirement of the [Tor Browser design](https://www.torproject.org/projects/torbrowser/design/#proxy-obedience).

# News from Tor StackExchange

Tor StackExchange has started its [site self-evaluation](https://meta.tor.stackexchange.com/q/221/88) for September 2014. [Ten questions](http://tor.stackexchange.com/review/site-eval) were selected and you’re asked to review them. Are they good or is there room for improvement? Please have a look at the questions and rate them.

Jens Kubieziel noted that users mix up the terms [Tor, Tor Browser and torbrowser-launcher](https://tor.stackexchange.com/q/4192/88), so he explained each of them to users of the Q&A page.

* * *
This issue of Tor Weekly News has been assembled by harmony, qbi, Lunar, Matt Pagan, dope457, and Yawning Angel.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the team [mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

