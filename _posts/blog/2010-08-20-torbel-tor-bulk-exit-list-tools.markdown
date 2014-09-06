---
layout: post
title: "TorBEL: The Tor Bulk Exit List Tools"
permalink: blog/torbel-tor-bulk-exit-list-tools
date: 2010-08-20
author: hbock
category: blog
tags: ["gsoc2010", "torbel"]
---

We have finally crossed the point of no return: 16 August 2010, 1900 UTC. Google Summer of Code 2010 is over; it's been a lot of fun and a lot of hard work participating in GSoC this year, and I hope that I have accomplished my goal. I took up the task of redesigning [TorDNSEL](https://exitlist.torproject.org), a DNSBL-style interface for querying information about Tor exit nodes, to be more thorough, more usable, and more maintainable. Out of this effort came TorBEL, a set of specifications and Python tools that try to address this problem.

The TorBEL codebase as released today contains several important
 pieces:

- A more thorough [specification](http://git.spanning-tree.org/index.cgi/torbel/tree/doc/test-spec.txt?id=torbel-0.1-gsoc) for active testing of the Tor network to determine fine-grained reachability through exit relays
- A [specification](http://git.spanning-tree.org/index.cgi/torbel/tree/doc/data-spec.txt?id=torbel-0.1-gsoc) for the export of this data in bulk to consumers, in CSV and JSON formats and via the DNSEL blocklist interface.
- A high-throughput implementation of the active testing scheme using the [Twisted](http://twistedmatrix.com/trac/) framework (torbel)
- A Python API (torbel.query) to easily query against these exports.
- An implementation of a DNSEL server (torbel.dnsel) written on top of twisted.names compatible with the original tordnsel that supports more query types and uses TorBEL's export formats and query API.

Although TorBEL is relatively stable at this point and does its job well, providing better answers where the current DNSEL is not accurate and providing an easy way for others to generate and consume exit node data, it is far from finished. Bugs need fixing and test accuracy can be improved further still, and TorBEL will need to face the test of running on a production system, used by real-world consumers like OFTC and FreeNode. I fully intend to stay with the Tor project as a volunteer developer and maintain TorBEL as long as it needs maintaining.

I'd like to thank Sebastian Hahn for being a fantastically helpful mentor and for sticking with me even through some frustrating late nights and my lack of regular communication. Sebastian has pushed me harder than I expected to meet my goals on time and to revise them when I could not do so. Working with me from another part of the world with a six-hour time difference made things interesting, although insomnia played a key role in keeping us in contact. I can be terribly difficult to get in touch with and it really didn't help working another part-time job for the entire coding duration. This caused a few problems, as Sebastian tried very hard to encourage me to work in the open and communicate often, which I often failed to do. I will try to improve my communications with Tor project members in the future.

In addition to Sebastian, I'd like to thank the many kind members of the Tor community for reaching out and helping me get up to speed and resolve many areas I had trouble with, including Nick Matthewson, Roger Dingledine, Mike Perry, Damian Johnson, and Ilja Hallberg. Without their unending help and resourcefulness I would have been stuck long ago.

All in all GSoC 2010 has been a great experience and I really hope to see that TorBEL gets some real-world usage in the very near future. I very much look forward to continuing work with the Tor developer community on TorBEL and hopefully other interesting projects as well.

