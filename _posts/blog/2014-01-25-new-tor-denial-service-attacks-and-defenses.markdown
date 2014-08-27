---
layout: post
title: "New Tor Denial of Service Attacks and Defenses"
permalink: new-tor-denial-service-attacks-and-defenses
date: 2014-01-25
author: robgjansen
category: blog
tags: ["denial of service", "dos", "hidden services", "research"]
---

New work on denial of service in Tor will be presented at [NDSS '14 on Tuesday, February 25th, 2014](http://www.internetsociety.org/ndss2014/programme#session5):

<cite><br>
<b>The Sniper Attack: Anonymously Deanonymizing and Disabling the Tor Network</b><br>
by Rob Jansen, Florian Tschorsch, Aaron Johnson, and Björn Scheuermann<br>
To appear at the 21st Symposium on Network and Distributed System Security<br>
</cite>

[A copy of the published paper is now available](https://www-users.cs.umn.edu/~jansen/publications/sniper-ndss2014.pdf), as are my slides explaining the attacks in both [PPTX](https://www-users.cs.umn.edu/~jansen/talks/sniper-dcaps-20131011.pptx) and [PDF](https://www-users.cs.umn.edu/~jansen/talks/sniper-dcaps-20131011.pdf) formats.

We found a new vulnerability in the design of Tor's flow control algorithm that can be exploited to remotely crash Tor relays. The attack is an extremely **low resource** attack in which an adversary's bandwidth may be traded for a target relay's memory (RAM) at an amplification rate of one to two orders of magnitude. Ironically, the adversary can use Tor to protect it's identity while attacking Tor without significantly reducing the effectiveness of the attack.

We studied **relay availability** under the attack using [Shadow](https://shadow.github.io/), a discrete-event network simulator that runs the real Tor software in a safe, private testing environment, and found that we could disable each of the fastest guard and the fastest exit relay in a range of 1-18 minutes (depending on relay RAM capacity). We also found that the entire group of the top 20 exit relays, representing roughly 35% of Tor bandwidth capacity at the time of the analysis, could be disabled in a range of 29 minutes to 3 hours and 50 minutes. We also analyzed how the attack could potentially be used to **deanonymize** hidden services, and found that it would take between 4 and 278 hours before the attack would succeed (again depending on relay RAM capacity, as well as the bandwidth resources used to launch the attack).

Due to our devastating findings, we also designed three defenses that mitigate our attacks, one of which provably renders the attack ineffective. Defenses have been implemented and deployed into the Tor software to ensure that **the Tor network is no longer vulnerable as of Tor version 0.2.4.18-rc and later** . Some of that work can be found in Trac tickets [#9063](https://trac.torproject.org/projects/tor/ticket/9063), [#9072](https://trac.torproject.org/projects/tor/ticket/9072), [#9093](https://trac.torproject.org/projects/tor/ticket/9093), and [#10169](https://trac.torproject.org/projects/tor/ticket/10169).

In the remainder of this post I will detail the attacks and defenses we analyzed, noting again that this information is presented more completely (and more elegantly) in [our paper](https://www-users.cs.umn.edu/~jansen/publications/sniper-ndss2014.pdf).

* * *

# The Tor Network Infrastructure

The Tor network is a distributed system made up of thousands of computers running the Tor software that contribute their bandwidth, memory, and computational resources for the greater good. These machines are called Tor **relays** , because their main task is to forward or relay network traffic to another entity after performing some cryptographic operations. When a Tor user wants to download some data using Tor, the user's Tor client software will choose three relays from those available (an **entry** , **middle** , and **exit** ), form a path or **circuit** between these relays, and then instruct the third relay (the exit) to fetch the data and send it back through the circuit. The data will get transferred from its source to the exit, from the exit to the middle, and from the middle to the entry before finally making its way to the client.

# Flow Control

The client may request the exit to fetch large amounts of data, and so Tor uses a window-based [flow control](http://en.wikipedia.org/wiki/Flow_control_%28data%29) scheme in order to limit the amount of data each relay needs to buffer in memory at once. When a circuit is created, the exit will initialize its circuit **package** counter to 1000 cells, indicating that it is willing to send 1000 cells into the circuit. The exit decrements the package counter by one for every data cell it sends into the circuit (to the middle relay), and stops sending data when the package counter reaches 0. The client at the other end of the circuit keeps a **delivery** counter, and initializes it to 0 upon circuit creation. The client increments the delivery counter by 1 for every data cell it receives on that circuit. When the client's delivery counter reaches 100, it sends a special Tor control cell, called a SENDME cell, to the exit to signal that it received 100 cells. Upon receiving the SENDME, the exit adds 100 to its package counter and continues sending data into the circuit.

This flow control scheme limits the amount of outstanding data that may be in flight at any time (between the exit and the client) to 1000 cells, or about 500 KiB, per circuit. The same mechanism is used when data is flowing in the opposite direction (up from the client, through the entry and middle, and to the exit).

# The Sniper Attack

The new Denial of Service (DoS) attack, which we call **"The Sniper Attack"** , exploits the flow control algorithm to remotely crash a victim Tor relay by depleting its memory resources. The paper presents three attacks that rely on the following two techniques:

1. the attacker **stops reading from the TCP connection containing the attack circuit** , which causes the TCP window on the victim's outgoing connection to close and the victim to buffer up to 1000 cells; and
2. the attacker causes cells to be continuously sent to the victim (exceeding the 1000 cell limit and consuming the victim's memory resources) either by **ignoring the package window at packaging end** of the circuit, or by **continuously sending SENDMEs from the delivery end** to the packaging end even though no cells have been read by the delivery end.

I'll outline the attacks here, but remember that the [paper](https://www-users.cs.umn.edu/~jansen/publications/sniper-ndss2014.pdf) and [slides](https://www-users.cs.umn.edu/~jansen/talks/sniper-dcaps-20131011.pdf) provide more details and useful illustrations of each of the three versions of the attack.

## Basic Version 1 (attacking an entry relay)

In basic version 1, the adversary controls the client and the exit relay, and chooses a victim for the entry relay position. The adversary builds a circuit through the victim to her own exit, and then the exit continuously generates and sends arbitrary data through the circuit toward the client while ignoring the package window limit. The client stops reading from the TCP connection to the entry relay, and the entry relay buffers all data being sent by the exit relay until it is killed by its OS out-of-memory killer.

## Basic Version 2 (attacking an exit relay)

In basic version 2, the adversary controls the client and an Internet destination server (e.g. website), and chooses a victim for the exit relay position. The adversary builds a circuit through the victim exit relay, and then the client continuously generates and sends arbitrary data through the circuit toward the exit relay while ignoring the package window limit. The destination server stops reading from the TCP connection to the exit relay, and the exit relay buffers all data being sent by the client until it is killed by its OS out-of-memory killer.

## Efficient Version

Both of the basic versions of the attack above require the adversary to generate and send data, consuming roughly the same amount of upstream bandwidth as the victim's available memory. The efficient version reduces this cost by one to two orders of magnitude.

In the efficient version, the adversary controls **only a client** . She creates a circuit, choosing the victim for the entry position, and then instructs the exit relay to download a large file from some external Internet server. The client stops reading on the TCP connection to the entry relay, causing it to buffer 1000 cells.

At this point, the adversary may "trick" the exit relay into sending more cells by sending it a SENDME cell, even though the client has not actually received any cells from the entry. As long as this SENDME does not increase the exit relay's package counter to greater than 1000 cells, the exit relay will continue to package data from the server and send it into the circuit toward the victim. If the SENDME does cause the exit relay's package window to exceed the 1000 cell limit, it will stop responding on that circuit. However, the entry and middle node will hold the circuit open until the client issues another command, meaning its resources will not be freed.

The bandwidth cost of the attack after circuit creation is simply the bandwidth cost of occasionally sending a SENDME to the exit. The memory consumption speed depends on the bandwidth and congestion of non-victim circuit relays. We describe how to parallelize the attack using multiple circuits and multiple paths with diverse relays in order to draw upon Tor's inherent resources. We found that with roughly 50 KiB/s of upstream bandwidth, an attacker could consume the victim's memory at roughly 1 MiB/s. This is highly dependent on the victim's bandwidth capabilities: relays that use token buckets to restrict bandwidth usage will of course bound the attack's consumption rate.

Rather than connecting directly to the victim, the adversary may instead launch the attack through a separate Tor circuit using a second client instance and the "Socks4Proxy" or "Socks5Proxy" option. In this case, she may benefit from the anonymity that Tor itself provides in order to evade detection. We found that there is not a significant increase in bandwidth usage when anonymizing the attack in this way.

# Defenses

A simple but naive defense against the Sniper Attack is to have the guard node watch its queue length, and if it ever fills to over 1000 cells, kill the circuit. This defense does not prevent the adversary from parallelizing the attack by using multiple circuits (and then consuming 1000 cells on each), which we have shown to be extremely effective.

Another defense, called "authenticated SENDMEs", tries to protect against receiving a SENDME from a node that didn't actually receive 100 cells. In this approach, a 1 byte nonce is placed in every 100th cell by the packaging end, and that nonce must be included by the delivery end in the SENDME (otherwise the packaging end rejects the SENDME as inauthentic). As above, this does not protect against the parallel attack. It also doesn't defend against either of the basic attacks where the adversary controls the packaging end and ignores the SENDMEs anyway.

The best defense, as we suggested to the Tor developers, is to implement a custom, adaptive out-of-memory circuit killer in application space (i.e. inside Tor). The circuit killer is only activated when memory becomes scarce, and then it chooses the circuit with the oldest front-most cell in its circuit queue. This will prevent the Sniper Attack by killing off all of the attack circuits.

With this new defense in place, the next game is for the adversary to try to cause Tor to kill an honest circuit. In order for an adversary to cause an honest circuit to get killed, it must ensure that the front-most cell on its malicious circuit queue is at least slightly "younger" than the oldest cell on any honest queue. We show that the Sniper Attack is impractical with this defense: due to fairness mechanisms in Tor, the adversary must spend an extraordinary amount of bandwidth keeping its cells young — bandwidth that would likely be better served in a more traditional brute-force DoS attack.

Tor has implemented a version of the out-of-memory killer for circuits, and is currently working on [expanding this to channel and connection buffers](https://trac.torproject.org/projects/tor/ticket/10169) as well.

# Hidden Service Attack and Countermeasures

The paper also shows how the Sniper Attack can be used to deanonymize hidden services:

1. run a malicious entry guard relay;
2. run [the attack from Oakland 2013](http://freehaven.net/anonbib/#oakland2013-trawling) to learn the current guard relay of the target hidden service;
3. run the Sniper Attack on the guard from step 2, knocking it offline and causing the hidden service to choose a new guard;
4. repeat, until the hidden service chooses the relay from step 1 as its new entry guard.

The technique to verify that the hidden service is using a malicious guard in step 4 is the same technique used in step 2.

In the paper, we compute the expected time to succeed in this attack while running malicious relays of various capacities. It takes longer to succeed against relays that have more RAM, since it relies on the Sniper Attack to consume enough RAM to kill the relay (which itself depends on the bandwidth capacity of the victim relay). For the malicious relay bandwidth capacities and honest relay RAM amounts used in their estimate, we found that deanonymization would involve between 18 and 132 Sniper Attacks and take between ~4 and ~278 hours.

This attack becomes much more difficult if the relay is rebooted soon after it crashes, and the attack is ineffective when Tor relays are properly defending against the Sniper Attack (see the "Defenses" section above).

Strategies to defend hidden services in particular go beyond [those suggested here](https://blog.torproject.org/blog/improving-tors-anonymity-changing-guard-parameters) to include **entry guard rate-limiting** , where you stop building circuits if you notice that your new guards keep going down (failing closed), and **middle guards** , guard nodes for your guard nodes. Both of these strategies attempt to make it harder to coerce the hidden service into building new circuits or exposing itself to new relays, since that is precisely what is needed for deanonymization.

# Open Problems

The main defense implemented in Tor will start killing circuits when memory gets low. Currently, Tor uses a configuration option (MaxMemInCellQueues) that allows a relay operator to configure when the circuit-killer should be activated. There is likely not one single value that makes sense here: if it is too high, then relays with lower memory will not be protected; if it is too low, then there may be more false positives resulting in honest circuits being killed. Can Tor determine this setting in an OS-independent way that allows relays to automatically find the right value for MaxMemInCellQueues?

The defenses against the Sniper Attack prevent the adversary from crashing the victim relay, but the adversary may still consume a relay's bandwidth (and memory resources, to a critical level) at relatively low cost. This means that even though the Sniper Attack can no longer kill a relay, it can still consume a large amount of its bandwidth at a relatively low cost (similar to more traditional bandwidth amplification attacks). More analysis of **general bandwidth consumption attacks and defenses** remains a useful research problem.

Finally, [hidden services also need some love](https://blog.torproject.org/blog/hidden-services-need-some-love). More work is needed to redesign them in a way that does not allow a client to cause the hidden service to choose new relays on demand.

