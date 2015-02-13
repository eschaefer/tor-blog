---
layout: post
title: "Vidalia 0.2.10 Released"
permalink: vidalia-0210-released
date: 2010-09-28 10:31:45
author: phobos
category: blog
status: closed
tags: ["bugfixes", "geoip fixes", "osx fixes", "vidalia"]
---

The latest version of the graphical controller for tor, Vidalia, is now available. The main change is the use of Tor's native geoip database to map relay IP addresses to country. This removes the remote geoip resolution that occurred over Tor in previous versions of Vidalia.

Vidalia can be found at [https://www.torproject.org/vidalia/](https://www.torproject.org/vidalia/ "https://www.torproject.org/vidalia/").

The full changelog is: [**read more »**](https://blog.torproject.org/blog/vidalia-0210-released)

Drop remote GeoIP lookups. Instead, the default behavior now is to use the country-level GeoIP database that ships with Tor to map an IP address to a country code, and then map the country code to latitude and longitude with a separate database built into Vidalia.

Add a -DUSE\_GEOIP build option to enable building with MaxMind's GeoIP C library for using a local city-level or country-level database instead of Tor's database. See README.geoip for details on use.
