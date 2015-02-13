---
layout: post
title: "Say hi to the new GetTor"
permalink: say-hi-new-gettor
date: 2014-11-26 12:22:42
author: ilv
category: blog
status: open
tags: ["censorship", "circumvention", "gettor", "gsoc", "gsoc14", "revamp", "torbrowser", "torproject websites"]
---

Hello people. It's been a while since Google Summer of Code 2014 ended, but I wanted to give you a brief review of the work done on GetTor.  
   
  
 **What is GetTor?**

GetTor is a program that serves Tor Browser over email. In the past, people would make requests by sending emails to GetTor, which would send back Tor Browser as email attachments. In **highly censored** countries (and places) where the Tor Project website is blocked, GetTor would be a convenient way for people to get access to Tor Browser.

There were lots of nice features incorporated in GetTor, such as specifying the operating system and language for the package wanted, or sending delay messages to let people know the package was on its way. But Tor Browser started to get larger in size (over 25 MB), to the point where it wasn't longer possible to send it via most email providers.  
   
  
 **Revamp**

It wasn't long until a solution for this problem came up. The idea consisted on uploading Tor Browser to the cloud (Dropbox) and when someone asked for it via GetTor, a reply with the links for download was sent. This worked quite well, but the fix was far from being complete and at that point the whole GetTor was in need of some love to get back to its shiny days.  
   
  
 **Google Summer of Code**

All of what I mentioned was listed on the Volunteer page of the Tor Project website, so when I got there looking for a project to work on for the Google Summer of Code, I immediatly considered it into my options, because of the *social impact* of GetTor as for the technical skills required. I was happy to learn that my proposal got accepted and I was one of the fourteen students selected to work on the Tor Project during the northern hemisphere summer (actually, it was winter here in Chile).

First, I started to work on the design, making sure that when I started to code, most of the ideas I would be implementing were carefully described and discussed. Of course, a lot of things did change over the coding period, some of them small stuff like how the links would be internally stored by GetTor, and some of them not so small, like changing one of the distribution modules.

Anyhow, I don't want to bore you with technical details here, but if you're interested, please read my [biweekly reports](https://trac.torproject.org/projects/tor/wiki/doc/gsoc) and check the [code repository](https://gitweb.torproject.org/gettor.git/tree/?h=revamp).  
   
  
 **Outcome**

The coding period lasted a little more than three months, and I managed to pass both mid-term and final evaluations. But more importantly, the status of GetTor improved significantly during that time. I did a *full rewrite* of it, focusing on having clean and readable code, and on making it easy to add new distribution modules and cloud providers for storing Tor Browser. Two distribution modules were successfully finished: SMTP, for asking via email; and XMPP, for asking via Jabber (you know, chat style).

Even though the new GetTor is able to manage requests in multiple locales, for now the SMTP module has been deployed with support for English requests only; other locales and modules will eventually/gradually be supported. We will let you know when that happens (*soon* we hope!).

Almost all of the testing and other minor fixes were done after the Google Summer of Code ended, and this is because I explicitly mentioned to my mentors that I have the intention to keep working on it and to continue as the lead developer if needed. It's not just for the work I did, but more importantly for the possibility of *helping other people*, specially those that have the bad fortune to live under regimes and/or organizations which think they can impose control on the information you can access, spy on what you do and chase you for what you think. If I have the chance to help avoiding this dystopia, as little as I can, I would certainly do whatever is in my hands, and I invite you to do the same.  
   
  
 **Great, but how do I use it?**

You can reach GetTor by sending emails to **gettor@torproject.org**. To ask for Tor Browser, you just have to send an email with the word **windows** in the body to get it for Windows, **osx** to get it for Mac OSX, or **linux** to get it for Linux. The options are case insentitive, so it doesn't matter if you send *Linux*, or *linux*, or *LiNuX*, as long as it describes one of the options mentioned before; if you send anything different from that, you will receive a help message with detailed instructions on how to interact with it. Once you ask for Tor Browser, GetTor will reply to you with Dropbox links to download the required package for your architecture (32/64 bit) and operating system, along with some extra information to help you verify the integrity of the downloaded files. Please note that you can reach GetTor from **any** email address: gmail, yahoo, hotmail, riseup, etc. The only restriction is that you can do a maximum of three requests in a row, after that you'll have to wait 20 minutes to reach GetTor again. You can find out more about its purpose and how it works [here](https://www.torproject.org/projects/gettor.html).  
   
  
 **Collaborate**

The main way to collaborate is to use GetTor and provide **feedback**! Please tell us what you like, what you don't like, what works smoothly and what doesn't work or could work better; after all, GetTor is here for **you**, so you should tell us what we need to do :) For this, please open a ticket on the [trac system](https://trac.torproject.org/projects/tor) under the GetTor component. You can file anything from usability suggestions/bugs to new development ideas.

On the other hand, I've read lots of people who are interested to collaborate with the Tor Project and they just don't know where to start or they are looking for something easy to collaborate with. The code and work on GetTor is quite straightforward, so if you know some Python and have some free time that you feel you want to give to an awesome **open source** organization, check the [git repository](https://gitweb.torproject.org/gettor.git/tree/?h=revamp) and the [tickets](https://trac.torproject.org/projects/tor/query?status=accepted&status=assigned&status=needs_information&status=needs_review&status=needs_revision&status=new&status=reopened&component=GetTor&col=id&col=summary&col=component&col=status&col=type&col=priority&col=milestone&order=priority) and you might find something easy to start with. There are various ideas and things left to do in GetTor, so please join us!  
   
  
 **Other options**

It's important to note that there are a couple more options to obtain Tor Browser when you cannot access Tor Project's website. The first and easiest is to access the official mirrors: [EFF](https://tor.eff.org/projects/torbrowser.html.en) and [torservers.net](https://www.torservers.net/mirrors/torproject.org/projects/torbrowser.html.en). If those sites are blocked too, you can try using [Satori](https://github.com/glamrock/satori), an app for Google Chrome that distributes various circumvention tools in a difficult-to-block way, making it easy for users to check if the software has been tampered. If after all, you manage to get the Tor Browser but you are not able to reach the Tor network, you might want to use bridges or the pluggable transports. You can read more about that [here](https://blog.torproject.org/blog/ways-get-tor-browser-bundle), [here](https://bridges.torproject.org/) and [here](https://www.torproject.org/docs/pluggable-transports.html.en).

  
  
 **Thanks**

I want to end this blog post by thanking to the Tor Project organization in general for letting me be part of it during the summer and kindly answer any doubt that came up, and to *Sukhbir* and *Nima* in particular for their awesome job as mentors, I couldn't have done it without you, thanks a lot guys!  
   

