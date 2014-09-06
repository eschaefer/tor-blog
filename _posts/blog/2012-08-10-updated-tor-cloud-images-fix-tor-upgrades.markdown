---
layout: post
title: "Updated Tor Cloud images with fix for Tor upgrades"
permalink: blog/updated-tor-cloud-images-fix-tor-upgrades
date: 2012-08-10
author: Runa
category: blog
tags: ["bridges", "relays", "tor", "tor cloud"]
---

[The Tor Cloud](https://cloud.torproject.org/) images for all the seven regions have been updated to include the latest cloud image for stable Ubuntu release 10.04 LTS (Lucid Lynx). These new images are available on the Tor Cloud website.

The new images include a fix to allow Tor to upgrade automatically without requiring user intervention ( [#6511](https://trac.torproject.org/projects/tor/ticket/6511)).

If you are already running a Tor Cloud bridge, you will need to either manually update your image, or set up a new Tor Cloud bridge and terminate the old one. If you decide not to take action, your image will fail to upgrade Tor correctly and will not be running as a bridge.

To manually update your image, do the following:

0. Log on with SSH
1. Open /etc/apt/apt.conf.d/50unattended-upgrades
2. Add the line: Dpkg::Options { --force-confold; }
3. Save and exit

