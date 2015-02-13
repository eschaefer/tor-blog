---
layout: post
title: "Training Journalists in Istanbul"
permalink: training-journalists-istanbul
date: 2013-02-04 10:12:56
author: Runa
category: blog
status: closed
tags: ["training", "trip report"]
---

After meeting with [SOCA in London](https://blog.torproject.org/blog/meeting-soca-london), I traveled to Istanbul to teach local and foreign journalists how to use Tor and Tails to keep themselves, their colleagues, and their sources safe online. I also met with the team behind [Zero Day](http://zerodaydoc.com/), a documentary about all things Internet security, to talk about Tor and the work that I do.

I met with foreign journalists on the first day and local journalists the day after. Around 30 people attended in total, and each training session lasted just over two hours. [My presentation](http://encrypted.cc/2013-01-28-istanbul.pdf) covered threats, how you can protect your communication, local data, and external data, as well as how to use the Tor Browser Bundle and Tails. I gave out USB sticks with the [Tor Browser Bundle](https://www.torproject.org/projects/torbrowser.html.en), [the short user manual](https://www.torproject.org/dist/manual/short-user-manual_en.xhtml), and the [CPJ Journalist Security Guide](https://cpj.org/reports/2012/04/journalist-security-guide.php). PC users were also given USB sticks with [Tails](https://tails.boum.org/).

Presentation
------------

The feedback has been really positive from everyone who attended, and I have been told that those who were unable to attend have been given the material I handed out. There are some things that can be improved, however:

-   Tor does not prevent somebody watching your Internet traffic from learning that you’re using Tor. In some cases, the fact that you are using Tor and encrypting emails/chat/drives can be a red flag. I am not sure how to best address this in a presentation, other than just say that yes, it can be a red flag.
-   We talked about a few different risks, such as having your phone tapped, your email hacked, and your home or hotel room broken into. Having solid examples and stories helps a lot.
-   I introduced a lot of new technology in a short amount of time. Those who are not familiar with technology such as [full disk encryption](http://en.wikipedia.org/wiki/Disk_encryption), [GPG](http://www.gnupg.org/), and [OTR](http://www.cypherpunks.ca/otr/), would benefit from a longer and more hands-on session.
-   The presentation included screenshots of encrypted email, encrypted chat, and the Tor Browser Bundle. Having a few videos that illustrate how it works, what the user sees, and what the new workflow is will make it easier to understand.
-   The presentation mentioned [Bitlocker](http://en.wikipedia.org/wiki/Bitlocker), [FileVault](http://en.wikipedia.org/wiki/FileVault), and [TrueCrypt](http://www.truecrypt.org/) for full disk encryption, but did not go into details. I told everyone how to enable FileVault in OS X, and I should add these step-by-step instructions to the presentation.
-   Tor was originally designed, implemented, and deployed as a project of the U.S. Naval Research Laboratory. We also receive funding via U.S. government organizations. I covered this briefly in my presentation, but could have spent a bit more time talking about the Tor Project, Inc and why we are qualified to talk about Internet security and online anonymity.

Tails
-----

I asked a few people to try out Tails and let me know if something was confusing, did not work, or could be improved:

-   Tails has [very limited support](https://tails.boum.org/support/known_issues/index.en.html#index1h2) for Apple hardware. 23 out of 30 attendees were Mac users. I tried booting Tails on my MacBook Air, but OS X was unable to find the USB stick.
-   I am used to the Tor Browser and was surprised to see that [check.torproject.org](https://check.torproject.org) was not the default home page.
-   Firefox will start automatically once you are connected to the Internet. Most users did not wait for the Tails website to load before entering another URL in the address bar. Users did not question if they were actually using Tor.
-   One user waited for the Tails website to load, saw the green download button and then asked if he needed to upgrade to a newer version. I wonder if there is a way to let users know which version they are currently using.
-   A few users seemed confused when Pidgin automatically connected to IRC. I wonder if it would be better to have that disabled by default, and instead take users through the process of setting up their own accounts.
-   One user tried the email client, skipped the part where you set up the mail servers, and tried to write an email. I wonder if there is a way to improve this, as most users expect the mail client to work just like the one they are used to in their normal operating system.
-   Tails uses a US keyboard layout by default. This can be confusing for anyone with a different keyboard layout. A few users mentioned that the tap-touchpad-to-click functionality did not work.
-   One user pointed out that there is no logout or shutdown option available when using Tails in Windows XP mode.
-   The shutdown process can look a bit scary for anyone who is not used to Linux, especially the part where it wipes the memory. A friendly splash-screen of some sort would be good.

Thanks to my wonderful hosts for providing me with a place to stay, great food, suggestions on what to see in Istanbul, and for organizing and hosting the training sessions.
