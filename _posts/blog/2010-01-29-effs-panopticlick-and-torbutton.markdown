---
layout: post
title: "EFF's Panopticlick and Torbutton"
permalink: effs-panopticlick-and-torbutton
date: 2010-01-29
author: mikeperry
category: blog
tags: ["EFF", "online anonymity", "panopticlick", "privacy", "tor", "torbutton"]
---

The EFF has recently released a [browser fingerprinting test suite](http://panopticlick.eff.org/) that they call [Panopticlick](http://panopticlick.eff.org/about.php). The idea is that in normal operation, your browser leaks a lot of information about its configuration which [can be used to uniquely fingerprint you](https://www.eff.org/deeplinks/2010/01/tracking-by-user-agent) independent of your cookies.

Because of how EFF's testing tool functions, it has created some confusion and concern among Tor users, so I wanted to make a few comments to try to clear things up.

First off, Torbutton has defended against [these and other types of attacks](https://www.torproject.org/torbutton/design/#attacks) since the 1.2.0 series began. We make the User Agent of all Torbutton users uniform, we block all plugins both to prevent proxy bypass conditions and to block subtler forms of plugin tracking, we round screen resolution down to 50 pixel multiples, we set the timezone to GMT, and we clear and disable DOM Storage.

In fact, based on [my display resolution calculations](https://www.torproject.org/torbutton/design/#id2530601), we should only be presenting just over 7 bits of information to fingerprint Tor users, and this is only in the form of window size, which for most users either changes from day to day, or is set to a common maximized display size.

Why then does EFF's page tend to tell Tor users that they are unique amongst the hundreds of thousands of users that have been fingerprinted so far? The answer has largely to do with selection bias. The majority of visitors to EFF's site are likely not Tor users. Thus Torbutton's protection mechanisms tend to make Tor users stand out as unique amongst the rest of the web. This is not as bad as it seems. Torbutton's protection mechanisms are only meant to make all Tor users look uniform amongst themselves, not to make them look like the rest of web users. After all, Tor users are already identifiable because they appear from [easily recognizable Tor exit node IP addresses](https://www.torproject.org/tordnsel/).

What's more is that these protections are of course not enabled while Tor is disabled. In fact, one of [Torbutton's design requirements](https://www.torproject.org/torbutton/design/#requirements) is to not provide any evidence that you are a Tor user during normal operation.

I'd like to commend the EFF for bringing these web fingerprinting details to the public eye in a way that I unfortunately was unable to do when I first developed protections for them.

However, I wish that they also included or at least referenced [url history disclosure information](http://whattheinternetknowsaboutyou.com/) with their tool. After all, if you have history enabled (and you haven't set Torbutton to block history reads during Non-Tor usage), each URL you visit adds [another bit](https://www.eff.org/deeplinks/2010/01/primer-information-theory-and-privacy) to the set that can be used to fingerprint you. Often bits that are extremely sensitive, such as which diseases and genetic conditions you have based on your [Wikipedia](http://en.wikipedia.org/wiki/Category:Diseases_and_disorders) or [Google Health](https://www.google.com/health/) url history. I am convinced that it is only a matter of time before the ad networks begin mining this data to provide targeted ads for over-the-counter and prescription medications and to sell this data to other marketing and insurance firms, if they don't do it already.

