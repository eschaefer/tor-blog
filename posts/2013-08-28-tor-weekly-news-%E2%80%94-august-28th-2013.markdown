---
layout: post
title: "Tor Weekly News — August, 28th 2013"
permalink: tor-weekly-news-%E2%80%94-august-28th-2013
date: 08/28/2013
author: lunar
category: blog
tags: ["tor weekly news"]
---

Welcome to the ninth issue of Tor Weekly News, the weekly newsletter that covers what is happening in the determined Tor community.

# Orweb Security Advisory

On August 21st, Nathan Freitas from the Guardian Project issued security advisory regarding a [possible anonymity flaw affecting Orweb](https://lists.torproject.org/pipermail/tor-talk/2013-August/029503.html):

“The Orweb browser app is vulnerable to leak the actual IP of the device it is on, if it loads a page with HTML5 video or audio tags on them, and those tags are set to auto-start or display a poster frame. On some versions of Android, the video and audio player start/load events happen without the user requesting anything, and the request to the URL for the media src or through image poster is made outside of the proxy settings”, wrote Nathan.

Users who use the root mode with transparent proxying, as that handles proxying the entire traffic of the entire device or a particular app are NOT affected by this flaw.

Unfortunately, the problem mentioned above hasn't been fixed yet, as there is [no patch developers are happy with](https://lists.torproject.org/pipermail/news-team/2013-August/000019.html). According to Nathan the temporary solution is ”switch to Firefox, with the appropriate set of add-ons.” The Guardian Project has updated its website with a [step by step guide](https://guardianproject.info/apps/proxymob-firefox-add-on/) on how to set this up.

# “Why would anyone want a deterministic build process?”

In a blog post published last week, [Mike Perry explained the motivations](https://blog.torproject.org/blog/deterministic-builds-part-one-cyberwar-and-global-compromise) behind his three months long effort to make “deterministic builds” for the [3.0 series](https://blog.torproject.org/category/tags/tbb-30) of the Tor Browser Bundle.

“The short answer is: to protect against targeted attacks” introduced Mike. With automatic remote updates becoming the norm, it becomes very interesting for a malware to “distribute copies of itself to tens or even hundreds of millions of machines in a single, officially signed, instantaneous update.” The attack shifts from attacking a millions of machines to attacking the few that are involved in “software development and build processes”.

Be sure to read Mike's post to get the full picture.

Mike concludes with how deterministic builds can mitigate the issue: “in [Tor] case, any individual can use our anonymity network to privately download our source code, verify it against public signed, audited, and mirrored git repositories, and reproduce our builds exactly, without being subject to such targeted attacks. If they notice any differences, they can alert the public builders/signers, hopefully using a pseudonym or our anonymous trac account.”

Even if “it is important for Tor to set an example on this point”, Mike hopes that Linux distributions will follow in making deterministic packaging the norm.” It looks like at least [NixOS](http://lists.science.uu.nl/pipermail/nix-dev/2013-June/011357.html) and now [Debian](https://wiki.debian.org/ReproducibleBuilds) have started working on this.

# Filters and the default Tor Browser search engine

Four months ago, an anonymous reporter complained that the search engine  
used by default by the Tor Browser, Startpage, had a [“family filter” enabled by default](https://bugs.torproject.org/8839). The reporter pointed out that it was pretty funny “for a browser that people use to evade censorship and filters”. Another anonymous contributor quickly pointed out that the filter could be deactivated in a few clicks in Startpage preferences.

The issue got some more attention a few days ago as Nick Mathewson mentioned hearing reports that the filter was blocking “LGBT stuff, which is of course serious”. Nick further identified that the filter was blocking — among several other things — search for “ [The Owl and the Pussy-Cat](https://en.wikipedia.org/wiki/The_Owl_and_the_Pussycat)”, “ [Pussy Riot](https://en.wikipedia.org/wiki/Pussy_Riot)”, “ [Dick Cheney](https://en.wikipedia.org/wiki/Dick_Cheney)”, “ [Cock Robin](https://en.wikipedia.org/wiki/Cock_Robin_%28band%29)”, ” [Gerald Cock](https://en.wikipedia.org/wiki/Gerald_Cock)”.

Censoring 19th century poetry and repressed Russian punk bands was enough to make Nick conclude by an euphemism: “let's kill this filter hard”.

Mike Perry had some insights: “What we're seeing here is actually a change in Google's Safesearch. It used to be on by default and quite a bit smarter about differentiating porn from non-porn.” Mike mailed Startpage people to explain the problem and suggests that they leave the filter off by default.

In the case they would leave it on, both Nick and Mike agreed that a technical workaround should be implemented to automatically deactivate the filters when using the Tor Browser.

# Sudden rise in direct Tor users

On Tuesday 27th, [Roger Dingledine drew attention](https://lists.torproject.org/pipermail/tor-talk/2013-August/029582.html) to the huge increase of Tor clients running. It seems that their number has doubled since August 19th according to the count of [directly connecting users](https://metrics.torproject.org/users.html?graph=direct-users&start=2013-05-29&end=2013-08-27&country=all&events=off#direct-users).

According to Roger this is not just a fluke in the metrics data. The extra [load on the directory authorities](https://metrics.torproject.org/network.html#dirbytes) is clearly visible, but it does not look that the [overall network performance](https://metrics.torproject.org/performance.html) are affected so far.

The cause is still unknown, but there are already speculations about the [Pirate Browser or the](https://lists.torproject.org/pipermail/tor-talk/2013-August/029584.html) [new “anti-piracy” law in Russia](https://lists.torproject.org/pipermail/tor-talk/2013-August/029583.html) which is in force since August 1<sup>st</sup>. As Roger pointed out, “some good solid facts would sure be useful.”

# Help Desk Roundup

Users continue to have trouble verifying package signatures. One user was confused when the signature was automatically saved as a “.txt” file. Other problems included not being running the command from the correct directory, and downloading a signature that did not correspond with the downloaded file.

Users sometimes write the help desk seeking clarification about misconceptions about Tor. Examples of such misconceptions include “Is it true that Tor is illegal in the United States?” and “Is it true that Tor has been compromised by the NSA?”. Using Tor is not currently illegal anywhere. For information about the recent vulnerability, users are advised to read the [recent blog post on the subject](https://blog.torproject.org/blog/hidden-services-current-events-and-freedom-hosting).

# Miscellaneous news

David Goulet [announced the first release candidate](https://lists.torproject.org/pipermail/tor-dev/2013-August/005319.html) of [his rewrite of torsocks](https://github.com/dgoulet/torsocks). Several bug reports have since been fixed from early testers. Expect a new release soon.

Not all computers currently have their clock synchronized. This means that any timestamps in the Tor protocol can unfortunately be used to fingerprint Tor users. Nick Mathewson would like to improve the situation and has [sent proposal 222](https://lists.torproject.org/pipermail/tor-dev/2013-August/005302.html), aiming to eliminate “passive timestamp exposure”, for reviews.

Karsten Loesing has made [further progress](https://bugs.torproject.org/9166#comment:25) on “experimenting with a client and private bridge connected over uTP”. Reduced time for client to bootstrap over uTP from 2 minutes to 6 seconds and more.

Orbot's new version 12.0.5 brings identity switching-by-swiping along with a few bugfixes. It can be [downloaded from Google Play](https://play.google.com/store/apps/details?id=org.torproject.android) or from the Guardian Project's channels.

GSoC students sent another wave of bi-weekly reports: Kostas Jakeliunas on [Searchable Metrics Archive](https://lists.torproject.org/pipermail/tor-dev/2013-August/005310.html), Johannes Fürmann on [EvilGenius](https://lists.torproject.org/pipermail/tor-dev/2013-August/005317.html), Hareesan on the [Steganography Browser Extension](https://lists.torproject.org/pipermail/tor-dev/2013-August/005320.html), Robert on [Stream-RTT](https://lists.torproject.org/pipermail/tor-dev/2013-August/005323.html), and Cristian-Matei Toader on [Tor capabilities](https://lists.torproject.org/pipermail/tor-dev/2013-August/005327.html).

The Torservers.net crowdfunding campaign for Tor exit bandwidth ended on August 26th, yielding “3771,84 Euro to be spread equally across our current seven organizations” [anounnced Moritz Bartl](https://lists.torproject.org/pipermail/tor-relays/2013-August/002544.html).

Kostas Jakeliunas answered George's [call for help](https://lists.torproject.org/pipermail/tor-relays/2013-August/002477.html) to gather more accurate bridge statistics by writing [step by step instructions](https://lists.torproject.org/pipermail/tor-relays/2013-August/002500.html) on how to upgrade a bridge running on a Rasberry Pi to use the tor master branch. Lunar also pointed out that — thanks to Peter Palfrader's work on setting up continuous integration — Debian packages for the tor master branch were also available and [ready to be used](https://lists.torproject.org/pipermail/tor-relays/2013-August/002503.html).

* * *

This issue of Tor Weekly News has been assembled by Lunar, dope457, mttp and Karsten Loesing.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing-list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!

