---
layout: post
title: "How to use the “meek” pluggable transport"
permalink: how-use-%E2%80%9Cmeek%E2%80%9D-pluggable-transport
date: 2014-08-15
author: dcf
category: blog
tags: ["censorship circumvention", "pluggable transports"]
---

The recently released 4.0-alpha-1 version of Tor Browser includes [meek](https://trac.torproject.org/projects/tor/wiki/doc/meek), a new [pluggable transport](https://www.torproject.org/docs/pluggable-transports.html) for censorship circumvention. meek tunnels your Tor traffic through HTTPS, and uses a technique called “domain fronting” to hide the fact that you are communicating with a Tor bridge—to the censor it looks like you are talking to some other web site. For more details, see the [overview](https://trac.torproject.org/projects/tor/wiki/doc/meek#Overview) and the [Child’s Garden of Pluggable Transports](https://trac.torproject.org/projects/tor/wiki/doc/AChildsGardenOfPluggableTransports#meek).

You only need meek if your Internet connection is censored so that you can’t use ordinary Tor. Even then, you should try other pluggable transports first, because they have less overhead. My recommended order for trying transports is:

1. obfs3
2. fte
3. scramblesuit
4. meek
5. flashproxy

Use meek if other transports don’t work for you, or if you want to help development by testing it. I have been using meek for my day-to-day browsing for a few months now.

All pluggable transports have some overhead. You might find that meek feels slower than ordinary Tor. We’re working on some tickets that will make it faster in the future: [#12428](https://trac.torproject.org/projects/tor/ticket/12428 "Make it possible to have multiple requests and responses in flight"), [#12778](https://trac.torproject.org/projects/tor/ticket/12778 "Put meek HTTP headers on a diet"), [#12857](https://trac.torproject.org/projects/tor/ticket/12857 "Use streaming downloads").

At this point, there are two different backends supported. [meek-amazon](https://trac.torproject.org/projects/tor/wiki/doc/meek#AmazonCloudFront) makes it look like you are talking to an Amazon Web Services server (when you are actually talking to a Tor bridge), and [meek-google](https://trac.torproject.org/projects/tor/wiki/doc/meek#GoogleAppEngine) makes it look like you are talking to the Google search page (when you are actually talking to a Tor bridge). It is likely that both will work for you. If one of them doesn’t work, try the other.

These instructions and screenshots are for the 4.0-alpha-1 release. If they change in future releases, they will be updated at [https://trac.torproject.org/projects/tor/wiki/doc/meek#Quickstart](https://trac.torproject.org/projects/tor/wiki/doc/meek#Quickstart "https://trac.torproject.org/projects/tor/wiki/doc/meek#Quickstart").

# How to use meek

First, download a meek-capable version of Tor Browser for your platform and language.

- [https://www.torproject.org/projects/torbrowser.html#downloads-alpha](https://www.torproject.org/projects/torbrowser.html#downloads-alpha "https://www.torproject.org/projects/torbrowser.html#downloads-alpha")

[Verify the signature](https://www.torproject.org/docs/verifying-signatures.html) and run the bundle according to the instructions for [Windows](https://www.torproject.org/projects/torbrowser.html#windows), [OS X](https://www.torproject.org/projects/torbrowser.html#macosx), or [GNU/Linux](https://www.torproject.org/projects/torbrowser.html#linux).

On the first screen, where it says _Which of the following best describes your situation?_, click the **Configure** button.

<center><img src="https://people.torproject.org/~dcf/graphs/blogfiles/4.0-alpha-1-meek-conf-0.png" alt="Tor Network Settings “Which of the following best describes your situation?” screen with the “Configure” button highlighted."></center>

On the screen that says _Does this computer need to use a proxy to access the Internet?_, say **No** unless you know you need to use a proxy. meek supports using an upstream proxy, but most users don’t need it.

<center><img src="https://people.torproject.org/~dcf/graphs/blogfiles/4.0-alpha-1-meek-conf-1.png" alt="Tor Network Settings “Does this computer need to use a proxy to access the Internet?” screen with “No” selected."></center>

On the screen that says _Does this computer's Internet connection go through a firewall that only allows connections to certain ports?_, say **No** . As an HTTPS transport, meek only uses web ports, which are allowed by most firewalls.

<center><img src="https://people.torproject.org/~dcf/graphs/blogfiles/4.0-alpha-1-meek-conf-2.png" alt="Tor Network Settings “Does this computer's Internet connection go through a firewall that only allows connections to certain ports?” screen with “No” selected."></center>

On the screen that says _Does your Internet Service Provider (ISP) block or otherwise censor connections to the Tor Network?_, say **Yes** . Saying Yes will lead you to the screen for configuring pluggable transports.

<center><img src="https://people.torproject.org/~dcf/graphs/blogfiles/4.0-alpha-1-meek-conf-3.png" alt="Tor Network Settings “Does your Internet Service Provider (ISP) block or otherwise censor connections to the Tor Network?” screen with “Yes” selected."></center>

On the pluggable transport screen, select **Connect with provided bridges** and choose either **meek-amazon** or **meek-google** from the list. Probably both of them will work for you, so choose whichever feels faster. If one of them doesn’t work, try the other. Then click the **Connect** button.

<center><img src="https://people.torproject.org/~dcf/graphs/blogfiles/4.0-alpha-1-meek-conf-4.png" alt="Tor Network Settings “You may use the provided set of bridges or you may obtain and enter a custom set of bridges.” screen with “meek-google” selected."></center>

If it doesn’t work, you can write to the [tor-dev mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-dev), or to me personally at [dcf@torproject.org](mailto:dcf@torproject.org), or file a [new ticket](https://trac.torproject.org/projects/tor/newticket?component=meek).

