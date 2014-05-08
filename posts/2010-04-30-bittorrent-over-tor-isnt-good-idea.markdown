---
layout: post
title: "Bittorrent over Tor isn't a good idea"
permalink: bittorrent-over-tor-isnt-good-idea
date: 04/30/2010
author: arma
category: blog
tags: ["anonymity applications attack", "BitTorrent", "different exit", "network", "peer", "post privacy problem", "relay"]
---

An increasing number of people are asking us about the [recent paper](http://hal.inria.fr/docs/00/47/15/56/PDF/TorBT.pdf) coming out of Inria in France around Bittorrent and privacy attacks. This post tries to explain the attacks and what they imply.

There are three pieces to the attack (or three separate attacks that build on each other, if you prefer).

The first attack is on people who configure their Bittorrent application to proxy their tracker traffic through Tor. These people are hoping to keep their IP address secret from somebody looking over the list of peers at the tracker. The problem is that several popular Bittorrent clients (the authors call out uTorrent in particular, and I think Vuze does it too) just ignore their socks proxy setting in this case. Choosing to ignore the proxy setting is understandable, since modern tracker designs use the UDP protocol for communication, and socks proxies such as Tor only support the TCP protocol -- so the developers of these applications had a choice between "make it work even when the user sets a proxy that can't be used" and "make it mysteriously fail and frustrate the user". The result is that the Bittorrent applications made a different security decision than some of their users expected, and now it's biting the users.

The attack is actually worse than that: apparently in some cases uTorrent, BitSpirit, and libTorrent simply write your IP address directly into the information they send to the tracker and/or to other peers. Tor is doing its job: Tor is \_anonymously\_ sending your IP address to the tracker or peer. Nobody knows where you're sending your IP address from. But that probably isn't what you wanted your Bittorrent client to send.

That was the first attack. The second attack builds on the first one to go after Bittorrent users that proxy the rest of their Bittorrent traffic over Tor also: it aims to let an attacking peer (as opposed to tracker) identify you. It turns out that the Bittorrent protocol, at least as implemented by these popular Bittorrent applications, picks a random port to listen on, and it tells that random port to the tracker as well as to each peer it interacts with. Because of the first attack above, the tracker learns both your real IP address and also the random port your client chose. So if your uTorrent client picks 50344 as its port, and then anonymously (via Tor) talks to some other peer, that other peer can go to the tracker, look for everybody who published to the tracker listing port 50344 (with high probability there's only one), and voila, the other peer learns your real IP address. As a bonus, if the Bittorrent peer communications aren't encrypted, the Tor exit relay you pick can also [watch the traffic](https://trac.torproject.org/projects/tor/wiki/TheOnionRouter/TorFAQ#CanexitnodeseavesdroponcommunicationsIsntthatbad) and do the attack.

That's the second attack. Combined, they present a variety of reasons why running any Bittorrent traffic over Tor isn't going to get you the privacy that you might want.

So what's the fix? There are two answers here. The first answer is "don't run Bittorrent over Tor". We've been saying for years not to run Bittorrent over Tor, because the Tor network [can't handle the load](https://blog.torproject.org/blog/why-tor-is-slow); perhaps these attacks will convince more people to listen. The second answer is that if you want your Bittorrent client to actually provide privacy when using a proxy, you need to get the application and protocol developers to fix their applications and protocols. [Tor can't keep you safe if your applications leak your identity.](https://www.torproject.org/download.html.en#Warning)

The third attack from their paper is where things get interesting. For efficiency, Tor [puts multiple application streams over each circuit](https://svn.torproject.org/svn/projects/design-paper/tor-design.html#sec:intro). This approach improves efficiency because we don't have to waste time and overhead making a new circuit for every tiny picture on the aol.com frontpage, and it improves anonymity because every time you build a new path through the Tor network, you increase the odds that one of the paths you've built is observable by an attacker. But the downside is that exit relays can build short snapshots of user profiles based on all the streams they see coming out of a given circuit. If one of those streams identifies the user, the exit relay knows that the rest of those streams belong to that user too.

The result? If you're using Bittorrent over Tor, and you're \_also\_ browsing the web over Tor at the same time, then the above attacks allow an attacking exit relay to break the anonymity of some of your web traffic.

What's the fix? The same two fixes as before: don't run Bittorrent over Tor, and/or get your Bittorrent developers to fix their applications.

But as Tor developers, this attack opens up an opportunity for a third fix. Is there a way that we as Tor can reduce the damage that users can do to themselves when they use insecure applications over Tor? We can't solve the fact that you'll shoot yourself in the foot if you use Bittorrent over Tor, but maybe we can still save the rest of the leg.

One approach to addressing this problem in Tor's design is to make each user application use a separate circuit. In Linux and Unix, we can probably hack something like that up -- there are ways to look up the pid (process ID) of the application connecting to our socket. I suspect it gets harder in Windows though. It also gets harder because many Tor applications use an intermediate http proxy, like Polipo or Privoxy, and we'd have to teach these other proxies how to distinguish between different applications and then pass that information along to Tor.

Another answer is to separate streams by destination port. Then all the streams that go to port 80 are on one circuit, and a stream for a different destination port goes on another circuit. We've had that idea lurking in the background for a long time now, but it's actually because of Bittorrent that we haven't implemented it: if a BT client asks us to make 50 streams to 50 different destination ports, I don't want the Tor client to try to make 50 different circuits. That puts too much load on the network. I guess we could special-case it by separating "80" and "not 80", but I'm not sure how effective that would be in practice, first since many other ports (IM, SSH, etc) would want to be special-cased, and second since firewalls are pressuring more and more of the Internet to go over port 80 these days.

We should keep brainstorming about ways to protect users even when their applications are handing over their sensitive information. But in the mean time, I think it's great that these researchers are publishing their results and letting everybody else evaluate the attacks. (If you're a researcher working on Tor attacks or defenses, check out our new [research resources](https://www.torproject.org/research.html.en) page.) The attacks in this paper are serious attacks if you're a Bittorrent user and you're hoping to have some privacy.

