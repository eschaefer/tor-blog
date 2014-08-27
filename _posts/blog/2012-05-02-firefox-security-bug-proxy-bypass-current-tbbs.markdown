---
layout: post
title: "Firefox security bug (proxy-bypass) in current TBBs"
permalink: firefox-security-bug-proxy-bypass-current-tbbs
date: 2012-05-02
author: rransom
category: blog
tags: ["dns bypass", "firefox", "security advisory", "tor browser bundle", "websockets"]
---

A user has discovered a severe security bug in Firefox related to websockets bypassing the SOCKS proxy DNS configuration. This means when connecting to a websocket service, your Firefox will query your local DNS resolver, rather than only communicating through its proxy (Tor) as it is configured to do. This bug is present in current Tor Browser Bundles (2.2.35-9 on Windows; 2.2.35-10 on MacOS and Linux).

To fix this dns leak/security hole, follow these steps:

1. Type “about:config” (without the quotes) into the Firefox URL bar. Press Enter.
2. Type “websocket” (again, without the quotes) into the search bar that appears below "about:config".
3. Double-click on “network.websocket.enabled”. That line should now show “false” in the ‘Value’ column.

See [Tor bug 5741](https://bugs.torproject.org/5741) for more details. We are currently working on new bundles with a better fix.

