---
layout: post
title: "Tor on Android"
permalink: tor-android
date: 2010-03-04
author: ioerror
category: blog
tags: ["android mobile phone linux"]
---

The Tor Project has been working very closely with [Nathan Freitas](http://openideals.com/) and [The Guardian Project](http://openideals.com/guardian/) to create an Android release. This is an early beta release and is not yet suitable for high security needs. The Android web browser is not protected by Torbutton and we have not yet developed an anonymous browser on the Android platform. Please be cautious with this release, it's probably pretty fragile and it's certainly not ready for serious use.

We've codenamed the Tor on Android project Orbot; Orbot is a single Android package that provides a new Tor controller, Privoxy as our trusty little HTTP proxy, libevent, and Tor itself. This Android package is using the C reference implementation of Tor. Orbot should be orders of magnitude safer than other Tor implementations on Android and it's our official release. Everything you'll need for using Tor is in the package. :-)

We now have [an Android webpage](https://www.torproject.org/docs/android.html) that discusses the Orbot Android package in some detail.

Orbot has some commonly used features such as support for bridges. It also has advanced features such as per application Torification on modified devices (commonly called 'rooted' phones). It has been tested on Android 1.5, 1.6, 2.0, 2.1 and on non-standard customized builds of Android. We think we've ironed out most of the kinks but we're looking for some community feedback from devices in the wild. We'd especially like to hear about the UI and what applications you commonly use with Tor.

When Orbot is successfully installed and running, it should provide a few standard interfaces to interface with the Tor network. Privoxy listens on 127.0.0.1:8118 - it's chained to the standard Tor SOCKS proxy on 127.0.0.1:9050. In addition, we have a DNSPort on port 5400. The DNSPort is most commonly used by the automagical per application Torification. These ports may change in the future; if they conflict with other common and popular applications, we'd like to hear about it.

Our official builds are available from our website. As per our usual style of package releases, we're releasing [the .apk package](https://www.torproject.org/dist/android/0.2.2.9-alpha-orbot-0.0.2.apk) with [gpg signatures](https://www.torproject.org/dist/android/0.2.2.9-alpha-orbot-0.0.2.apk.asc).

If you'd simply like the latest Android package, please visit this url:  
 [http://www.torproject.org/dist/android/alpha-orbot-latest.apk](http://www.torproject.org/dist/android/alpha-orbot-latest.apk)

If you have the barcode scanner, you'll be able to directly load the  
latest package by scanning the following QR code:

![](https://blog.torproject.org/files/orbot-qr-code-latest.png)

We plan to release Orbot in the Google Market in the near future. The  
Orbot package you install from our website and the application in the  
Market should be identical. In addition to the GPG signature, the .apk  
files contain a digital signature. If you're feeling reasonably  
paranoid, it's probably a fine idea to download the .apk from our  
website, check the GPG signature, and then install the package on your  
device manually.

If you'd like to reproduce our builds from source, we've documented the  
build process in  
 [our subversion repository](https://svn.torproject.org/svn/projects/android/trunk/Orbot/BUILD).

If you'd like to read more about Orbot, we suggest you check out the  
source and start hacking around:  
svn co [https://svn.torproject.org/svn/projects/android/trunk/](https://svn.torproject.org/svn/projects/android/trunk/ "https://svn.torproject.org/svn/projects/android/trunk/") android/

<thead><tr>
<th>Attachment</th>
<th>Size</th> </tr></thead><tbody>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/orbot-qr-code-latest.png">orbot-qr-code-latest.png</a></td>
<td>426 bytes</td> </tr>
</tbody>

