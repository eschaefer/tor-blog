---
layout: post
title: "Shutting down the Vidalia GeoIP mapping server"
permalink: shutting-down-vidalia-geoip-mapping-server
date: 2010-09-30 19:32:52
author: phobos
category: blog
status: closed
tags: ["city mapping", "geoip", "vidalia", "vidalia network map", "volunteer run"]
---

Vidalia is the graphical controller for the Tor software. It provides an easy to use interface to control some basic functionality of the Tor software and to give you graphical feedback as to what your Tor software is doing as you use it.

The Vidalia Project is shutting down the server that gives you the city-level location for tor relays in the Network Map. If you are running a version of Vidalia that is earlier than 0.2.10, you will lose your country flags and relays appearing in the Network Map. This is a display issue and does not affect the functionality of the Tor software itself. The main change in Vidalia 0.2.10 was to rely on the Tor software's local country-level GeoIP database that ships with the Tor software. [**read more »**](https://blog.torproject.org/blog/shutting-down-vidalia-geoip-mapping-server)
