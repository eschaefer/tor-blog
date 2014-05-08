---
layout: post
title: "Apple broke OpenSSL which breaks Tor on OS X"
permalink: apple-broke-openssl-which-breaks-tor-os-x
date: 01/27/2010
author: phobos
category: blog
tags: ["apple os x", "new packages", "no love from apple", "openssl", "static compilation"]
---

Apple OS X Security Update 2010-001 removes OpenSSL renegotation, [http://support.apple.com/kb/HT1222](http://support.apple.com/kb/HT1222 "http://support.apple.com/kb/HT1222"). We've filed a bug report with Apple on this issue. Their standard response so far is [http://support.apple.com/kb/HT4004](http://support.apple.com/kb/HT4004 "http://support.apple.com/kb/HT4004").

In the meanwhile, we have bug #1225 open, [https://bugs.torproject.org/flyspray/index.php?do=details&id=1225](https://bugs.torproject.org/flyspray/index.php?do=details&id=1225 "https://bugs.torproject.org/flyspray/index.php?do=details&id=1225"). Add yourself to the Notifications if you want updates as they happen. A fine explanation of why Tor is not affected by the TLS renegotiation bug can be found at [https://bugs.torproject.org/flyspray/index.php?do=details&id=1225&area=c...](https://bugs.torproject.org/flyspray/index.php?do=details&id=1225&area=comments#3804 "https://bugs.torproject.org/flyspray/index.php?do=details&id=1225&area=comments#3804")

Packages for testing are available at:  
 [https://www.torproject.org/dist/testing/](https://www.torproject.org/dist/testing/ "https://www.torproject.org/dist/testing/")

**READ THIS FINE PRINT** :

1. These will only work on OSX 10.5 and 10.6 (both i386 and powerpc). Tor fails to compile when using the 10.4 libraries and static openssl.
2. Tor-0.2.2.8-alpha-i386-Bundle.dmg is compiled to replace the tor  
binaries in /Applications/Vidalia.app/Contents/MacOS only. If your tor  
is located elsewhere, compile your own for now.
3. let us know if they work for you. My testing systems show it works  
for me. Update  
 [https://bugs.torproject.org/flyspray/index.php?do=details&id=1225](https://bugs.torproject.org/flyspray/index.php?do=details&id=1225 "https://bugs.torproject.org/flyspray/index.php?do=details&id=1225") if it  
doesn't work or you have other issues with these testing packages.

I'm still working on os x 10.4 packages.

