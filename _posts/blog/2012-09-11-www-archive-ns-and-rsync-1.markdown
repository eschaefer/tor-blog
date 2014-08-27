---
layout: post
title: "www, archive, ns, and rsync +1"
permalink: www-archive-ns-and-rsync-1
date: 2012-09-11
author: phobos
category: blog
tags: ["archive", "debian", "infrastructure", "listera", "mirror", "nameserver", "rsync", "server", "www"]
---

Thanks to [Debian](http://www.debian.org/) for providing a fine server capable of providing redundancy for a number of services. This new server is in live rotation for [https://archive.torproject.org](https://archive.torproject.org "https://archive.torproject.org"), [https://www.torproject.org](https://www.torproject.org "https://www.torproject.org"), acts as one of our primary DNS servers, and provides rsync for the archive data store. It mirrors 165GB of data hourly. The server is located in Darmstadt, Germany and provides a copy of the services on the European continent.

The addition of a second server allows us to implement some changes to the way we allow others to mirror our data sets. The primary server behind archive.torproject.org is also known as rsync.torproject.org. It now solely serves up rsync.torproject.org. If you have scripts that periodically mirror archive.torproject.org, you probably want to update them for rsync.torproject.org.

Thanks to the Debian Sysadmin Team for the server and hosting!

