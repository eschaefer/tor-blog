---
layout: post
title: "Tor and the BEAST SSL attack"
permalink: tor-and-beast-ssl-attack
date: 09/24/2011
author: nickm
category: blog
tags: ["internals", "security", "ssl"]
---

Today, Juliano Rizzo and Thai Duong presented a new attack on TLS Ekoparty security conference in Buenos Aires. Let's talk about how it works, and how it relates to the Tor protocol.

Short version: Don't panic. The Tor software itself is just fine, and the free-software browser vendors look like they're responding well and quickly. I'll be talking about why Tor is fine; I'll bet that the TBB folks will have more to say about browsers sometime soon.

There is some discussion of the attack and responses to it out there already, written by [seriously smart cryptographers](http://www.schneier.com/blog/archives/2011/09/man-in-the-midd_4.html) and [high-test browser security people](http://www.imperialviolet.org/2011/09/23/chromeandbeast.html). But I haven't seen anything out there yet that tries to explain what's going on for people who don't know TLS internals and CBC basics.

So I'll do my best. This blog post also assumes that _I_ understand the attack. Please bear with me if I'm wrong about that.

Thanks to the authors of the paper for letting me read it and show it to other Tor devs. Thanks also to Ralf-Philipp Weinmann for helping me figure the analysis out.

## The attack

### How the attack works: Basic background

This writeup assumes that you know a little bit of computer stuff, and you know how xor works.

Let's talk about block ciphers, for starters. A [block cipher](http://en.wikipedia.org/wiki/Block_cipher) is a cryptographic tool that encrypts a small chunk of plaintext data into a same-sized chunk of encrypted data, based on a secret key.

In practice, you want to encrypt more than just one chunk of data with your block cipher at a time. What do you do if you have a block cipher with a 16-byte block (like AES), when you need to encrypt a 256-byte message? When most folks first consider this problem, they say something like "Just split the message into 16-byte chunks, and encrypt each one of those." That's an old idea (it's called ECB, or " [electronic codebook](http://en.wikipedia.org/wiki/Block_cipher_modes_of_operation#Electronic_codebook_.28ECB.29)"), but it has some serious problems. Most significantly, if the same 16-byte block appears multiple times in the plaintext, the ciphertext will also have identical blocks in the same position. The Wikipedia link above has a cute demonstration of this.

Okay, so nobody reasonable uses ECB. Some people, though, do use a mode called CBC, or " [Cipher Block Chaining](http://en.wikipedia.org/wiki/Block_cipher_modes_of_operation#Cipher-block_chaining_.28CBC.29)." With CBC, when you want to encrypt a message, you start your ciphertext message with a single extra random block, or IV ("initialization vector"). Now, when you go to encrypt each plaintext block to get its ciphertext block, you first [xor](http://en.wikipedia.org/wiki/Xor) the plaintext with the previous ciphertext. (So you xor the IV with the first plaintext block, encrypt that, and output it. Then you xor that ciphertext block with the second plaintext block, encrypt that, output it, and so on. The Wikipedia page has pretty good examples and illustrations here too.)

TLS and its earlier incarnation, SSL, are the encryption protocols that many applications, including Tor, use to send streams of encrypted data. They use CBC mode for most of their block ciphers. Unfortunately, before TLS version 1.1, they made a bad mistake. Instead of using a new random IV for every TLS message they sent, they used the ciphertext of the last block of the last message as the IV for the next message.

Here's why that's bad. The IV is not just supposed to be random-looking; it also needs to be something that an attacker cannot predict. If I know that you are going to use IV x for your next message, and I can trick you into sending a message that starts with a plaintext block of [(NOT x) xor y], then you will encrypt y for me.

That doesn't sound too bad. But [Wei Dai](http://www.mail-archive.com/openssl-dev@openssl.org/msg10664.html) and [Gregory V. Bard](http://eprint.iacr.org/2004/111.pdf) both found ways to exploit this to learn whether a given ciphertext block corresponds to a given plaintext. The attacker makes the user encrypt C' xor p, where p is the guessed plaintext and C' is the ciphertext block right before where the attacker thinks that plaintext was. If the attacker guessed right, then the user's SSL implementation outputs the same ciphertext as it did when it first encrypted that block.

And even **that** doesn't sound too bad, even in retrospect. In order to mount this attack, an adversary would need to be watching your internet connection, and be able to force you to start your next TLS record with a given string of his choice, and be able to guess something sensitive that you said earlier, and guess which part of your TLS stream might have corresponded to it.

Nevertheless, crypto people implemented workarounds. Better safe than sorry! In version 1.1 of the TLS protocol, every record gets a fresh IV, so the attacker can't know the IV of the next message in advance. And OpenSSL implemented a fix where, whenever they're about to send a TLS record, they send an empty TLS record immediately before, and then send the record with the message in it. The empty TLS record is enough to make the CBC state change, effectively giving the real message a new IV that the attacker can't predict.

These fixes haven't gotten very far in the web world, though. TLS 1.1 isn't widely implemented or deployed, even though the standard has been out since 2006. And  
OpenSSL's "empty record" trick turns out to break some non-conformant SSL implementations, so lots of folks turn it off. (The OpenSSL manual page for the option in question even says that "it is usually safe" to do so.)

I suppose that, at the time, this seemed pretty reasonable. Guessing a plaintext is hard: there are something like 3.4 x 10^38 possible values. But as they say, attacks only get better.

### How the attack works: What's new as of today

Juliano Rizzo and Thai Duong have two contributions, as I see it. (And please correct me if I'm getting this wrong; I have not read the literature closely!) First, they came up with a scenario to implement a pretty clever variation of Dai's original attack.

Here's a simplified version, not exactly as Rizzo and Duong present it. Let's suppose that, for some reason, the user has a secret (like a web cookie) that they send in every TLS record. And let's assume also that the attacker can trick the user into inserting any number of characters in their plaintext at the start of the record right before the secret. So the plaintext for every record is "Evil | Secret", where Evil is what the attacker chooses, and Secret is the secret message. Finally, let's suppose that the attacker can make the user send as many records as he wants.

The ability to decide where block boundaries fall turns out to be a big deal. Let's suppose that instead of filling up a full plaintext block with 16 bytes of Evil, the attacker only fills up 15 bytes... so the block will have 15 bytes the attacker controls, and one byte of the secret.

Whoops! There are only 256 possible values for a single byte, so the attacker can guess each one in turn, and use the older guess-checking attack to see if he guessed right. And once the attacker knows the first byte, he starts sending records with 14 attacker-controlled bytes, one byte that he knows (because he made a bunch of guesses and used the older attack to confirm which was right), and one byte that he doesn't. Again, this block has only 256 possible values, and so guessing each one in turn is efficient.

They then show how to extend this to cases where the attacker doesn't actually control the start of the block, but happens to know (or is able to guess) it, and make other extensions to the attack.

The second neat facet of Duong and Rizzo's work is that they actually found some ways to make this attack work against web browsers. That's no mean feat! You need to find a way to trick a web client into sending requests where you control enough of the right parts of them to mount this attack, and you need to be able to do it repeatedly. It seems to have taken a lot of HTTP hackery, but it seems they managed to do it. There's more detailed information here at [Eric Rescorla's blog](http://www.educatedguesswork.org/2011/09/security_impact_of_the_rizzodu.html), and of course once Juliano and Thai have their paper out, there will be even more to goggle at. This is really clever stuff IMO.

[Disclaimer: Again, I may have made mistakes above; if so, I will correct it when I wake up in the morning, or sooner. Please double-check me if you know this work better than I do.]

## So, does this attack work on Tor?

Nope.

Tor uses OpenSSL's "empty fragment" feature, which inserts a single empty TLS record before every record it sends. This effectively randomizes the IV of the actual records, like a low-budget TLS 1.1. So the attack is simply stopped.

This feature has been in OpenSSL since 0.9.6d: see item 2 in [Bodo Müller's good old CBC writeup](http://www.openssl.org/~bodo/tls-cbc.txt) for full details on how it works. It makes our SSL incompatible with some standards-non-compliant TLS implementations... but we don't really care there, since all of the TLS implementations that connect to the Tor network are OpenSSL, or are compatible with it.

Tor requires OpenSSL 0.9.7 or later, and has since 0.2.0.10-alpha. Amusingly, we were considering dropping our use of the empty fragment feature as "probably unnecessary" in 2008, but we never got around to it. I sure don't think we'll be doing that now!

Now, it's possible that clients we didn't write might be using other TLS implementations, but the opportunity for plaintext injection on client->relay links is much lower than on relay->relay links; see below. As far as I know, there are no Tor server implementations compatible with the current network other than ours.

Also, this only goes for the Tor software itself. Applications that use TLS need to watch out. Please install patches, and look for new releases if any are coming out soon.

## But what if...

### Okay, but would it work if we didn't use OpenSSL's empty-fragment trick?

For fun, what would our situation be if we weren't using openssl's empty fragment trick?

I'm going to diverge into Tor protocol geekery here. **All of the next several sections are probably irrelevant** , since the OpenSSL trick above protects Tor's TLS usage already. I'm just into analyzing stuff sometimes... and at the time I originally wrote this analysis, we didn't have confirmation about whether the OpenSSL empty-record trick would help or not.

This part will probably be a little harder to follow, and will require some knowledge of Tor internals. You can find all of our documents and specifications online at our handy [documentation page](https://www.torproject.org/docs/documentation.html#DesignDoc) if you've got some free time and you want to come up to speed.

The attack scenario that makes sense is for an attacker to be trying to decrypt stuff sent from one Tor node to another, or between a Tor node and a client. The attacker is not one of the parties on the TLS link, obviously: if they were, they'd already know the plaintext and would not need to decrypt it.

First, let's make some assumptions to make things as easy for the attacker as possible. Let's assume that the attacker can trivially inject chosen plaintext, and can have the TLS records carve up the plaintext stream anywhere he wants.

(Are those assumptions reasonable? Well, it's easy to inject plaintext on a relay->relay link: sending a node an EXTEND cell will make it send any CREATE cell body that you choose, and if you have built a circuit through a node, you can cause a RELAY cell on that node to have nearly any body you want, since the body is encrypted/decrypted in counter mode. I don't see an obvious way to make a node send a chosen plaintext to a client or make a client send a chosen plaintext to a node, but let's pretend that it's easy to do that too.

The second assumption, about how it's easy to make the boundaries of TLS records fall wherever you want, is likely to be more contentious; see "More challenges for the attacker" below.)

Also let's assume that on the targeted link, traffic for only one client is sent. An active attacker might arrange this through a trickle attack or something.

I am assuming that the attacker is observing ciphertext at a targeted node or client, but not at two targeted places that allow him to see the same traffic enter and leave the network: by our threat model, any attacker who can observe two points on a circuit is assumed to win via traffic correlation attacks.

I am going to argue that even then, the earlier attack doesn't get the attacker anything, and the preconditions for the Duong/Rizzo attack don't exist.

### CLAIM 1: The earlier (Dai/Bard) attacks don't get the attacker anything against the Tor protocol

There are no interesting guessable plaintexts sent by a well-behaved client or node[\*] on a Tor TLS link: all are either random, nearly random, or boring from an attacker's POV.

[\*] What if a node or client is hostile? Then it might as well just publish its plaintext straight to the attacker.

Argument: CREATE cell bodies contain hybrid-encrypted stuff that (except for its first bit) should be indistinguishable from random bits, or pretty close to indistinguishable from random bits. CREATED cell bodies have a DH public key and a hash: also close to indistinguishable from random. CREATE\_FAST cell bodies \*are\* randomly generated, and CREATED\_FAST cell bodies have a random value and a hash.

RELAY and RELAY\_EARLY cell bodies are encrypted with at least one layer of AES\_CTR, so they shouldn't be distinguishable from random bits either.

DESTROY, PADDING, NETINFO, and VERSIONS cells do not have interesting bodies. DESTROY and PADDING bodies are either 0s or random bytes, and NETINFO and VERSIONS provide only trivial information that you can learn just by connecting to a node (the time of day, its addresses, and which versions of the Tor link protocol it speaks).

That's cell bodies. What about their headers? A Tor cell's header has a command and a circuit ID that take up only 3 bytes. Learning the command doesn't tell you anything you couldn't notice by observing the encrypted link in the first place and doing a little traffic analysis. The link-local 2-byte circuit ID is random, and not  
interesting per se, but possibly interesting if you could use it to demultiplex traffic sent over multiple circuits. I'll discuss that more below at the end of the next section.

### CLAIM 2: You can't do the Duong/Rizzo attack against the Tor protocol either

The attack requires that some piece of sensitive information M that you want to guess be re-sent repeatedly after the attacker's chosen plaintext. That is, it isn't enough to get the target to send one TLS record containing (evil | M) -- you need to get it to send a bunch of (evil | M) records with the same M to learn much about M.

But in Tor's link protocol, nothing sensitive is sent more than once. Tor does not retry the same CREATE or CREATE\_FAST cells, or re-send CREATED or CREATED\_FAST cells. RELAY cells are encrypted with at least one layer of AES\_CTR, and no RELAY cell body is sent more than once. (The same applies to RELAY\_EARLY.)

PADDING cells have no interesting content to learn. VERSIONS and NETINFO cells are sent only at the start of the TLS connection (and their contents are boring too).

What about the cell headers? They contain a command and a circuit ID. If a node is working normally, you can already predict that most of the commands will be RELAY. You can't predict that any given circuit's cells will be sent reliably after yours, so you can't be sure that you'll see the same circuitID over and over... unless if you've done a trickle attack, in which case you already know that all the cells you're seeing are coming from the same place; or if you've lucked out and one circuit is way louder than all the others, but you would already learn that from watching the node's network. So I think that anything that is sent frequently enough to be decryptable with this method is not in fact worth decrypting. But see the next section.

### Hey, what if I'm wrong about those cell headers?

Let's pretend that I flubbed the analyis above, and that the attacker can read the command and circuitID for every cell on a link. All this allows the attacker to do is to demultiplex the circuits on the link, and better separate the traffic pattern flows that the link is multiplexing for different clients... but the attacker can't really  
use this info unless the attacker can correlate it with a flow somewhere else. This requires that the attacker be watching the same traffic at two points. But if the attacker can do that, the attacker can already (we assume) do a passive correlation attack and win.

### And what if I'm wrong entirely?

Now let's imagine that I am totally wrong, and TLS is completely broken, providing no confidentiality whatsoever? (Assume that it's still providing authenticity.)

Of course, this is a _really unlikely scenario_, but it's neat to speculate.

The attacker can remove at most one layer of encryption from RELAY cells in this case, because every hop of a circuit (except sometimes the first) is created with a one-way-authenticated Diffie-Hellman handshake. (The first hop may be created with a CREATE\_FAST handshake, which is not remotely secure against an attacker who can see the plaintext inside the TLS stream.) Anonymized RELAY traffic is encrypted in AES\_CTR mode with keys based on at least one CREATE handshake, so the attacker can't beat it. Non-anonymized RELAY traffic (that is, tunneled directory connections) don't contain sensitive requests or information.

So if the attacker can use this attack to completely decrypt TLS at a single hop on a Tor circuit, they still don't win. (All they can do is demultiplex circuits, about which see above.) And for them to do this attack at multiple points on the circuit, they would have to observe those points, in which case they're already winning according to our threat model.

### More challenges for the attacker

It's actually even a little harder to do this attack against Tor than I've suggested.

First, consider bandwidth-shaping: If a node or a link is near its bandwidth limit, it will split cells in order to stay under that limit.

Also, on a busy node, you can't really send a cell and expect it to get decrypted and put into the next output record on a given link: there are likely to be other circuits queueing other cells for that link, and by the time your cell is sent, it's likely that they'll have sent stuff too. You can get increased priority by making a very quiet  
circuit, though.

Finally, I don't actually think it's possible to cause chosen plaintext to appear on a client->server link.

### Recommendations

We dodged an interesting bullet on this one: part of it was luck, and part of it was a redundant protocol design. Nevertheless, let's "close the barn doors," even though the horse is still tied up, chained down, and probably sedated too.

First, as soon as OpenSSL 1.0.1 is out and stable, we should strongly suggest that people move to it. (It provides TLS 1.1.) We should probably build all of our packages to use it. But sadly, we'll have to think about protocol fingerprinting issues there, in case nobody else jumps onto the TLS 1.1 bandwagon with us. :/

We should include recommended use of the OpenSSL empty-record trick in our spec as a requirement or a strong recommendation. I'll add a note to that effect.

In future designs of replacements for the current RELAY and CREATE format, we should see if there are ways to prevent them from being used for chosen plaintext injection. This might not be the last attack of its kind, after all.

Perhaps we should put an upper bound on the circuit priority algorithm if we haven't already, so that no circuit can achieve more than a given amount of priority for being quiet, and so that you can't reliably know that your cell will be sent next on a link. But that's pretty farfetched.

### And in closing

[longpost is loooooooong](http://www.google.com/search?q=longcat&hl=en&prmd=imvns&tbm=isch)

Thanks to everybody who followed along with me so far, thanks to Juliano and Thai for letting me read their paper ahead of time, and thanks to everybody who helped me write this up. And thanks especially to my lovely spouse for proofreading.

Now, it's a Friday evening, and if you'll excuse me, I think I'm going to go off the 'nets for a little while.

