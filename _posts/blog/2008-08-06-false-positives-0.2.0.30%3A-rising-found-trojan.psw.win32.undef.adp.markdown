---
layout: post
title: "False Positives in 0.2.0.30:  RISING found Trojan.PSW.Win32.Undef.adp"
permalink: false-positives-0.2.0.30%3A-rising-found-trojan.psw.win32.undef.adp
date: 2008-08-06
author: phobos
category: blog
tags: ["false positives", "privoxy", "trojan", "vidalia", "virus", "windows bundles"]
---

I've noticed a [few comments](https://blog.torproject.org/blog/june-2008-progress-report#comment-154) about a Chinese anti-virus program, RISING, reporting that Vidalia.exe and Privoxy.exe are infected with Trojan.PSW.Win32.Undef.adp. In both cases, I suspect that RISING is reporting false positives. These executables as packaged and available on the Tor download page are not infected.

I've looked at the MD5 and SHA-1 sums of these programs as included in the Vidalia bundle and they match what the source packages produce as executables. The privoxy.exe included in the bundles is the exact same one as found at the [Sourceforge Privoxy Download Page](http://downloads.sourceforge.net/ijbswa/privoxy_setup_3_0_6.exe?modtime=1164015760&big_mirror=0).

The Vidalia.exe is the same as the one included in the [Vidalia Download Page](http://www.vidalia-project.net/dist/vidalia-0.1.7.exe).

Feel free to confirm this is true for you. Better yet, let us know if these individual packages (Vidalia.exe from Vidalia and Privoxy.exe from Sourceforge) also show up as infected.

