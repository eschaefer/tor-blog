---
layout: post
title: "Stem Release 1.2"
permalink: stem-release-12
date: 2014-06-01 15:53:37
author: atagar
category: blog
status: closed
tags: ["stem"]
---

Hi all. After months of work I'm please to announce the release of Stem 1.2.0!

For those who aren't familiar with it, Stem is a Python library for interacting with Tor. With it you can script against your relay, descriptor data, or even write applications similar to arm and Vidalia.

**[https://stem.torproject.org/](https://stem.torproject.org/)**

So what's new in this release?

* * * * *

Interactive Tor Interpreter
---------------------------

The control interpreter is a new method for interacting with Tor's control interface that combines an interactive python interpreter with raw access similar to telnet. This adds several usability features, such as...

-   Irc-style commands like '/help'.
-   Tab completion for Tor's controller commands.
-   History scrollback by pressing up/down.
-   Transparently handles Tor authentication at startup.
-   Colorized output for improved readability.

For a tutorial to get you started see...

**[Down the Rabbit Hole](https://stem.torproject.org/tutorials/down_the_rabbit_hole.html)**

* * * * *

New connect() Function
----------------------

This release of Stem provides a new, even easier method for establishing controllers. Connecting to Tor can now be as easy as...

     import sys  from stem.connection import connect  if __name__ == '__main__':   controller = connect()    if not controller:     sys.exit(1)  # unable to get a connection    print 'Tor is running version %s' % controller.get_version()   controller.close() 

  

* * * * *

For a rundown on the myriad of improvements and fixes in this release see...

**[https://stem.torproject.org/change\_log.html\#version-1-2](https://stem.torproject.org/change_log.html#version-1-2)**

Cheers! -Damian
