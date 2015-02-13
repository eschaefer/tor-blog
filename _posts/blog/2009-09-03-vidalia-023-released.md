---
layout: post
title: "Vidalia 0.2.3 released"
permalink: vidalia-023-released
date: 2009-09-03 08:48:53
author: phobos
category: blog
status: closed
tags: ["drag and drop OS X install", "msi installer", "updated packages", "vidalia bundle"]
---

On August 27th, we released Vidalia 0.2.3. This fixes some more bugs with "Who has used by bridge" functionality and switches to Qt signals for event handling.

The updated Vidalia packages can be found at [https://www.torproject.org/vidalia](https://www.torproject.org/vidalia "https://www.torproject.org/vidalia")

The changes are: [**read more »**](https://blog.torproject.org/blog/vidalia-023-released)

Create the data directory before trying to copy over the default  
 Vidalia configuration file from inside the application bundle on Mac  
 OS X. Affects only OS X drag-and-drop installer users without a  
 previous Vidalia installation.

Change all Tor event handling to use Qt's signals and slots mechanism  
 instead of custom QEvent subclasses.

Fix another bug that resulted in the "Who has used my bridge?" link  
 initially being visible when the user clicks "Setup Relaying" from  
 the control panel if they are running a non-bridge relay.  
 (Ticket \#509, reported by "vrapp")

Always hide the "Who has used my bridge?" link when Tor isn't running,  

