---
layout: post
title: "Ways to get the Tor Browser Bundle"
permalink: ways-get-tor-browser-bundle
date: 2014-03-29 18:29:17
author: sukhbir
category: blog
status: closed
tags: ["censorship", "tbb", "torbrowser", "torproject websites"]
---

Below is a collection of resources that will help you get Tor up and running. We also discuss alternative approaches of downloading the Tor Browser Bundle and provide mirrors for all these resources in case [torproject.org](https://www.torproject.org/) is blocked.

To start with, please look at [Bundle Downloads](#1) and determine the best way for you to download the Tor Browser Bundle. After you have downloaded the bundle and before you install/extract it, you should also verify it to make sure the bundle you downloaded is genuine and has not been tampered with; this step is optional but recommended.

We have screencasts (video guides) that will help you with the installation and verification process on Windows, Linux and OS X.

**Windows**  
 [TBBTraining-DownloadAndVerify-Windows.mp4](https://media.torproject.org/video/TBBTraining/TBBTraining-DownloadAndVerify-Windows.mp4)

Mirror:  
 [torservers.net](https://www.torservers.net/mirrors/media.torproject.org/video/TBBTraining/TBBTraining-DownloadAndVerify-Windows.mp4)

**Linux**  
 [TBBTraining-DownloadAndVerify-Linux.mp4](https://media.torproject.org/video/TBBTraining/TBBTraining-DownloadAndVerify-Linux.mp4)

Mirror:  
 [torservers.net](https://www.torservers.net/mirrors/media.torproject.org/video/TBBTraining/TBBTraining-DownloadAndVerify-Linux.mp4)

**OS X**  
 [TBBTraining-DownloadAndVerify-MacOS.mp4](https://media.torproject.org/video/TBBTraining/TBBTraining-DownloadAndVerify-MacOS.mp4)

Mirror:  
 [torservers.net](https://www.torservers.net/mirrors/media.torproject.org/video/TBBTraining/TBBTraining-DownloadAndVerify-MacOS.mp4)

**Text guide for signature verification**  
 [https://www.torproject.org/docs/verifying-signatures.html.en](https://www.torproject.org/docs/verifying-signatures.html.en "https://www.torproject.org/docs/verifying-signatures.html.en")

Mirrors:  
 [EFF](https://s.eff.org/tor-mirror/docs/verifying-signatures.html.en)  
 [torservers.net](https://www.torservers.net/mirrors/torproject.org/docs/verifying-signatures.html.en)

Tor Browser Bundle Downloads
----------------------------

### torproject.org

[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en "https://www.torproject.org/projects/torbrowser.html.en")

Mirrors:  
 [EFF](https://s.eff.org/tor-mirror/projects/torbrowser.html.en)  
 [torservers.net](https://www.torservers.net/mirrors/torproject.org/projects/torbrowser.html.en)

### GetTor

GetTor is a program for serving the Tor Browser Bundle through email. This is particulary useful if you cannot access torproject.org or any other mirrors.

To request a bundle from GetTor, send a blank email to [gettor@torproject.org](mailto:gettor@torproject.org). GetTor will then respond with links to the Tor Browser Bundle for all platforms.

Note: GetTor was earlier restricted to requests from Gmail and Yahoo!. This is no longer the case and you can request for bundles from **any** email address, including Outlook.

Bridges
=======

If you are unable to reach the Tor network after installation (Tor Launcher starts, however the green progress bar stops), you need to use bridges.

### Acquiring Bridges

One way to find public bridge addresses is to send an email (from a Gmail or a Yahoo! address) to [bridges@bridges.torproject.org](mailto:bridges@bridges.torproject.org) with the line 'get bridges' by itself in the body of the mail.

You can also acquire bridges by visiting [https://bridges.torproject.org/](https://bridges.torproject.org/ "https://bridges.torproject.org/"). If you see that this page is offline, please wait for a few minutes and try again.

### Bridge Usage

1. Launch the Tor Browser Bundle  
 2. Click "Configure"  
 3. Click "Next" until you reach a page that reads "If this computer's Internet connection is censored, you will need to obtain and use bridge relays"  
 4. Enter the bridges you received from one of the methods above into the text box  
 5. Click "Connect"

Pluggable Transports
====================

If you find that using standard bridges fails for you, you can try using the 3.6-beta-1 bundle located on the same downloads page listed above. These bundles included integrated pluggable transport support, and are useful in areas where standard bridges are blocked.

To activate pluggable transports in the 3.6-beta-1 bundle, follow the bridge directions above, however simply select "obfs3" or "fte" when you reach the bridge configuration page (instead of entering bridge addresses yourself).

Support
=======

Still need help? If you have any questions, trouble connecting to Tor network, or need to talk to a human, please contact our support team at:

> [help@rt.torproject.org](mailto:help@rt.torproject.org) for English  
>  [help-ar@rt.torproject.org](mailto:help-ar@rt.torproject.org) for Arabic  
>  [help-es@rt.torproject.org](mailto:help-es@rt.torproject.org) for Spanish  
>  [help-fa@rt.torproject.org](mailto:help-fa@rt.torproject.org) for Farsi  
>  [help-fr@rt.torproject.org](mailto:help-fr@rt.torproject.org) for French  
>  [help-zh@rt.torproject.org](mailto:help-zh@rt.torproject.org) for Mandarin

  

* * * * *

Written in collaboration with Colin Childs. Screencasts by Sherief Alaa.
