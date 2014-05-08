---
layout: post
title: "Shutting down the Vidalia GeoIP mapping server"
permalink: shutting-down-vidalia-geoip-mapping-server
date: 10/01/2010
author: phobos
category: blog
tags: ["city mapping", "geoip", "vidalia", "vidalia network map", "volunteer run"]
---

Vidalia is the graphical controller for the Tor software. It provides an easy to use interface to control some basic functionality of the Tor software and to give you graphical feedback as to what your Tor software is doing as you use it.

The Vidalia Project is shutting down the server that gives you the city-level location for tor relays in the Network Map. If you are running a version of Vidalia that is earlier than 0.2.10, you will lose your country flags and relays appearing in the Network Map. This is a display issue and does not affect the functionality of the Tor software itself. The main change in Vidalia 0.2.10 was to rely on the Tor software's local country-level GeoIP database that ships with the Tor software.

Running geoip.vidalia-project.net saved us from including a large database within the packages. The Tor software packages include a small country-level database which works fine for this Network Map display purpose. The Tor software's database provides country-level resolution, so you'll still know where your relay and circuits are traveling around the globe.

If you've lost your flags in Vidalia, upgrade to 0.2.10. Vidalia itself can be downloaded at [https://www.torproject.org/vidalia/](https://www.torproject.org/vidalia/ "https://www.torproject.org/vidalia/"). All packages we maintain have been updated with Vidalia 0.2.10. See [https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download") for more options.

