---
layout: post
title: "Summer of Torbutton"
permalink: summer-torbutton
date: 09/16/2009
author: koryk
category: blog
tags: ["gsoc torbutton"]
---

This summer I have been working on new feature for the Torbutton Firefox extension with Mike Perry as my mentor. The Tor Project volunteer page describes this project as requiring a high skill and effort level. Initially, I was confident in the effort that I was capable of putting forth, however I was doubtful of my skill level. My knowledge of XUL (an xml based markup language for the Mozilla Framework) and Javascript was a medium at best. Knowing that I was going to have to spend a good amount of time becoming adept with these languages, I took on writing three new features for Torbutton.

The first feature is handling tor:// and tors:// urls. I implemented these protocols to be handled by Torbutton, and will be opened in your Tor connection. If you do not have Tor enabled, you will be prompted to enable it. In addition, I added options in any link’s context menu for copying Tor URLs and opening them in a new window or tab.

The next feature I implemented was a referrer spoofer. The ‘referer’ http header field allows your browser to specify the address of the webpage of the resource which links to it. By checking the referrer, a new page can see where the request came from. Referrers leak information and reduce a user’s anonymity set. My feature intercepts the header and rewrites it. There are options to: leave the referrer blank, make the domain the referrer, make the root folder of the page the referrer, or a custom referrer.

The last feature I implemented was the Cookie Protecter. When enabled, the Cookie Protector allows a user to choose which cookies are saved/deleted on Tor toggle. The Cookie Protector is a dialog that shows all of your current cookies. A user can then delete cookies and choose ones to be protected upon toggle. The user can also specify whether new cookies are automatically protected or not. When Torbutton is toggled, the protected cookies get jarred up and saved for when the user toggles Torbutton again.

These features are almost ready to be released. There will be a pre-release version that will be out soon, I will notify or-talk when this is ready – so that it can be tested before release. In particular, I am looking for possible security vulnerabilities in my features. The tor/tors protocol is currently a source of vulnerability, because it can be called from many different places in the browser, and could be used to correlate a user’s Tor identity with his/her non-Tor identity. Therefore I want to make sure that it can only be called from a few parts on the page.

I plan on making sure that my features are robust and secure before releasing them, and expect that to be done by the next release of Torbutton. In addition, I plan on continuing to contribute to the Tor Project. I enjoyed my Summer of Code, and now I am looking forward to contributing to Tor.

