---
layout: post
title: "Some thoughts on the CRIME attack"
permalink: blog/some-thoughts-crime-attack
date: 2012-09-14
author: nickm
category: blog
tags: ["crime", "security", "tls"]
---

By this point, some people have started to ask me about the Rizzo and Duong's new [CRIME](http://www.ekoparty.org//2012/juliano-rizzo.php) attack on TLS.

The short version is the same as with [BEAST](https://blog.torproject.org/blog/tor-and-beast-ssl-attack) last year: Tor is not affected. TorBrowser is not affected. Other applications may be affected; please consult your app vendor.

Here's the longer version, in case you're more curious. This is going to assume a little technical background, but not too much.

**The attack** : CRIME exploits TLS compression to learn secret cookies. (Approximate description follows.) The attacker uses JavaScript (or some other means) to cause a client to make an encrypted, compressed request to a webserver. Part of that request (for example, the URL) is under the attacker's control. Part of that request (for example, the cookie) is secret. TLS does not hide the length of what it's transmitting[\*], so the attacker can learn the length of the compressed request. The length of the compressed request will depend on how much redundancy there is between the attacker-controlled data and the rest of the request (including the secret). By learning how much redundancy there was, the attacker can learn how many bytes of attacker-controlled information were shared with the secret, and thereby how many bytes.

You can imagine it as something like a sophisticated game of [Mastermind](http://en.wikipedia.org/wiki/Mastermind_(board_game)): the attacker gets to guess a cookie, and they learn something how much of the cookie they guessed right. With enough guesses, they can learn the cookie, which lets them impersonate the client to the server.

[\*] (Okay, not all TLS implementation reveal the exact length of what they're encrypting. If they're using CBC, they'll round up to the nearest 16 bytes. But that's still enough information about the compressed data's length for this attack to work.)

**Is Tor vulnerable?** Tor isn't vulnerable because Tor (mostly!) never compresses anything secret before encrypting it. Tor doesn't use TLS compression at all. The only compressed data in Tor are pieces of directory information; and nearly all directory information is public knowledge, and downloaded by all clients.

The only non-public pieces of directory information in Tor are bridge descriptors and hidden-service descriptors. But these are only transmitted compressed on their own, and never compressed along with something adversary-controlled.

**What about TorBrowser?** TorBrowser isn't affected by CRIME as it stands either: It has disabled SPDY, and it has never enabled TLS compression.

Other browsers are probably affected; please check your browser vendor for updates.

**So, what about the rest of the internet?**

If you write, maintain, or use an application that uses TLS compression, you should probably just turn off the TLS compression until you figure out whether it's safe for your application.

The CRIME attack exploits a few key properties of HTTPS (the encrypted web protocol that uses the TLS encryption protocol). These properties are:

- The TLS protocol doesn't hide the length of what it's encrypting. (It hides it not at all with stream ciphers, and not at all well with block ciphers.)
- TLS has an optional compression feature where data can be compressed before it's encrypted.
- The length of the compressed record depends on the value of what is being compressed. (This is inevitable with lossless compression.)
- The same secret is sent over and over.
- The attacker can make the client generate compressed requests that contain attacker-controlled data in the same stream with secret data.

So it doesn't look the internet is out of the woods yet here: I don't believe we've seen the end of the CRIME attack. Even when TLS compression is disabled, we'll still need to worry about other compression: HTTP transfer encodings, for example. If an HTTPS page contains both an a secret part (like an anti-XSS token) and an attacker-controlled part, that's possibly enough for the attack to succeed. I predict that we'll be finding vulnerabilities of this type for a while, in nearly anything complicated that uses compression.

So, what can be done for programs and protocols in general (not just HTTP)?

1. Don't use compression.
2. Never compress anything containing a secret.
3. Never compress secret data and attacker-controlled data in the same compression stream without flushing the compression state between the two.
4. Don't send the same secret over and over.

Option 1 won't please the engineers: bandwidth savings from compression are real.

I hear some advocacy for options 2 or 3, but they're pretty fiddly. They require programmers to do something that programmers have historically been pretty bad at: tagging all of the tainted or the sensitive data in their programs, without exception. I predict that among people who take this approach with complex programs or websites, it's going to be pretty common to miss at least one secret or at least one attacker-controlled data vector.

Option 4 is what I like most, but it's going to require more crypto and engineering. It's the 21st century, after all. Cookies are a stupid way to authenticate; we have had better authentication protocols for decades.

**Oh, and one more thing to worry about** : Predictable data compressed along with a secret can be pretty bad too. Suppose for example that there's a fine-grained timestamp that gets compressed over and over along with the same secret, and the attacker can view the length of each compresed stream, and make a good guess about the timestamp's value. This leaks some information about the secret to the attacker, and with enough measurements, is probably enough to attack some systems.

**In Summary** :

The CRIME attack is very clever indeed. I'm looking forward to seeing the authors' talk/code in full once they're public.

CRIME is very bad against HTTPS, and makes TLS compression also look risky. Make sure your browser is updated.

Tor is not affected. TorBrowser's HTTPS is not affected. TorBrowser doesn't do SPDY.

And despite what you're hearing, this is not a TLS-specific or HTTPS-specific attack. All compress-and-encrypt combinations could probably use some attention, and should probably be considered suspect until they can get evaluated. This is going to be hard, since you can't just look at the encryption layer: you need to look at the compressed data stream itself, to see whether it's going to compress the same secrets secrets together with attacker-controlled or attacker-known values over and over.

So, who wants to have a crack at X11-over-compressed-SSH? Anybody know any fun automated systems built on top of PGP?

And y'know, while you're looking for places that compress secrets, it's probably a good idea to think about timing side-channels from your compression too.

**Acknowledgements** : my thanks to Juliano for explaining the attack to me and helping me understand its ramifications. Lots of the analysis above is due to a conversation with him. Thanks also to Juliano and Thai for coming up with the attack. Thanks to Robert Ransom for feedback and corrections on the first draft of this post.

