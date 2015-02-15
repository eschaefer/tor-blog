---
layout: post
title: "New SSLv3 attack found: Disable SSLv3 in TorBrowser"
permalink: new-sslv3-attack-found-disable-sslv3-torbrowser
date: 2014-10-14 21:16:03
author: nickm
category: blog
comments: closed
tags: ["poodle", "ssl", "sslv3", "tls", "torbrowser"]
---

Hi! It's a new month, so that means there's a new attack on TLS.

This time, the attack is that many clients, when they find a server that doesn't support TLS, will downgrade to the ancient SSLv3. And SSLv3 is subject to a new padding oracle attack.

There is a readable summary of the issue at [Adam Langley's blog](https://www.imperialviolet.org/2014/10/14/poodle.html); it links to other descriptions of the attack.

Tor itself is not affected: all released versions for a long time have shipped with TLSv1 enabled, and we have never had a fallback mechanism to SSLv3. Furthermore, Tor does not send the same secret encrypted in the same way in multiple connection attempts, so even if you could make Tor fall back to SSLv3, a padding oracle attack probably wouldn't help very much.

TorBrowser, on the other hand, is based on Firefox, and has the same protocol downgrade mechanisms as Firefox. I expect and hope the TorBrowser team will be  
 releasing a new version soon with SSLv3 disabled. But in the meantime, I think you can disable SSLv3 yourself by changing the value of the "security.tls.version.min" preference to "1". (The default value is "0".)

To do that:

1.  Enter "about:config" in the URL bar.
2.  Then you click "I'll be careful, I promise".
3.  Then enter "security.tls.version.min" in the preference "search"  
     field underneath the URL bar. (Not the search box next to the URL  
     bar.)
4.  You should see an entry that says "security.tls.version.min" under  
     "Preference Name". Double-click on it, then enter the value "1" and  
     click okay.

You should now see that the value of "security.tls.version.min" is set to one.

(Note that I am not a Firefox developer or a TorBrowser developer: if you're cautious, you might want to wait until one of them says something here before you try this workaround. On the other hand, if you believe me, you should probably do this in your regular Firefox as well.)

Obviously, this isn't a convenient way to do this; if you are uncertain of your ability to do so, waiting for an upgrade might be a good move. In the meantime, if you have serious security requirements and you cannot disable SSLv3, it might be a good idea to avoid using the Internet for a week or two while this all shakes out.

Best wishes to other residents of these interesting times.
