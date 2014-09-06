---
layout: post
title: "Quick thoughts on tor2web"
permalink: blog/quick-thoughts-tor2web
date: 2008-12-16
author: phobos
category: blog
tags: ["hidden services", "onion addresses", "tor2web"]
---

Aaron and Virgil's [tor2web](http://tor2web.com) site has been picked up by [Wired's 27bstroke6 blog](http://blog.wired.com/27bstroke6/2008/12/tor-anonymized.html) and [Ars Technica](http://arstechnica.com/news.ars/post/20081215-tor2web-brings-anonymous-tor-sites-to-the-regular-web.html).

First off, I think it's a neat implementation of allowing non-Tor users access to the realm of .onion, aka hidden services. While I think using the [Tor Browser Bundle](https://www.torproject.org/torbrowser/) is incredibly easy, not everyone agrees with me. Neither Tor nor tor2web host any of the hidden service content. We don't know who does, nor who runs the hidden service. This brings me to my next thought.

Part of the challenge is that right now there is usually some place in the world that will publish your thing for you if it's interesting. Wikileaks is this year's example. But down the road, it may become the case that some things are just too hot for a public site to touch, and besides not everybody can convince Wikileaks to put up their document. Remember Usenet in the 80s? Remember BBSes? Remember NCSA Mosaic and the web in the early '90s? Technical people gravitated to these technologies first. The content reflected the people running the nodes; and the size of the community. People post things just because they can. Teenagers continue to post their plans for world domination; I've read them on BBSes, usenet, .plan files, and their web pages over the decades. Why should hidden services be any different?

Hidden Services are fairly new. They can be slow. They are a work in progress, but we believe them to be very secure and anonymous. They are an example of an application that can run on top of an anonymized network layer, such as Tor. Much like any new technology, the userbase is probably small. Sure, all Tor users have access to them, but it takes a lot of motivation and skill to setup a website correctly for hidden services. There are lots of ways to do it wrong and expose where the hidden service runs on the public Internet. This leads to less useful content generated for the masses. Make it easier, and perhaps the users will come in droves.

A few thoughts about potential services, merely copying from the current public Internet now;

- anonymous blogging (think wordpress, movable type, blogspot)
- anonymous microblogging (aka twitter)
- anonymous forums for dissidents, abuse survivors, cancer survivors, human rights activists
- anonymous dropbox or other personal document sharing (for stuff you just want to access when remote)
- anonymous instant messaging

Why couldn't twitter, wordpress/MT/Blogspot, and forum providers setup a hidden service to their current offerings? Wikileaks and IndyMedia do already. If your customers are on a heavily censored Internet connection, hidden services may be the only way they can access your service. Some of these suggestions exist today, but they suffer from the lack of "network effect".

There is a lot of potential for hidden services to be valuable and host great content. Don't judge them by the little known content that exists today.

Hidden services aren't limited to websites either. I use them heavily for anonymous ssh access and getting access to my file systems behind NAT and firewalls.

Be aware that if tor2web logs IP addresses, they have yours; I don't believe they do log, however. I wonder if Google, Yahoo, and others will crawl tor2web and start indexing the content.

P.S. Wired, we're torproject.org, not tor.eff.org anymore.

