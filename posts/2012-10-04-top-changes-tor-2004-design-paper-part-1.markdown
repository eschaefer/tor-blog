---
layout: post
title: "Top changes in Tor since the 2004 design paper (Part 1)"
permalink: top-changes-tor-2004-design-paper-part-1
date: 10/04/2012
author: nickm
category: blog
tags: []
---

The main academic reference for Tor is ["Tor: The Second-Generation Onion Router" by Dingledine, Mathewson, and Syverson](https://svn.torproject.org/svn/projects/design-paper/tor-design.pdf). But that paper was published back in 2004, and Tor has evolved since then. So Steven Murdoch and Nick Mathewson are currently preparing an updated version of the Tor design paper, to include new design changes and research results concerning Tor over the last 8 years.

In this series of posts, we (Steven and Nick) will try to summarize the most interesting or significant changes to Tor's design since the publication of the original paper. We're only going to cover the stuff we think is most interesting, and we'll aim to do so in an interesting way.

We think this will be a three part series. In this first part, we'll cover the evolution of Tor's directory system, and some performance improvements in Tor's circuit creation and cell scheduling logic.

## 1. Node discovery and the directory protocol

Since the earliest versions of Tor, we knew that node discovery would require a better implementation than we had. There are a few key issues that any anonymity network's node discovery system needs to solve.

Every client needs to be selecting nodes from the same probability distribution, or an adversary could be able to exploit differences in client knowledge. In the worst case, if an adversary can cause one client to know about an exit node that no other client uses, the adversary can know that all traffic leaving that exit is coming from the targeted client. But even in more mild cases, where (say) every client knows every node with P=90%, an adversary can use this information to [attack users](http://freehaven.net/anonbib/#danezis-pet2008).

While there has been some work on quantifying these so-called "epistemic attacks," we're proceeding with the conservative assumption that clients using separate sets of nodes are likely to be partitionable from one other, and so the set of nodes used by all clients needs to be uniform.

The earliest versions of Tor solved this problem with a "Directory" object – each server generated a signed "router descriptor", and uploaded it to one of a small set (three) of "directory authorities". Each of these authorities generated a signed concatenated list of router descriptors, and served that list to clients over HTTP.

This system had several notable problems:

- Clients needed to download the same descriptors over and over, whether they needed them or not.
- Each client would believe whichever directory authority it had spoken to most recently: rather than providing distributed trust, each authority was fully trusted in its own right, and any one misbehaving authority could completely compromise all the clients that talked to it.
- To the extent that directory authorities disagreed, they created partitions in client knowledge, which could in the worst case allow an adversary to partition clients based on which authority's directory each client had downloaded most recently.
- The load on the authorities promised to grow excessive, as every client contacted every authority.
- The contents of the directory were sent unencrypted, which made them trivially easy to fingerprint on the wire.

### Early changes in the Version 1 Directory System

Our earliest changes focused on improving scalability rather than improving the trust model. We began by having each authority publish two documents, rather than one: a directory that contained all the router descriptors, and a "network status" document that was a list of which descriptors were up and which were down (Tor 0.0.8pre1, in Jul 2004). Clients could download the latter more frequently to avoid using down servers, and refresh the former only periodically.

We also added a caching feature in Tor 0.0.8pre1, where nodes could act as directory caches. With this feature, once a client had a directory, it no longer needed to contact the directory authorities every time it wanted to update it, but rather could contact a cache instead.

### The Version 2 Directory System (deprecated)

In Tor 0.1.1.8-alpha (Oct 2005), we took our first shot at solving the trust model. Now, we had each authority sign a more complete network status statement, including a list of all the nodes that it believed should be in the network, a digest of each node's public key, and a digest of each node's router descriptor. Clients would download one of these documents signed by each authority, and then compute, based on all the documents they had, which collection of nodes represented the consensus view of all the authorities.

To get router descriptors, clients would then contact one or more caches, and ask for the descriptors they believed represented the consensus view of all the authorities.

This approach meant that a single rogue directory authority could no longer completely control any client's view of the network. Clients became **more** fragmented, however, since instead of falling into one of N possible groups based on which authority they contacted most recently, they fell into one of M<sup>N</sup> groups where N was the number of authorities and M was the number of recently valid opinions from each authority.

Around this time we also had authorities begin assigning flags to nodes, so that in addition to recording "up" or "down" for each node, authorities could also declare whether nodes were fast, stable, likely to be good guard nodes, and so forth.

All of the improvements so far were oriented toward saving bandwidth at the server side: we figured that clients had plenty of bandwidth, and we wanted to avoid overloading the authorities and caches. But if we wanted to add more directory authorities (a majority of 5 is still an uncomfortably small number), bootstrapping clients would have to fetch one more network status for every new authority. By early 2008, each status document listed 2500 relay summaries and came in around 175KB compressed, meaning you needed 875KB of status docs when starting up, and then another megabyte of descriptors after that. And we couldn't add more authorities without making the problem even worse.

### Version 3: Consensus and Directory Voting

To solve the problems with the v2 directory protocol, Tor 0.2.0.3-alpha (Jul 2007) introduced a directory voting system, where the authorities themselves would exchange vote documents periodically (currently once per hour), compute a consensus document based on everyone's votes, and all sign the consensus.

Now clients only need to download a single signed consensus document periodically, and check that it is signed by a sufficiently large fraction of the authorities that the client knows about. This gives clients a uniform view of the network, makes it harder still for a small group of corrupt authorities to attack a client, and limits the number of documents they need to download.

The voting algorithm is _ad hoc_, and is by no means the state of the art in byzantine fault tolerance. Our approach to failures to reach a consensus (which have been mercifully infrequent) is to find what's wrong and fix it manually.

### Saving bytes with microdescriptors

Now that the consensus algorithm finally matched what we had in mind when we wrote the first Tor paper, it was time to address the protocol's verbosity.

Out of all the data in a typical 1500-byte server descriptor, a client really only needs to know what ports it supports exiting to, its current RSA1024 onion key, and other information that is fully redundant with its listing in the consensus network status document.

One crucial observation is that signatures on the router descriptors themselves don't actually help clients: if there were enough hostile authorities to successfully convince the clients to use a descriptor that a router didn't actually sign, they could as easily convince the clients to use a descriptor signed with a phony identity key.

This observation let us move (in Tor 0.2.3.1-alpha, May 2011) to a design where the authorities, as part of their voting process, create an abbreviated version of each descriptor they recommend. Currently, these contain only a short summary of the router's exit policy, and the router's current onion key. Clients now download these abbreviated "microdescriptors", which cuts the information downloaded each node by about 75%. Further, because the data here change relatively infrequently, it cuts down the frequency with which clients fetch new information about each router at all.

### Tunneling directory connections over Tor

In 0.1.2.5-alpha (Jan 2007), we added support by default for clients to download all directory documents over HTTP over Tor, rather than by contacting directories and caches over unencrypted HTTP. This change helps clients resist fingerprinting.

Because clients aren't using Tor for anonymity on directory connections, they build single-hop circuits. We use HTTP over a one hop Tor circuit, rather than plain old HTTPS, so that clients can use the same TLS connection both for a directory fetch and for other Tor traffic.

## 2. Security improvements for hidden services

### Decentralized hidden-service directory system

A partly-centralized directory infrastructure makes sense for Tor nodes, since every client is supposed to be able to know about every node, but it doesn't make a great deal of sense for hidden services.

To become more censorship-resistant, we started (in Tor 0.2.0.10-alpha, Nov 2007) to instead use the Tor network itself to cache and serve hidden service descriptors. Now, instead of publishing their hidden service descriptors anonymously to a small fixed set of hidden service authorities, hidden services publish to a set of nodes whose identity keys are [closest](http://en.wikipedia.org/wiki/Consistent_hashing) to a hash of the service's identity, the current date, and a replica number.

### Improved authorization model for hidden services

We also added improved support for authentication to hidden services. Optionally, to use a hidden service, a client must know a shared key, and use this key to decrypt the part of a hidden service descriptor containing the introduction points. It later must use information in that encrypted part to authenticate to any introduction point it uses, and later to the hidden service itself. One of the main uses of authentication here is to hide _presence_ -- only authenticated users can learn [whether the hidden service is online](http://petsymposium.org/2008/hotpets/vrtprsvc.pdf).

## 3. Faster first-hop circuit establishment with CREATE\_FAST

At each stage of extending a circuit to the next hop, the client carries out a Diffie-Hellman (DH) key agreement protocol with that next hop. This step provides confidentiality (and forward secrecy) of the relay cell payload as it is passed on by intermediate hops. Originally Tor also carried out DH with the first hop, even though there was already a DH exchange as part of the TLS handshake. DH is quite computationally expensive for both ends, so Tor 0.1.1.10-alpha (Dec 2005) onwards skipped the DH exchange on the first hop by sending a CREATE\_FAST (as opposed to a standard CREATE) cell, which generates key material simply by hashing random numbers sent by the client and server.

## 4. Cell queueing and scheduling

The original Tor design left the fine-grained handling of incoming cells unspecified: every circuit's cells were to be decrypted and delivered in order, but nodes were free to choose which circuits to handle in any order they pleased.

Early versions of Tor also punted on the question: they handled cells in the order they were received on incoming OR connections, encrypting/decrypting them and handing them off immediately to the next node on the circuit, or to the appropriate exit or entry connection. This approach, however, frequently created huge output buffers where quiet circuits couldn't get a cell in edgewise.

Instead, Tor currently places incoming cells on a per-circuit queue associated with each circuit. Rather than filling all output buffers to capacity, Tor instead fills them up with cells on a near just-in-time basis.

When we first implemented these cell queues in 0.2.0.1-alpha (Jun 2007), we chose which cells to deliver by rotating the circuits in a round-robin approach. In Tor 0.2.2.7-alpha (Jan 2010), we began to instead [favor the circuits on each connection that had been quiet recently](http://freehaven.net/anonbib/#ccs10-scheduling), so that a circuit with small, infrequent amounts of cells will get better latency than a circuit being used for a bulk transfer. (Specifically, when we are about to put a cell on an outgoing connection, we choose the circuit which has sent the lowest total exponentially-decaying number of cells so far. Currently, each cell has a 30-second half-life.)

In Part 2 we will look at changes to how Tor selects paths and the new anti-censorship measures.

