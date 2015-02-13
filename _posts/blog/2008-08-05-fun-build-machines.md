---
layout: post
title: "Fun with build machines"
permalink: fun-build-machines
date: 2008-08-05 21:50:21
author: phobos
category: blog
status: closed
tags: ["centos4", "osx 10.4", "osx tiger", "packages"]
---

Perhaps you've noticed that the packages for CentOS 4 and OSX Tiger/10.4 haven't been updated lately. Welcome to dead hard drives.

For a long while, I used [VMware Server](http://www.vmware.com/products/server/) for guest OSes to build the various rpm and windows packages. This mostly worked well. And then both drives in the physical server I used to host the vmware instance failed. A two-drive RAID 1 array doesn't like it when both drives fail. I replaced the drives, re-installed Debian, and attempted to install vmware server again. The vmware kernel module refused to load. I tried the old tricks to get it to work, nothing. I finally looked at some script/patch that I found via Google, and got the module to load. Then my license key didn't work anymore.

In frustration, I gave up and installed [VirtualBox](http://www.virtualbox.org/). CentOS 4 defaults to using an SMP kernel on install, which Virtualbox (aka qemu) doesn't like at all. CentOS 4 installs just fine, it just won't boot after install. I haven't had time to further fix the problem. For the time being, there's no CentOS 4 (Redhat 4 rpms) for Tor.

As for OSX, well, there was no raid array of any kind, just a single drive in a mac mini. It died in a fit of 0xE0030005 (Undefined) errors and now won't boot at all. A new drive is on the way. I expect to have OSX Tiger/10.4 packages in a week or so. The good news is that the [Panther Mac](http://www.everymac.com/systems/apple/imac/stats/imac_se_dv_400.html) continues to work just fine.

Perhaps it's time to start using Amazon's EC2 or something similar instead of messing with all this hardware and virtualization software. Or maybe I should work on hacking OSX 10.4 and 10.5 into virtualbox.

\*\* Update 2008-08-06: new drive was DOA. And it appears the logic board on the mac mini is fried. Ugh.
