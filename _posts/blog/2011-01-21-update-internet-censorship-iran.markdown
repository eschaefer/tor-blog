---
layout: post
title: "Update on Internet censorship in Iran"
permalink: blog/update-internet-censorship-iran
date: 2011-01-21
author: phobos
category: blog
tags: ["great potato wall", "internet censorship", "iran", "ssl man-in-the-middle"]
---

Here's a quick update on what we're seeing from Tor clients in Iran. This is an update to [https://blog.torproject.org/blog/new-blocking-activity-iran](https://blog.torproject.org/blog/new-blocking-activity-iran "https://blog.torproject.org/blog/new-blocking-activity-iran"). It appears that one of the five Iranian ISPs is experimenting in blocking censorship circumvention tools; such as Tor, Freegate, Ultrasurf, and Hot Spot Shield. There have been reports that this update to censorship technologies was coming soon, [https://www.azadcyber.info/articles/1560](https://www.azadcyber.info/articles/1560 "https://www.azadcyber.info/articles/1560").

Previously, we had data suggesting that ssl-connections were being throttled or experiencing a forced reduced-throughput. It seems this is no longer the case. A simple IP address access list is used to stop access to the public Tor nodes, as well as many Tor bridges. An example of this blocklist on the Iranian Tor users:

![](https://blog.torproject.org/files/direct-users-2011-01-21-ir-2010-10-23.png)

and

![](https://blog.torproject.org/files/bridge-users-2011-01-21-ir-2010-10-23.png)

We are seeing success in users choosing to configure their Tor clients to use a [socks or https proxy](https://www.torproject.org/docs/proxychain) and then connecting to the public Tor network. The trick here is that Iranian tor users now look to be coming from wherever the open proxy is located. A few volunteers in Europe and SE Asia have setup [proxy servers](http://www.inet.no/dante/) restricted to Iranian IP space.

On a more technical level, here's what we were seeing last week for ssl manipulation, [https://blog.torproject.org/files/https-traffic-flow.txt](https://blog.torproject.org/files/https-traffic-flow.txt "https://blog.torproject.org/files/https-traffic-flow.txt"). What's interesting is the tor-server to client communication is with a TTL of 40. The TLSv1 Encrypted Alert is from the tor-server, except the TTL is 39. Unless the tor-server suddenly jumped one hop further from the client, something intercepted the connection and injected that packet on behalf of the tor-server.

This week we're seeing straight IP blocking after the ssl handshake starts, [https://blog.torproject.org/files/ip-blocking.txt](https://blog.torproject.org/files/ip-blocking.txt "https://blog.torproject.org/files/ip-blocking.txt"). In both cases, this is to the same tor bridge from the same tor client as before.

In a short few months, Iran has vastly improved the sophistication of their censorship technologies. Right now, the best option is to use tor through open socks/https proxies. A risk is the open proxies can see you are using tor, but cannot see the traffic passing through the open proxy, for everything is wrapped in layers of encryption by Tor. However, it appears the Iranian Potato Wall can detect Tor or not in any case by analyzing the traffic on the wire. We have reports this is true for other circumvention tools as well.

I thank the many people that have taken risks to share data with us.

<thead><tr>
<th>Attachment</th>
<th>Size</th> </tr></thead><tbody>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/direct-users-2011-01-21-ir-2010-10-23.png">direct-users-2011-01-21-ir-2010-10-23.png</a></td>
<td>14.75 KB</td> </tr>
 <tr class="even">
<td><a href="https://blog.torproject.org/files/bridge-users-2011-01-21-ir-2010-10-23.png">bridge-users-2011-01-21-ir-2010-10-23.png</a></td>
<td>11.93 KB</td> </tr>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/https-traffic-flow.txt">https-traffic-flow.txt</a></td>
<td>3.6 KB</td> </tr>
 <tr class="even">
<td><a href="https://blog.torproject.org/files/ip-blocking.txt">ip-blocking.txt</a></td>
<td>3.58 KB</td> </tr>
</tbody>

