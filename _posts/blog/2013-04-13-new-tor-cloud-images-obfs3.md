---
layout: post
title: "New Tor Cloud images with obfs3"
permalink: new-tor-cloud-images-obfs3
date: 2013-04-13 18:14:32
author: Runa
category: blog
status: closed
tags: ["bridges", "tor", "tor cloud"]
---

The [Tor Cloud](https://cloud.torproject.org/) images have been updated to include the latest version of Ubuntu 12.04.2 LTS (Precise Pangolin). An instance created from any of the images will automatically be a normal bridge, an obfs2 bridge, and an obfs3 bridge.

When setting up an instance, please remember to edit the security group with the following rules: SSH (22), HTTPS (443), 40872, and 52176.
