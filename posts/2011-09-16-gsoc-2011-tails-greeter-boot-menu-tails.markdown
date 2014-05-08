---
layout: post
title: "GSoC 2011: tails-greeter - boot menu for TAILS"
permalink: gsoc-2011-tails-greeter-boot-menu-tails
date: 09/16/2011
author: max
category: blog
tags: ["anonymous operating systems", "gsoc 2011", "tails"]
---

This is a guest post from our 2011 Google Summer of Code student, Max:

Throughout the summer I've been working on 'tails-greeter' ( [https://tails.boum.org/todo/TailsGreeter/](https://tails.boum.org/todo/TailsGreeter/ "https://tails.boum.org/todo/TailsGreeter/")) project for TAILS ( [https://tails.boum.org](https://tails.boum.org "https://tails.boum.org")) live-cd. Essentially it's an implementation of boot-menu ( [https://tails.boum.org/todo/boot\_menu/](https://tails.boum.org/todo/boot_menu/ "https://tails.boum.org/todo/boot\_menu/")) in a form of GDM's greeter (that little program which asks your login and password before you see your desktop).

The initial proposal ( [http://www.google-melange.com/gsoc/proposal/review/google/gsoc2011/mx/20...](http://www.google-melange.com/gsoc/proposal/review/google/gsoc2011/mx/2001 "http://www.google-melange.com/gsoc/proposal/review/google/gsoc2011/mx/2001")) was adjusted as the project developed but major ideas remained the same: to implement an extensible boot menu which is easy to include into live-cd and maintain.

This posed several challenges: limit on dependencies I can use (has to be in Debian Squeeze or in backports), mastering Debian packaging, working with git (which sometimes does things in... non-obvious ways). Last but not least, tails-greeter is actually only 3rd consumer of GDM's greeter API besides GDM's own greeter and gdm-commmunity-greeter ( [https://launchpad.net/gdm-commmunity-greeter](https://launchpad.net/gdm-commmunity-greeter "https://launchpad.net/gdm-commmunity-greeter")). Because of that many things about the interaction with GDM are not very well documented.

Nevertheless, with the help from community, tails-greeter is ready to perform its duties: request language & layout information, set password for user and perform login. The project is rather easy to understand (581 source lines of code according to sloccount) so it can (and probably will) be extended in the future to request more information to adapt TAILS for user needs before login.

There are several things which could be improved, both user-visible (data representation) and internal (login procedure). I plan to stay in touch with the community to help to make tails-greeter ready for the inclusion into TAILS.

