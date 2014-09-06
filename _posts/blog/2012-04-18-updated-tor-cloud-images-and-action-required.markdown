---
layout: post
title: "Updated Tor Cloud images, and action required"
permalink: blog/updated-tor-cloud-images-and-action-required
date: 2012-04-18
author: Runa
category: blog
tags: ["bridge relays", "cloud", "tor", "tor cloud"]
---

The [Tor Cloud](https://cloud.torproject.org/) images for all the seven regions have been updated to include the latest cloud image for stable Ubuntu release 10.04 LTS (Lucid Lynx). These new images are available on the [Tor Cloud website](https://cloud.torproject.org/).

If you are already running a Tor Cloud bridge, you will need to either manually update your image, or set up a new Tor Cloud bridge and terminate the old one. If you decide not to take action, your image may fail to download package updates correctly.

What follows is an important message from the [ubuntu-cloud mailing list](https://lists.ubuntu.com/archives/ubuntu-cloud/2012-April/000752.html):

In an effort to improve on reliability of the Ubuntu archive mirrors for EC2 instances, Canonical is replacing the existing EC2 archive mirrors with mirrors backed by Amazon S3. This change itself will be done via modification of DNS entries and will be transparent to users.

However, due to a bug in the http pipelining implementation in S3 a change to apt configuration needs to be made to avoid download errors. We have chosen to deliver this change via a package upgrade in cloud-init.

The **action required** is one of the following:

- Upgrade cloud-init using _sudo apt-get update ; sudo apt-get install -y cloud-init_
- Launch official AMI's released after 2012-04-01, which will have the fix included
- Manually disable http pipeline use in apt using _echo 'Acquire::http::Pipeline-Depth "0";' | sudo tee /etc/apt/apt.conf.d/99-no-pipelining_

Should you choose not to take appropriate action, you will likely experience transient apt downloading errors after the change is implemented. In order to give appropriate time to apply the change, this transition will not occur before April 18, 2012.

