---
layout: post
title: "The Debian OpenSSL flaw: what does it mean for Tor clients?"
permalink: debian-openssl-flaw%3A-what-does-it-mean-tor-clients%3F
date: 2008-05-14
author: arma
category: blog
tags: ["openssl", "security advisory"]
---

There have been a lot of questions today about just what [the  
recent Debian OpenSSL](http://lists.debian.org/debian-security-announce/2008/msg00152.html) flaw means for Tor clients. Here's an attempt to  
explain it in a bit more detail. (Go read [the Tor security advisory](http://archives.seul.org/or/announce/May-2008/msg00000.html) before  
reading this post.)

First, let's look at the security/anonymity implications for users who  
aren't running on Debian, Ubuntu, or similar. These implications all  
stem from the fact that some of the Tor relays and v3 directory authorities  
have weak keys, so the Tor network isn't able to provide as much anonymity  
as we would like.

The biggest issue is that perhaps 300 Tor relays were running with  
weak keys and weak crypto, out of the roughly 1500-2000 total running  
relays. What can an attacker do from this? If you happen to pick three  
weak relays in a row for your circuit, then somebody watching your local  
network connection (or watching the first relay you pick) could break all  
the layers of Tor encryption and read the traffic as if they were watching  
it at the exit relay. (I don't want to say they could read the plaintext,  
because if you used end-to-end encryption like SSL they wouldn't be able  
to see inside of that -- unless of course the webserver you contact is  
running Debian and affected by this bug!) Because this attacker can read  
the traffic inside Tor, they would also break your anonymity: they know  
both you and the destination(s) you asked for.

Worse, this attack works against past traffic too: what if an attacker  
logged traffic over the past two years? As long as there's a single  
non-weak non-colluding Tor relay in your circuit, you're fine -- that  
relay will provide encryption that the attacker can't break, then or  
now. But if you ever picked a path that consisted entirely of relays  
with broken RNGs, and an attacker logged this traffic, then he can unwrap  
the traffic from his logs using the same approach as above.

(Somebody who knows a Tor relay's private key could also impersonate that  
relay. So he can do a man-in-the-middle attack, intercepting your traffic  
to the "real" Tor relay and handling it himself. But this wouldn't give  
him anything that he can't already do just by watching. Another attack would  
be to create a fake descriptor and upload that. But this wouldn't give him  
anything he can't do by starting his own relay and uploading a descriptor for it.)

This evening we've begun the process of making the directory authorities  
reject all uploaded descriptors that are signed using these keys, so  
we will effectively cut them out of the network. Peter Palfrader, our  
Tor debian package maintainer, has also put out a new deb package that  
will automatically discard the old relay keys when the relays upgrade,  
so they'll automatically generate new safe keys.

The next big issue is that three of the six v3 directory authorities  
were using weak keys for their directory votes and signatures. This  
issue doesn't affect Tor clients running the 0.1.2.x (stable) series,  
since those clients use the v2 directory system, none of whose keys  
(I think) are weak.

What can three v3 authorities do? If they could forge a new v3  
networkstatus consensus, they could trick users into using their own  
fabricated Tor network, which would totally ruin their anonymity. Worse,  
they could do this in a way that would be very hard to detect, by just  
giving out their forged consensus to a few target users and giving out  
the "real" consensus the rest of the time. But fortunately, Tor clients  
require a majority of signatures before they'll believe the consensus --  
and that's four of six. (Whew, that was close!)

Now, three v3 authorities can still influence the consensus a lot. As  
one example, they could pick their favorite relays (say, because they  
operate those relays, or because those are the ones that are easiest to  
monitor), and put in three votes claiming that all the other relays are  
unusable. The resulting consensus will then list only those relays as  
"Running", since no other relays got enough votes. Then we're back to  
the above scenario. But in this case at least one other v3 authority  
would need to participate in building the consensus, so this couldn't be  
a selective one-off attack. The whole consensus would appear different  
to everybody, and hopefully somebody would notice.

The 0.2.0.26-rc release resolves these concerns by replacing those  
three weak identity keys with new strong ones. Once you upgrade, your  
new Tor won't trust any of those old keys -- so if anybody tries the  
above attacks on you, your Tor won't buy it.

And the last issue that affects non-Debian users? If you use a hidden  
service that generated its ".onion" key on a weak system, then you can  
no longer be sure that you're actually talking to the original person  
who generated the key. That's because somebody else might have figured  
out the private key for that service, and started advertising it himself.  
(Ordinarily, hidden services guarantee that nobody can intercept and read  
or modify your communications with the service, because only the person  
on the other end knows the private key that generated the ".onion" name.)

Now, what about the effects on Tor clients that run Debian, Ubuntu,  
or the like? Well, first they're affected by all the above attacks. And  
on top of that, any encryption they do can be considered to have no real  
effect. So for example if an attacker can observe your traffic either  
locally or at the first relay, he can see right through it all.

Similarly, if anybody has logs of traffic coming out of a Debian or Ubuntu  
Tor client, they can strip it of its encryption, and thus retroactively  
break the anonymity.

And lastly, don't forget there are plenty of other issues that this  
OpenSSL bug causes that are unrelated to Tor. As a simple example, if your  
bank generated its SSL cert on Debian or Ubuntu, then your SSL connection  
to your bank (likely including your password) is readable. Or if you ever  
tried to ssh into (or out of) an affected system, you have a problem. I  
imagine some broader lists of examples will start appearing soon.

