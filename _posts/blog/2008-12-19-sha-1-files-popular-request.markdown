---
layout: post
title: "SHA-1 files by popular request"
permalink: sha-1-files-popular-request
date: 2008-12-19
author: phobos
category: blog
tags: ["downloads", "file verification", "hashes", "sha-1"]
---

We've received requests for .sha1 files in addition to .asc for our packages. Starting with 0.2.1.8-alpha, there are now .sha1 files in the [appropriate dist directories](https://www.torproject.org/dist/). Displaying them on the download web page is still a bit tricky. The current layout leaves the page even more cluttered with .sha1 links all over it.

When you download a 0.2.1.8-alpha or later package, simply replace ".asc" with ".sha1" to get the hash file.

You'll then need to either "openssl sha1 {package}" or "sha1sum {package}" to see if the hash you downloaded matches the package you downloaded. Note: replace {package} with the name of the file you downloaded.

Enjoy.

If you don't know what any of this means, [start here](http://en.wikipedia.org/wiki/File_verification).

