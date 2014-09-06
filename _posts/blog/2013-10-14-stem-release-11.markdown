---
layout: post
title: "Stem Release 1.1"
permalink: blog/stem-release-11
date: 2013-10-14
author: atagar
category: blog
tags: ["stem"]
---

Hi all. After seven months of work I'm pleased to announce Stem's 1.1.0 release!

For those who aren't familiar with it, Stem is a Python library for interacting with Tor. With it you can script against your relay, descriptor data, or even write applications similar to [arm](https://www.atagar.com/arm/) and [Vidalia](https://www.torproject.org/projects/vidalia.html.en).

**[https://stem.torproject.org/](https://stem.torproject.org/)**

So what's new in this release?

* * *

## Remote Descriptor Fetching

The [stem.descriptor.remote](https://stem.torproject.org/api/descriptor/remote.html) module allows you download current Tor descriptor data from directory authorities and mirrors, much like Tor itself does. With this you can easily check the status of the network without piggybacking on a local instance of Tor (or even having it installed).

For example...

    from stem.descriptor.remote import DescriptorDownloader


    downloader = DescriptorDownloader()


    try:
      for desc in downloader.get_consensus().run():
        print "found relay %s (%s)" % (desc.nickname, desc.fingerprint)
    except Exception as exc:
      print "Unable to retrieve the consensus: %s" % exc

* * *

## Connection Resolution

One of arm's most popular features has been its ability to monitor Tor's connections, and stem can now do the same! Lookups are performed via seven \*nix and FreeBSD resolvers, for more information and an example see [our tutorials](https://stem.torproject.org/tutorials/east_of_the_sun.html#connection-resolution).

* * *

## Numerous Features and Fixes

For a rundown of other changes see...

**[https://stem.torproject.org/change\_log.html#version-1-1](https://stem.torproject.org/change_log.html#version-1-1)**

Cheers! -Damian

