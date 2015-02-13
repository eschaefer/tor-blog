---
layout: post
title: "Tails 0.9 Released"
permalink: tails-09-released
date: 2011-11-15 22:31:18
author: phobos
category: blog
status: closed
tags: ["anonymous operating system", "tails"]
---

The latest version of the anonymous operating system Tails is now available.

Notable user-visible changes include:

\#\# Tor  
 - Upgrade to 0.2.2.34. This fixes CVE-2011-2768 and CVE-2011-2769 which prompted for manual updates for users of Tails 0.8.1.  
 - Suppress Tor's warning about applications doing their own DNS lookups. Some users have reported concerns about these warnings, but it should be noted that they are completely harmless inside Tails as its system DNS resolver is Torified.

- Linux 3.0.0-6, which fixed a great number of bugs and security issues.

\#\# Iceweasel  
 - Upgrade to 3.5.16-11 ((fixes CVE-2011-3647, CVE-2011-3648, CVE-2011-3650).  
 - Torbutton: upgrade to 1.4.4.1-1, including support for the in-browser "New identity" feature.  
 - FireGPG: upgrade to 0.8-1+tails2. Users are notified that the FireGPG Text Editor is the only safe place for performing cryptographic operations, and these operations has been disabled in other places. Performing them outside of the editor opens up several severe attacks through JavaScript (e.g. leaking plaintext when decrypting, signing messages written by the attacker).  
 - Replace CS Lite with Cookie Monster for cookie management. Cookie Monster has an arguably nicer interface, is being actively maintained and is packaged in Debian.

\#\# Software  
 - Install MAT, the Metadata Anonymisation Toolkit. Its goal is to remove file metadata which otherwise could leak information about you in the documents and media files you publish. This is the result of a Tails developer's suggestion for GSoC 2011, although it ended up being mentored by The Tor Project.  
 - Upgrade WhisperBack to 1.5\~rc1. Users are guided how to send their bug reports through alternative channels upon errors sending them. This will make bug reporting easier when there's no network connection available.  
 - Upgrade TrueCrypt to 7.1.

\#\# Miscellaneous  
 - The date and time setting system was completely reworked. This should prevent time syncing issues that may prevent Tor from working properly, which some users have reported. The new system will not leave a fingerprintable network signature, like the old system did. Previously that signature could be used to identify who is using Tails (but not deanonymize them).  
 - Erase memory at shutdown: run many instances of the memory wiper. Due to architectural limitations of i386 a process cannot access all memory at the same time, and hence a single memory wipe instance cannot clear all memory.  
 - Saner keyboard layouts for Arabic and Russian.  
 - Use Plymouth text-only splash screen at boot time.

Plus the usual bunch of minor bug reports and improvements. The full [technical changelog](http://git.immerda.ch/?p=amnesia.git;a=blob_plain;f=debian/changelog;hb=refs/tags/0.9) is available.

The full version of this release is available at [http://tails.boum.org/news/version\_0.9/](http://tails.boum.org/news/version_0.9/ "http://tails.boum.org/news/version_0.9/").

Download from here, [http://tails.boum.org/download/index.en.html](http://tails.boum.org/download/index.en.html "http://tails.boum.org/download/index.en.html")
