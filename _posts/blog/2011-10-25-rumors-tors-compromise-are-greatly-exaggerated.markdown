---
layout: post
title: "Rumors of Tor's compromise are greatly exaggerated"
permalink: rumors-tors-compromise-are-greatly-exaggerated
date: 2011-10-25
author: phobos
category: blog
tags: ["anonymity research", "attacks on tor", "facts", "freedom hosting", "hidden services", "research", "tor compromise", "winning the attention economy"]
---

There are two recent stories claiming the Tor network is compromised. It seems it is easier to get press than to publish research, work with us on the details, and propose solutions. Our comments here are based upon the same stories you are reading. We have no insider information.

The first story has been around 'Freedom Hosting' and their hosting of child abuse materials as exposed by [Anonymous Operation Darknet](http://arstechnica.com/business/news/2011/10/anonymous-takes-down-darknet-child-porn-site-on-tor-network.ars). We're reading the press articles, pastebin urls, and talking to the same people as you. It appears 'Anonymous' cracked the Apache/PHP/MySQL setup at Freedom Hosting and published some, or all, of their users in the database. These sites happened to be hosted on a [Tor hidden service](https://www.torproject.org/docs/hidden-services.html.en). Further, 'Anonymous' used a somewhat recent RAM-exhaustion denial of service attack on the 'Freedom Hosting' Apache server. It's a simple resource starvation attack that can be conducted over low bandwidth, low resource requirement connections to individual hosts. This isn't an attack on Tor, but rather an attack on some software behind a Tor hidden service. This attack was discussed in a thread on the [tor-talk](https://lists.torproject.org/pipermail/tor-talk/2011-October/021822.html) mailing list starting October 19th.

The second story is around Eric Filiol's claims of compromising the Tor network leading up to his Hackers to Hackers talk in Brazil in a few days. This claim was initially announced by some French websites; however, it has spread further, such as this [Hacker News](http://thehackernews.com/2011/10/tor-anonymizing-network-compromised-by.html) story.

Again, the [tor-talk](https://lists.torproject.org/pipermail/tor-talk/2011-October/021722.html) mailing list had the first discussions of these attacks back on October 13th. To be clear, neither Eric nor his researchers have disclosed anything about this attack to us. They have not talked to us, nor shared any data with us — despite some mail exchanges where we reminded him about the phrase "responsible disclosure".

Here's the attack as we understand it, from reading the various press reports:

They enumerated 6000 IP addresses that they think are Tor relays. There aren't that many Tor relays in the world — [2500](https://metrics.torproject.org/network.html) is a more accurate number. We're not sure what caused them to overcount so much. Perhaps they watched the Tor network over a matter of weeks and collected a bunch of addresses that aren't relays anymore? The set of relays is public information, so there's no reason to collect your own list and certainly no reason to end up with a wrong list.

One-third of the machines on those IP addresses are vulnerable to operating system or other system level attacks, meaning he can break in. That's quite a few! We wonder if that's true with the real Tor network, or just their simulated one? Even ignoring the question of what these 3500 extra IP addresses are, it's important to remember that one-third by number is not at all the same as one-third by capacity: Tor clients load-balance over relays based on the relay capacity, so any useful statement should be about how much of the _capacity_ of the Tor network is vulnerable. It would indeed be shocking if one-third of the Tor network by capacity is vulnerable to external attacks.

(There's also an aside about enumerating [bridges](https://www.torproject.org/docs/bridges). They say they found 181 bridges, and then there's a quote saying they "now have a complete picture of the topography of Tor", which is a particularly unfortunate time for that quote since there are currently around 600 bridges running.)

We expect the talk will include discussion about some cool Windows trick that can modify the crypto keys in a running Tor relay that you have local system access to; but it's simpler and smarter just to say that when the attacker has local system access to a Tor relay, the attacker controls the relay.

Once they've broken into some relays, they do congestion attacks like [packet spinning](http://freehaven.net/anonbib/#torspinISC08) to congest the relays they couldn't compromise, to drive users toward the relays they own. It's unclear how many resources are needed to keep the rest of the relays continuously occupied long enough to keep the user from using them. There are probably some better heuristics that clients can use to distinguish between a loaded relay and an unavailable relay; we look forward to learning how well their attack here actually worked.

From there, the attack gets vague. The only hint we have is this nonsense sentence from the article:

> The remaining flow can then be decrypted via a fully method of attack called "to clear unknown" based on statistical analysis.

Do they have a new attack on AES, or on OpenSSL's implementation of it, or on our use of OpenSSL? Or are they instead doing some sort of timing attack, where if you own the client's first hop and also the destination you can use statistics to confirm that the two flows are on the same circuit? There's a history of [confused researchers](https://blog.torproject.org/blog/one-cell-enough) proclaiming some sort of novel active attack when passive correlation attacks are much simpler and just as effective.

So the summary of the attack might be "take control of the nodes you can, then congest the other ones so your targets avoid them and use the nodes you control. Then do some unspecified magic crypto attack to defeat the layers of encryption for later hops in the circuit." But really, these are just guesses based on the same news articles you're reading. We look forwarding to finding out if there's actually an attack we can fix, or if they are just playing all the journalists to get attention.

More generally, there are two broader lessons to remember here. First, research into anonymity-breaking attacks is how the field moves forward, and using Tor for your target is [common](http://freehaven.net/anonbib/) because a) it's resistant to all the simpler attacks and b) we make it [really easy](https://www.torproject.org/getinvolved/research.html.en) to do your research on. And second, remember that most other anonymity systems out there fall to these attacks so quickly and thoroughly that no researchers even talk about it anymore. For some recent examples, see the single-hop proxy discussions in [How Much Anonymity does Network Latency Leak?](http://freehaven.net/anonbib/#tissec-latency-leak) and [Website Fingerprinting in Onion Routing Based Anonymization Networks](http://freehaven.net/anonbib/#wpes11-panchenko).

I thank Roger, Nick, and Runa for helping with this post.

