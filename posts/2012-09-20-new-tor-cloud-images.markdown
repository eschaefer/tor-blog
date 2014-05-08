---
layout: post
title: "New Tor Cloud images"
permalink: new-tor-cloud-images
date: 09/20/2012
author: Runa
category: blog
tags: ["bridges", "relays", "tor", "tor cloud"]
---

[The Tor Cloud](https://cloud.torproject.org/) images for all the seven regions have been updated to include the latest cloud image for stable Ubuntu release 12.04.1 LTS (Precise Pangolin). These new images are available on the Tor Cloud website.

The new images include Tor's new GPG key, uses apt-get instead of aptitude, and also includes the deb.torproject.org-keyring package ( [#6776](https://trac.torproject.org/projects/tor/ticket/6776)).

If you are already running a Tor Cloud bridge, you will need to either manually update your image, or set up a new Tor Cloud bridge and terminate the old one. If you decide not to take action, your image will fail to upgrade Tor correctly and will not be running as a bridge. To manually update your image; log on with SSH, and follow the [instructions](https://www.torproject.org/docs/debian.html.en) to add the new GPG key, upgrade Tor, and install the deb.torproject.org-keyring package.

