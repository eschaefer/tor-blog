---
layout: post
title: "On recent and upcoming developments in Pluggable Transports"
permalink: recent-and-upcoming-developments-pluggable-transports
date: 2014-06-15 15:44:03
author: asn
category: blog
status: closed
tags: ["circumvention", "pluggable transports", "pt"]
---

Hello friends,

this is a brief post on recent and upcoming developments of the [Pluggable Transport](https://www.torproject.org/docs/pluggable-transports.html.en) world:

What has happened
=================

Here is what has been keeping us busy during the past few months:

TBB 3.6
-------

As many of you know, the TBB team recently released the [Tor Browser Bundle 3.6](https://www.torproject.org/download/download-easy.html.en) that features built-in PT support. This is great and has taken PT usage to [new levels](https://metrics.torproject.org/users.html?graph=userstats-bridge-transport&start=2014-03-17&end=2014-06-15&transport=obfs3#userstats-bridge-transport). Maaad props to the TBB team for all their work.

TBB-3.6 includes obfs3 and FTE by default. If the built-in bridges are blocked for you (this is the case at least in China), try getting some more bridges from [BridgeDB](https://bridges.torproject.org) (which also got renovated recently).

obfs2 deprecation
-----------------

We are in the process of [deprecating](https://trac.torproject.org/projects/tor/ticket/10314) the obfs2 pluggable transport.

This is because China blocks it using active probing, and because obfs3 is stictly better than obfs2. obfs3 can also be blocked using active probing, but China hasn't implemented this yet (at least as far as we know). The new upcoming line of PTs (like scramblesuit and obfs4) should be able to defend more effectively against active probing.

Outgoing proxies and Pluggable Transports
-----------------------------------------

Yawning Angel et al. recently implemented [outgoing proxy support for PTs](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/232-pluggable-transports-through-proxy.txt). This means that soon our PTs will be able to connect to an outgoing proxy using the Socks5Proxy torrc option (or the corresponding proxy field in TBB).

A Childs Garden Of Pluggable Transports
---------------------------------------

David Fifield created [refreshing visualizations of Pluggable Transports](https://trac.torproject.org/projects/tor/wiki/doc/AChildsGardenOfPluggableTransports). Take a look; it might help you understand what these damned things are doing.

What will happen
================

Now let's take a look into the short-term future (a few months ahead) of Pluggable Transports:

obfs4 and ScrambleSuit
----------------------

Remember [ScrambleSuit](https://lists.torproject.org/pipermail/tor-relays/2014-February/003886.html)? Guess what; we are thinking of **not** deploying it after all...

Don't get me wrong, ScrambleSuit is great, but during the past two months Yawning has been developing a new transport called ['obfs4'](https://github.com/Yawning/obfs4). obfs4 is like ScrambleSuit (with regards to features and threat model), but it's faster and autofixes some of the open issues with scramblesuit ([\#10887](https://trac.torproject.org/projects/tor/ticket/10887), [\#11271](https://trac.torproject.org/projects/tor/ticket/11271), ...).

Since scramblesuit has not been entirely deployed yet, we thought that it would be a good idea to deploy obfs4 instead, and keep scramblesuit around as an emergency PT.

Meek
----

Meek is an exciting new transport by David Fifield. You can read all about it here: [https://trac.torproject.org/projects/tor/wiki/doc/meek](https://trac.torproject.org/projects/tor/wiki/doc/meek "https://trac.torproject.org/projects/tor/wiki/doc/meek")

It's basically a transport that (ab)uses Firefox to do SSL in a way that makes it look like Firefox but underneath it's actually Tor. Very sneaky, and because it uses third-party services (like Google Appspot, Akamai, etc.) as proxies, the user does not need to input a bridge. Meek just works bridgeless and automagically.

Help us by testing the latest bundles that David made: [https://lists.torproject.org/pipermail/tor-qa/2014-June/000422.html](https://lists.torproject.org/pipermail/tor-qa/2014-June/000422.html "https://lists.torproject.org/pipermail/tor-qa/2014-June/000422.html")

Also, since the [recent Google block in China](https://en.greatfire.org/blog/2014/jun/google-disrupted-prior-tiananmen-anniversary-mirror-sites-enable-uncensored-access), Meek will not work with Google Appspot. However, other third-party services can be used instead of Appspot, so Meek does not lose its effectiveness.

PTs and IPv6
------------

PTs are not very good at IPv6 yet. We identified some of [the](https://trac.torproject.org/projects/tor/ticket/12138) [open](https://trac.torproject.org/projects/tor/ticket/11211) [issues](https://trac.torproject.org/projects/tor/ticket/7961) and hopefully we will fix them too.

* * * * *

  

And that's that for now.

Till next time, enjoy life and give thanks and praises :)

(For what it's worth, this was originally a post in the [tor-talk] mailing list:  
 [https://lists.torproject.org/pipermail/tor-talk/2014-June/033296.html](https://lists.torproject.org/pipermail/tor-talk/2014-June/033296.html "https://lists.torproject.org/pipermail/tor-talk/2014-June/033296.html"))
