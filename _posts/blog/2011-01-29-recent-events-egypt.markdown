---
layout: post
title: "Recent events in Egypt"
permalink: blog/recent-events-egypt
date: 2011-01-29
author: ioerror
category: blog
tags: ["bridges", "censorship", "egypt", "internet access", "relays"]
---

The current state of affairs in Egypt looks quite bleak for people using Vodafone, Orange, TE Data, and other well-known service providers. It is reported that each of those companies was ordered by the Egyptian government to turn down their internet services. The nature of the order and its legality is of course very unclear at this time. What is known is that nearly in perfect unison many Egyptian ISPs turned down their BGP route announcements to countries outside of Egypt and from what we've been able to gather they're also not peering with each other. The cables connecting ( [FLAG](http://en.wikipedia.org/wiki/FALCON_(cable_system)) and [SEABONE](http://www.seabone.net/)) Egypt to the world are still _physically_ intact.

The impact of de-peering is significant; even if someone is able to get packets directly to the edge routers of TE Data or another ISP, no response will be forthcoming. [Renesys](http://www.renesys.com/blog/2011/01/egypt-leaves-the-internet.shtml), [RIPE](http://stat.ripe.net/egypt/), and [BGPmon](http://bgpmon.net/blog/?p=450) have fantastic technical details for those without access to an active BGP router.

At this point it is also well-known that the ISP Noor has been up through the entire event. With access to systems inside of Egypt, we have discovered that it appears to be entirely unfiltered - Tor works perfectly, controversial websites are not blocked, and it is even quite fast compared to our systems on other Egyptian networks. As of very late last night, systems from Noor were still unable to reach systems on TE Data or other networks in Egypt. Early this morning it appears that another ISP, Etisalat (AS36992), returned to the Internet (via nileonline.palermo7.pal.seabone.net) and we're working with contacts in Egypt to test any possible filtering and to ensure that Tor is functional on their network.

In our tests of the TE Data network before it disconnected, we found very heavy handed but sloppy filtering. Tests of popular websites revealed that TE Data filtered based on IP blocklists, they did not tamper with DNS queries, they did not trigger TCP resets on keywords, nor did they attempt to perform any kind of Man-In-The-Middle attacks on SSL or SSH connections. While it is possible that TE Data may have layer seven filtering or Deep Packet Inspection capabilities, it does not appear to have used any advanced filtering methods.

While the seemingly unfiltered nature of Noor's network is a positive development and sharply contrasts with the heavy filtering of TE Data's network, we have no methods for discovering data retention policies or wiretapping capabilities of any of the available networks in Egypt. We urge all people in Egypt to consider that any ISP may log data and depending on political outcomes, it may not be favorable to have easy to trace records of your online activities.

Many Egyptians are also using dial up services that route through the Egyptian controlled state telecommunications systems. While on the face this seems safe and it may very well be safer than a known filtered or probably wiretapped network, it's certainly not outside of the capabilities of the Egyptian authorities to decode or analyse these kinds of communications. We urge people who are using dial up systems or leased lines, VSAT or even BGAN connections to be cautious. The nature of any internet connection has a variable difficulty for monitoring but it is by no means impossible. That's why we're working so hard on Tor because the world needs software for traffic analysis resistance; the internet doesn't have this for free and certainly not in a country with a highly centralized internet architecture.

There is a serious trade off to be made by users in hostile network environments with major political instability: Tor usage is possibly detectable with a skilled adversary. Connections made with questionable "privacy" or "security" proxy services are certainly easier than detecting Tor because of their static nature. The same is true of VPN services: all of these things are probably detectable with the right understanding and the proper equipment. It goes without saying that entirely unprotected connections to known unfavorable sites or services is detectable and well within the reach of the Egyptian network operators.

Please understand that while we make no promises, we believe that Tor is currently the best option for people in this situation. It's what we use when we're in Egypt and it's what we think will serve people the best in Egypt when they have a network connection to the rest of the internet.

The number of users in Egypt in the last week has skyrocketed:
 ![](https://blog.torproject.org/files/eg-users2-2011-01-28.png)

The number of bridges run around the world has increased remarkably:
 ![](https://blog.torproject.org/files/running-bridges-2011-01-28.png)

Most impressively, the number of fully public Tor relays has increased:
 ![](https://blog.torproject.org/files/relays-diff-2011-01-28.png)

It appears that the Tor network itself has gained bandwidth capacity and geographical scope thanks to people concerned with the situation in Egypt. If you'd like to get involved, we'd love it if you could help by [running a Tor relay or a Tor bridge](https://www.torproject.org/getinvolved/volunteer.html.en).

Update: As of late January 30th, most of Egypt's BGP routes for residential access has been pulled from the Internet.

<thead><tr>
<th>Attachment</th>
<th>Size</th> </tr></thead><tbody>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/eg-users2-2011-01-28.png">eg-users2-2011-01-28.png</a></td>
<td>8.29 KB</td> </tr>
 <tr class="even">
<td><a href="https://blog.torproject.org/files/running-bridges-2011-01-28.png">running-bridges-2011-01-28.png</a></td>
<td>20.54 KB</td> </tr>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/relays-diff-2011-01-28.png">relays-diff-2011-01-28.png</a></td>
<td>42.41 KB</td> </tr>
</tbody>

