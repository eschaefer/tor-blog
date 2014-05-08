---
layout: post
title: "Vidalia 0.2.5 Released"
permalink: vidalia-025-released
date: 10/17/2009
author: phobos
category: blog
tags: ["bug fixes", "usability enhancements", "vidalia release"]
---

On October 14th we released Vidalia 0.2.5. Changes are:

- Add support in the Network settings page for configuring the  
 Socks4Proxy and Socks5Proxy\* options that were added in  
 Tor 0.2.2.1-alpha. Patch from Christopher Davis.
- Add a "Automatically distribute my bridge address" checkbox (enabled  
 by default) to the bridge relay settings options. (Ticket #524)
- Add ports 7000 and 7001 to the list of ports excluded by the IRC  
 category in the exit policy configuration tab. (Ticket #517)
- Add a context menu for highlighted event items in the "Basic" message  
 log view that allows the user to copy the selected item text to the  
 clipboard.
- Maybe fix a time conversion bug that could result in Vidalia  
 displaying the wrong uptime for a relay in the network map.
- Stop trying to enforce proper quoting and escaping of arguments to be  
 given to the proxy executable (e.g., Polipo). Now the user is on their  
 own for properly formatting the command line used to start the proxy  
 executable. (Ticket #523)

