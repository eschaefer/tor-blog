---
layout: post
title: "Vidalia 0.2.10 Released"
permalink: vidalia-0210-released
date: 09/28/2010
author: phobos
category: blog
tags: ["bugfixes", "geoip fixes", "osx fixes", "vidalia"]
---

The latest version of the graphical controller for tor, Vidalia, is now available. The main change is the use of Tor's native geoip database to map relay IP addresses to country. This removes the remote geoip resolution that occurred over Tor in previous versions of Vidalia.

Vidalia can be found at [https://www.torproject.org/vidalia/](https://www.torproject.org/vidalia/ "https://www.torproject.org/vidalia/").

The full changelog is:

- Drop remote GeoIP lookups. Instead, the default behavior now is to use the country-level GeoIP database that ships with Tor to map an IP address to a country code, and then map the country code to latitude and longitude with a separate database built into Vidalia.
- Add a -DUSE\_GEOIP build option to enable building with MaxMind's GeoIP C library for using a local city-level or country-level database instead of Tor's database. See README.geoip for details on use.
- Only update a stream's displayed target address in the network map if no hostname was given in the stream's NEW status event. Fix suggested by Robert Hogan. (Ticket #608)
- Update the menubar icon at the same time as the dock icon on OS X. Previously, we had a blank icon in the menubar. (Ticket #610)
- Updated several translations.

