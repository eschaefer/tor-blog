---
layout: post
title: "Down to 0 issues on Coverity Scan."
permalink: down-0-issues-coverity-scan.
date: 01/11/2009
author: nickm
category: blog
tags: []
---

As of 7 January, we're down to 0 issues on Coverity Scan. This is great news!

In case you haven't heard of them, Coverity makes top-of-the-line static analysis tools (programs that analyse other programs looking for possible bugs). They're a big serious company, with a serious "enterprise" pricing structure. But, fortunately to us, they have [a program](http://scan.coverity.com/) to provide the use of these tools, free of charge, to selected open source projects. They've been scanning development snapshots of Tor for bugs since last September.

In September, they found 171 issues in our code. Many of these were just sloppiness in our unit tests' error handing, but a good fraction were real bugs in our main codebase, a couple of which could have resulted in crashes under unusual circumstances that probably would have been hard to debug. By December, we were down to 15 issues. Now we're at 0, at long last.

Congratulations and thanks to everybody who helped analyse and fix the bugs here, and many thanks to the administrators of Coverity Scan for helping us out.

