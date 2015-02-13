---
layout: post
title: "New Feature: Tor Interpreter"
permalink: new-feature-tor-interpreter
date: 2014-05-25 23:11:45
author: atagar
category: blog
status: closed
tags: ["stem"]
---

Hi all, after a couple months down in the engine room I'm delighted to announce a new Stem feature for advanced Tor users and developers!

**[Stem's Interpreter Tutoral](https://stem.torproject.org/tutorials/down_the_rabbit_hole.html)**

The control interpreter is a new method for interacting with Tor's control interface that combines an interactive python interpreter with raw access similar to telnet. This adds several usability features, such as...

-   Irc-style commands like '/help'.
-   Tab completion for Tor's controller commands.
-   History scrollback by pressing up/down.
-   Transparently handles Tor authentication at startup.
-   Colorized output for improved readability.

This is the last major feature going into the Stem's 1.2.0 release, which is coming out later this month. Until then you can easily give it a whirl with...

% git clone [https://git.torproject.org/stem.git](https://git.torproject.org/stem.git "https://git.torproject.org/stem.git")  
 % cd stem  
 % ./tor-prompt

Running into an issue? Got a feature request? As always feedback appreciated! -Damian
