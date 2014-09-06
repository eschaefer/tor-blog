---
layout: post
title: "Measuring Tor and Iran"
permalink: blog/measuring-tor-and-iran
date: 2009-06-19
author: phobos
category: blog
tags: ["directory services", "iran", "tor"]
---

I've been fielding some calls from the press about Tor and Iran. Someone quoted me as saying "double the clients from Iran over the past few days". We wondered, what are the real numbers? What does our network see from Iran? Is port 443 or https:// really blocked? Here's what we've discovered in the past day of working with the [new metrics](https://blog.torproject.org/blog/performance-measurements-and-blockingresistance-analysis-tor-network) we've developed to be safe to collect without compromising anyone's anonymity.

This first dataset is from one of the Directory Authorities. We have six authorities, so a plausible scaling factor is 6, assuming all authorities are seeing equal requests (it could be more or less than 6, too). We don't know if the authorities are seeing equal requests, as they listen on different TCP ports, are located in different parts of the world, and clients will chose one randomly. This graph roughly shows the number of requests from new Tor clients coming from IP addresses that our geoip database reports as Iran.

<center><img height="375" width="500" src="https://blog.torproject.org/files/new_tor_clients_from_iranian_ip_space.png"></center>

UPDATE 2009-06-24: Updated the graph with numbers through yesterday

The second dataset is from one Directory Mirror, of which there are hundreds. This mirror is only accessible on port 443, which is rumored to be blocked in parts of Iran over the past few days.

<center><img height="375" width="500" src="https://blog.torproject.org/files/tor_clients_from_iranian_ip_space_(port_443).png"></center>

The data points in the second graph are very rough, since they're an estimate of the total number of Tor users in Iran based on numbers from only one relay. In addition, we looked at some other relays running on port 443, and they also didn't show anywhere near the spike that we see in the directory authority graph above. The authority isn't listening on 443 -- perhaps that means there's some truth to the rumors that port 443 has been blocked recently in Iran. We look forward to having more precise data later on.

<thead><tr>
<th>Attachment</th>
<th>Size</th> </tr></thead><tbody>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/tor_clients_from_iranian_ip_space_(port_443).png">tor_clients_from_iranian_ip_space_(port_443).png</a></td>
<td>35.98 KB</td> </tr>
 <tr class="even">
<td><a href="https://blog.torproject.org/files/new_tor_clients_from_iranian_ip_space.png">new_tor_clients_from_iranian_ip_space.png</a></td>
<td>32.92 KB</td> </tr>
</tbody>

