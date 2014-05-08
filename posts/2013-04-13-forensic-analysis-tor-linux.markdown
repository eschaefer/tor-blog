---
layout: post
title: "Forensic Analysis of Tor on Linux"
permalink: forensic-analysis-tor-linux
date: 04/13/2013
author: Runa
category: blog
tags: ["forensic analysis", "linux", "tbb", "tor"]
---

As part of a deliverable for two of our sponsors ( [Sponsor J,](https://trac.torproject.org/projects/tor/wiki/org/sponsors/SponsorJ) [Sponsor L](https://trac.torproject.org/projects/tor/wiki/org/sponsors/SponsorL)), I have been working on a forensic analysis of the Tor Browser Bundle. In this three part series, I will summarize the most interesting or significant traces left behind after using the bundle. This post will cover Debian Linux ( [#8166](https://trac.torproject.org/projects/tor/ticket/8166)), part two will cover Windows 7, and part three will cover OS X 10.8.

### Process

I set up a virtual machine with a fresh install of Debian 6.0 Squeeze, logged in once and shut it down cleanly. I then connected the virtual drive to another virtual machine and used _dd_ to create an image of the drive. I also used _hashdeep_ to compute hashes for every file on the drive, and _rsync_ to copy all the files over to an external drive.

After having secured a copy of the clean virtual machine, I rebooted the system, connected an external drive, and copied the Tor Browser Bundle (version 2.3.25-6, 64-bit) from the external drive to my Debian home directory. I extracted the package archive and started the Tor Browser Bundle by running ./start-tor-browser inside the Tor Browser directory.

Once the Tor Browser was up and running, I browsed to a few pages, read a few paragraphs here and there, clicked on a few links, and then shut it down by closing the Tor Browser and clicking on the _Exit_-button in Vidalia. The Tor Browser did not crash and I did not see any error messages. I deleted the Tor Browser directory and the tarball using _rm -rf_.

I repeated the steps with _dd_, _hashdeep_, and _rsync_ to create a copy of the tainted virtual machine.

### Results

Using _hashdeep_, I compared the hashes from the tainted virtual machine against the hashes from the clean virtual machine: [68 files](https://trac.torproject.org/projects/tor/attachment/ticket/8166/debian_changed_files.txt) had a hash that did not match any of the hashes in the clean set. The most interesting files are:

**~/.local/share/gvfs-metadata/home** : contains the filename of the Tor Browser Bundle tarball: _tor-browser-gnu-linux-x86\_64-2.3.25-5-dev-en-US.tar.gz_. GVFS is the virtual filesystem for the GNOME desktop, so this result will probably vary depending on the window manager used. I have created [#8695](https://trac.torproject.org/projects/tor/ticket/8695) for this issue.

**~/.xsession-errors** : contains the following string: _“Window manager warning: Buggy client sent a \_NET\_ACTIVE\_WINDOW message with a timestamp of 0 for 0x3800089 (Tor Browse)”_. It is worth noting that a file named _.xsession-errors.old_ could also exist. I have created [#8696](https://trac.torproject.org/projects/tor/ticket/8696) for this issue.

**~/.bash\_history** : contains a record of commands typed into the terminal. I started the Tor Browser Bundle from the command line, so this file contains lines such as _./start-tor-browser_. I have created [#8697](https://trac.torproject.org/projects/tor/ticket/8697) for this issue.

**/var/log/daemon.log** , **/var/log/syslog** , **/var/log/kern.log** , **/var/log/messages** : contains information about attached devices. I had an external drive attached to the virtual machine, so these files contain lines such as _“Mounted /dev/sdb1 (Read-Write, label “THA”, NTFS 3.1)”_ and _“Initializing USB Mass Storage driver…”_.

