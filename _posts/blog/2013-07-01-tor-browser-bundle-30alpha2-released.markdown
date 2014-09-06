---
layout: post
title: "Tor Browser Bundle 3.0alpha2 Released"
permalink: blog/tor-browser-bundle-30alpha2-released
date: 2013-07-01
author: mikeperry
category: blog
tags: ["deterministic builds", "gitian", "security", "tbb", "tbb-3.0", "tor browser", "tor browser bundle", "tor-browser-bundle"]
---

The second alpha release in the [3.0 series](https://blog.torproject.org/category/tags/tbb-30) of the Tor Browser Bundle is now available from the [Tor Package Archive](https://archive.torproject.org/tor-package-archive/torbrowser/3.0a2).

In addition to providing important security updates to Firefox and Tor, these release binaries should now be exactly reproducible from the source code by anyone. They have been independently reproduced by at least 3 public builders using independent machines, and the Tor Package Archive contains all three builder's GPG signatures of the sha256sums.txt file in the package directory.

To build your own identical copies of these bundles from source code, check out [the official repository](https://gitweb.torproject.org/builders/tor-browser-bundle.git/) and [use](http://stackoverflow.com/questions/10303665/how-to-clone-a-specific-version-of-a-git-repository/10304054#10304054) git tag **tbb-3.0alpha2-release** (commit c0242c24bed086cc9c545c7bf2d699948792c1e3). [These instructions](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob/HEAD:/gitian/README.build) should explain things from there. If you notice any differences from the official bundles, I would love to hear about it!

I will be writing a two part blog series explaining why this is important, and describing the technical details of how it was accomplished in the coming week or two. For now, [a brief explanation](https://mailman.stanford.edu/pipermail/liberationtech/2013-June/009257.html) can be found on the [Liberation Technologies](https://mailman.stanford.edu/mailman/listinfo/liberationtech) mailing list archive.

# ChangeLog

- **All Platforms:**

  - Update Firefox to 17.0.7esr
  - Update Tor to 0.2.4.14-alpha
  - Include Tor's GeoIP file

    - This should fix custom torrc issues with country-based node restrictions
  - Fix several build determinism issues
  - Include ChangeLog in bundles
- **Windows:**

  - Fix many crash issues by disabling Direct2D support for now.
- **Mac:**

  - Bug 8987: Disable TBB's 'Saved Application State' disk records on OSX 10.7+
- **Linux:**

  - Use Ubuntu's 'hardening-wrapper' to build our Linux binaries

The [complete 3.0 ChangeLog now lives here](https://gitweb.torproject.org/builders/tor-browser-bundle.git/blob_plain/HEAD:/Bundle-Data/Docs/ChangeLog.txt).

# Major Known Issues

1. Windows XP users may still experience crashes due to [Bug 9084](https://trac.torproject.org/projects/tor/ticket/9084).
2. Transifex issues are still causing problems with missing translation text in some bundles

