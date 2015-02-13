---
layout: post
title: "Stem Release 1.0"
permalink: stem-release-10
date: 2013-03-30 22:05:30
author: atagar
category: blog
status: closed
tags: ["stem"]
---

Hi all. After eighteen months of work and a number of delays rivaling that of the Big Dig I'm pleased to announce the initial release of stem!

For those who aren't familiar with it, stem is a python controller library for tor. With it you can write scripts and applications that interact with your tor client or relay. For some examples of what you can do see the tutorials on...

**[https://stem.torproject.org/](https://stem.torproject.org/)**

Stem is compatible with python 2.6 and higher (including the 3.x series), and is a near complete implementation of tor's control and directory specifications. It has relatively high test coverage (\~80% for most modules) and integration tests to check its continued interoperability with new releases of tor.

As always, if you encounter issues or have feature requests then please [let me know](http://www.atagar.com/contact/)! Also, if you write something that uses stem then please tell me, both so we can continue to improve our API and expand the tutorial's list of examples.

Many thanks to everyone that helped make this initial release of stem possible, both with its development and packaging! -Damian
