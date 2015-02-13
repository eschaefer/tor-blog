---
layout: post
title: "Obfsproxy Bridges in the Amazon Cloud"
permalink: obfsproxy-bridges-amazon-cloud
date: 2012-09-26 07:42:52
author: Runa
category: blog
status: closed
tags: ["bridges", "obfsproxy", "relays", "tor", "tor cloud"]
---

[The Tor Cloud](https://cloud.torproject.org/) images for all the seven regions have been updated to fix a bug found in the unattended-upgrades configuration. The normal bridge images have also been updated to include [obfsproxy](https://www.torproject.org/projects/obfsproxy), which attempts to help users circumvent censorship by transforming the Tor traffic between the client and the bridge.

If you are already running a Tor Cloud bridge, you will need to either manually update your image, or set up a new Tor Cloud bridge and terminate the old one. If you decide not to take action, your image will fail to upgrade Tor correctly and will not be running as a bridge.

If you just want to fix the bug in the unattended-upgrades configuration, do the following; log on with SSH and edit */etc/apt/apt.conf.d/50unattended-upgrades* to say *precise* instead of *lucid*.
