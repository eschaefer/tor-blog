---
layout: post
title: "Activists in Iran and Syria targeted with malicious computer software"
permalink: blog/activists-iran-and-syria-targeted-malicious-computer-software
date: 2012-03-15
author: Runa
category: blog
tags: ["iran", "malware", "privacy", "security", "syria"]
---

In February 2012 we learned that activists in Iran and Syria were targeted with two different types of malicious computer software. We received a copy of each malware, and Jonathan Tomek from [ThreatGRID](http://threatgrid.com/) helped with the analysis.

**How you get infected**

The malicious software is spread as email attachments, and as files sent via Instant Messaging and Skype. The software looks like two completely harmless files; a Microsoft PowerPoint slide show and an image file. The malicious software will silently install itself on your computer when you open one of the files.

Malicious software, such as the two copies we analyzed, is normally designed to gather sensitive information and gain unauthorized access to a computer system. The seemingly harmless PowerPoint slide show turned out to be a keylogger, while the image file was really a backdoor, providing the attacker with full access to the system.

Both the keylogger and the backdoor will transfer data to www(dot)meroo(dot)no-ip(dot)org, on port 778. This domain name used to point to a server at a government-owned telecommunications company in Syria, but was later updated to point to a [Linode](http://www.linode.com/) server in London, UK. [No-IP](http://www.no-ip.com/) have since pointed the domain name to an invalid IP address (0.0.0.0).

Most anti-virus software will be able to detect and remove both the [keylogger](https://www.virustotal.com/file/cef080a347339eb37e7efb33ed458044610946c5af404c5eae06309953111cf5/analysis/) and the [backdoor](https://www.virustotal.com/file/f64434efd243e1a099ed4dee008286caebfcf407b245f72c5ec59222995702f4/analysis/). You may try updating your anti-virus software, running it, and using it to remove the malware if anything pops up. However, the safest course of action is to re-install the operating system on your computer.

The EFF wrote a blog post called _ [How to Find and Protect Yourself Against the Pro-Syrian-Government Malware on Your Computer](https://www.eff.org/deeplinks/2012/03/how-find-syrian-government-malware-your-computer-and-remove-it)_. In the post, they recommend _"that you take steps to protect yourself from being infected by not running any software received through e-mail, not installing software at all except over HTTPS, and not installing software from unfamiliar sources even if recommended by a pop-up ad or a casual recommendation from a friend."_.

**PowerPoint slide show: keylogger**

When you first try to open the PowerPoint slide show, you will get a security warning asking if you really want to allow this file to run. The _Name_ field points to the following executable file: _C:\Program Files\Common Files\VMConvert32\wmccds.exe_

If you ignore the warning and click _Run_, a self-extracting rar file will install the malware (the _wmccds_ executable) onto your computer. The PowerPoint slide show will then open and you will see a series of images and some text in Farsi. The malware will not activate until you reboot your computer.

The first time you reboot, the malware will activate and start logging your keystrokes. If you are running Windows 7, you will see the same warning as mentioned above, and you have to click _Run_ before the malware is actually activated. Older versions of Windows will not display this warning when you reboot.

The malware will modify the Windows startup script to ensure that the keylogger is always running when you are using the computer. The keylogger will affect your whole system, and it will even send the contents of your clipboard to the attacker. The Tor Browser Bundle does not protect you if you have a keylogger on your system.

**Windows screen saver: backdoor**

The Windows screen saver contains a type of malware that is a bit more complex than the one described above. When you run the Windows screen saver, it will start an image program and show you a picture (we saw a picture of a rifle, but that is not always the case). Meanwhile, the malicious software installs a backdoor onto your computer and opens a connection to www(dot)meroo(dot)no-ip(dot)org, using port 778.

The backdoor (_1122333.exe_ in the _Documents and Settings_ folder), which is similar to the DarkComet Remote Administration Tool, allows the attacker to connect to your computer and do anything that he or she wants, including logging keystrokes and acting as the system administrator. The malware will modify the Windows startup script to ensure that the connection is always open.

