---
layout: post
title: "Vidalia 0.2.12 is released"
permalink: vidalia-0212-released
date: 2011-04-12 21:13:44
author: erinn
category: blog
status: closed
tags: ["bug fixes", "improvements", "vidalia", "vidalia release"]
---

The new release of Vidalia 0.2.12 is out. We'd also like to congratulate Tomás Touceda on his first release and thank him for all his work and patience in getting this out!

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**0.2.12 10-Apr-2011**

-   Vidalia's SVN repository has been migrated to Git. All branches but  
     master have been archived for later review, since SVN trunk had changed  
     significantly; they should be reviewed later to determine whether  
     they can and should still be merged. All \\version \$Id\$ headers have been  
     removed since Git does not support \$Id\$.
-   As part of the move, Vidalia's Trac is now at:  
     [https://trac.torproject.org/](https://trac.torproject.org/ "https://trac.torproject.org/")  
     All Trac numbers in Vidalia 0.2.12 and beyond refer to the new Trac  
     entries. The old Trac is archived for posterity at:  
     [https://trac-vidalia.torproject.org/projects/vidalia](https://trac-vidalia.torproject.org/projects/vidalia "https://trac-vidalia.torproject.org/projects/vidalia")
-   Add support for Tor's ControlSocket as an alternative to ControlPort. It  
     can be used for Linux maintainers to build a better default interaction  
     between Tor and Vidalia by just setting the right permissions and file  
     owner on the socket file for the connection. Using ControlSocket means  
     you don't need to worry about authentication methods with ControlPort.  
     Resolves bug 2091.
-   Add a way to edit arbitrary torrc entries while Tor is running. Now  
     Vidalia users have more flexibility for configuring Tor. This change  
     doesn't replace editing torrc directly, because on some systems  
     (like Debian) Tor can't write to its torrc file. Resolves bug 2083.
-   Remove Vidalia's direct dependency on OpenSSL. This dependency had  
     caused Vidalia to fail to run on FreeBSD (due to a bug in the FreeBSD  
     ports collection) and Fedora 14 (due to an incompatibility between  
     OpenSSL and Fedora's SELinux configuration). Resolves bug 2287 and  
     2611.
-   Restore compatibility with Windows 2000. An update to the MiniUPnPc  
     library had introduced an unnecessary dependency on a system library  
     not included in Windows 2000. Fixes bug 2612.
-   Fix how the advanced message log window displays message updates when  
     messages are coming in too quickly, for example when you're listening  
     to debug-level messages from Tor. Fixes bug 2093.
-   Add a what's this? link to the bridge option to explain in a more verbose  
     fashion what being a bridge involves. Resolves bug 1995.
-   Prompt users to restart Tor after changing the path to torrc. Fixes bug  
     2086.
-   Disable the directory port configuration field when configuring a  
     bridge. A bridge does not need to operate a separate directory port,  
     and operating one can make a bridge easier to detect. Fixes bug 2431.
-   When Vidalia asks Tor for a bridge's usage history before anyone has  
     used it, correctly report that no clients have used the bridge recently.  
     Previously, it would incorrectly warn that it was unable to retrieve the  
     bridge's usage history. Fixes bug 2186.

