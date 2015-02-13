---
layout: post
title: "Advisory: remote DoS when using Tor with recent OpenSSL versions built with the \"no-ssl3\" option"
permalink: advisory-remote-dos-when-using-tor-recent-openssl-versions-built-no-ssl3-option
date: 2014-10-20 22:01:47
author: phoul
category: blog
status: closed
tags: ["little-t-tor", "poodle", "ssl", "sslv3", "tls", "tor"]
---

This is a copy of the message Nick Mathewson sent to the [tor-talk](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-talk) & [tor-relays](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-relays) mailing lists.

**Hello, relay operators!**

There's one important bugfix in the 0.2.5.9-rc release that relay operators should know about. If you have a version of OpenSSL that came out last week (like 1.0.1j, 1.0.0, ) and if your version of OpenSSL is built with the "no-ssl3" flag, then it's possible to crash your Tor relay remotely if you don't upgrade to 0.2.5.9-rc or to 0.2.4.25 (when that's out).

This appears to be an OpenSSL bug. The Tor releases in question contain a workaround for it.

To tell if your version of OpenSSL was built with 'no-ssl3': run:

> `openssl s_client -ssl3 -connect www.torproject.org:443`

If it gives you output beginning with something like:

> `CONNECTED(00000003) 140632971298688:error:14094410:SSL routines:SSL3_READ_BYTES:sslv3 alert handshake failure:s3_pkt.c:1257:SSL alert number 40 140632971298688:error:1409E0E5:SSL routines:SSL3_WRITE_BYTES:ssl handshake failure:s3_pkt.c:596: `

then you're fine and you don't need to upgrade Tor on your relay. But if it says something that starts with:

> `unknown option -ssl3 usage: s_client args `

then you need to upgrade Tor.

**Some questions and answers:**

Q: Does this affect clients?  
 A: No. Only relays.

Q: Does this affect me if I'm running a version of OpenSSL other than 1.0.1j, 1.0.0o, or 0.9.8zc?  
 A: No. Only those versions.

Q: Does this affect me if I'm running a version of OpenSSL configured without the "no-ssl3" option?  
 A: No. Only versions that were built with the "no-ssl3" option are affected.

Q: Does the OpenSSL team know?  
 A: Yes. Have a look at this [thread](http://marc.info/?l=openssl-dev&m=141357408522028&w=2). Also, before I saw that thread, I informed them the other day.

Q: Does this affect Tor packages?  
 A: I don't think that we shipped any packages where we used the "no-ssl3" flag to diable ssl3. So only if you're using OpenSSL from another source (say, your operating system) will you be affected.

Q: What can I do to remediate this problem?  
 A: You can upgrade to the most recent Tor, or you can use a version of OpenSSL built without the "no-ssl3" flag. Downgrading your OpenSSL is not recommended.

Q: What is the potential impact of this bug?  
 A: If a relay is affected by this bug, anybody can make the relay crash remotely. It does not enable any data leaks or remote code execution. Still, the ability to selectively disable relays might enable a sophisticated attacker to do some kinds of traffic analysis more efficiently. So, fix your relay if it's affected.

Q: Should we run in circles and freak out?  
 A: Not this time. We should just make sure we fix affected relays.

Q: Hey, Nick, you didn't explain this properly!  
 A: Please send a follow-up message that explains it better. :)
