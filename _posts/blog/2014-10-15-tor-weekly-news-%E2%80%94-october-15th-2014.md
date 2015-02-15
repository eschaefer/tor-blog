---
layout: post
title: "Tor Weekly News — October 15th, 2014"
permalink: tor-weekly-news-—-october-15th-2014
date: 2014-10-15 07:00:00
author: harmony
category: blog
comments: disabled
tags: ["tor weekly news"]
---

Welcome to the forty-first issue in 2014 of Tor Weekly News, the [weekly newsletter](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-news) that covers what’s happening in the Tor community.

Academic research into Tor: four recent studies
===============================================

Major contributions to the development and security of Tor are often made by academic researchers, either in a laboratory setting using network simulators like [Shadow](https://shadow.github.io/), or through measurement and analysis of the live network itself (taking care not to harm the security or anonymity of clients and services). Different aspects of Tor’s networking and security, from path selection to theoretical attacks, have been analysed in three recently-published studies.

Otto Huhta’s [MSc thesis](http://www0.cs.ucl.ac.uk/staff/G.Danezis/students/Huhta14-UCL-Msc.pdf) investigates the possibility that an adversary in control of a non-exit relay could link two or more Tor circuits back to the same client based on nothing more than timing information. As Otto [explained](https://lists.torproject.org/pipermail/tor-dev/2014-September/007517.html), “this is mainly the result of the fixed 10 minute circuit lifetime and the fact that the transition to using a new circuit is quite sharp.” With the help of a machine classifier, and the fact that any one client will build its circuits through a fixed set of entry guards, the study suggested that such an adversary “can focus only on circuits built through these specific nodes and quite efficiently determine if two circuits belong to the same user.” There is no suggestion that this knowledge alone poses a serious deanonymization risk to clients; however, wrote Otto, “our goal was not to ultimately break the anonymity of any real user but instead to expose a previously unknown threat so that it can be mitigated before anyone actually devises an attack around it.”

Steven Murdoch published a [paper](http://www.cl.cam.ac.uk/~sjm217/papers/#pub-el14optimising) on the optimization of Tor’s node selection probabilities showing, [in Steven’s words](https://lists.torproject.org/pipermail/tor-dev/2014-October/007601.html), “that what Tor used to do (distributing traffic to nodes in proportion to their contribution to network capacity) is not the best approach.” Prior to publication of the study, “Tor moved to actively measuring the network performance and manipulating the consensus weights in response to changes. This seems to have ended up with roughly the same outcome. […] However, the disadvantage is that it can only react slowly to changes in network characteristics.”

Sebastian Urbach [shared](https://lists.torproject.org/pipermail/tor-relays/2014-October/005434.html) a link to [“Defending Tor from Network Adversaries: A Case Study of Network Path Prediction”](http://arxiv.org/pdf/1410.1823v1.pdf), in which the researchers analyze the effect of network features like [autonomous systems](https://en.wikipedia.org/wiki/Autonomous_System_%28Internet%29) and [Internet exchanges](https://en.wikipedia.org/wiki/Internet_exchange_point) on the security of Tor’s path selection, finding that “AS and IX path prediction significantly overestimates the threat of vulnerability to such adversaries”, and that “the use of active path measurement, rather than AS path models” would be preferable “in further study of Tor vulnerability to AS- and IX-level adversaries and development of practical defenses.”

Meanwhile, Philipp Winter took to the [Tor blog](https://blog.torproject.org/blog/closer-look-great-firewall-china) to summarize some new findings concerning the the way in which the Chinese state Internet censorship system (the “Great Firewall of China”) acts upon blocked connections, like those trying to reach Tor, as detailed in a recent [project](http://www.cs.unm.edu/~royaen/gfw/) to which he contributed. Searching for spatial and temporal patterns in Chinese censorship activity, the researchers found that “many IP addresses inside the China Education and Research Network (CERNET) are able to connect” to Tor in certain instances, while the filtering of other networks — centrally conducted at the level of Internet exchanges — “seems to be quite effective despite occasional country-wide downtimes”.

Each of these studies is up for discussion on the [tor-dev mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/tor-dev), so feel free to join in there with questions and comments for the researchers!

Miscellaneous news
==================

Michael Rogers [submitted](https://lists.torproject.org/pipermail/tor-dev/2014-October/007590.html) patches against tor and jtorctl, making two improvements to the performance of mobile hidden services: one “avoids a problem where we’d try to build introduction circuits immediately, all the circuits would fail, and we’d wait for 5 minutes before trying again”, and the other “[adds] a command to the control protocol to purge any cached state relating to a specified hidden service”.

Karsten Loesing [published](https://lists.torproject.org/pipermail/tor-dev/2014-October/007605.html) a “non-functional” [mock-up](https://kloesing.github.io/metrics-2.0/) of a possible redesign for the Tor Metrics portal, with notes on design decisions: “Feedback much appreciated. This is the perfect time to consider your ideas.”

Jeremy Gillula analyzed data relating to Tor node churn found in Tor consensuses for September 2014, and [found](https://lists.torproject.org/pipermail/tor-talk/2014-October/035207.html) that “on average, 0.003% of nodes switch from being relay nodes to exit nodes in any given 1-hour period, and 0.002% switch from being exit nodes to relay nodes”.

[Noel Torres](https://lists.torproject.org/pipermail/tor-reports/2014-October/000674.html) and [Andrew Lewman](https://lists.torproject.org/pipermail/tor-reports/2014-October/000676.html) sent their status reports for September. Roger Dingledine also sent out the report for [SponsorF](https://lists.torproject.org/pipermail/tor-reports/2014-October/000675.html).

Greg Norcie [wondered](https://lists.torproject.org/pipermail/tor-talk/2014-October/035212.html) why the interval at which Tor switches to using a new circuit was set at ten minutes, and Nick Mathewson [responded](https://lists.torproject.org/pipermail/tor-talk/2014-October/035213.html) that after the original period of thirty seconds was found to be unworkable, the new number was selected in 2005 “more or less intuitively”. Paul Syverson [added](https://lists.torproject.org/pipermail/tor-talk/2014-October/035217.html) that the choice was “an informed one”, taken after “a bunch of discussions concerning the trade-offs between the overhead of the public-key operations of circuit building and the pseudonymous profiling occurring at an exit”.

Both Tor and Tails received their first [cinematic credits](https://twitter.com/postessive/status/520956478287777792) with the première of “[CITIZENFOUR](https://citizenfourfilm.com/)”, a documentary film concerning the recent disclosure of intelligence documents by Edward Snowden. Eagle-eyed viewers might spot a well-known hostname in the film’s [trailer](https://www.youtube.com/watch?v=XiGwAvd5mvM)…

WhonixQubes [reported](https://lists.torproject.org/pipermail/tor-talk/2014-October/035211.html) on progress in many areas of the Whonix+Qubes project, which as the name implies is a combination of the [Whonix](https://www.whonix.org/) and [Qubes](https://www.qubes-os.org/) operating systems. Among other things, the system now supports Whonix 9, a community forum has been set up, and greater upstream integration is being discussed.

News from Tor StackExchange
===========================

"What happens when Tor always chooses the same path?" [asks Mark](https://tor.stackexchange.com/q/3689/88) and wants to know which weaknesses this exposes. User194 believes that this would prevent a “predecessor attack” and make the system stronger, while Lisbeth writes: “This makes your entire traffic highly fingerprintable as compared to a standard random path. If your connections always used A, B, and C nodes, it is statistically unlikely that many other people are consistently using that same path, therefore it’s very easy to correlate your traffic to your originating IP.”

Muncher visited a [website](https://secure.sw.gs:419/aaw/publist/adblock.html) which asked to add HidServAuth into the torrc and wants to know [if it is safe to do so](https://tor.stackexchange.com/q/3226/88). Jeff recommended that this is safe because it doesn’t divulge anything about the identity of a user. Mirimir furthermore referred to a question where adrelanos [looks for documentation](https://tor.stackexchange.com/q/219/88).

* * * * *

This issue of Tor Weekly News has been assembled by Lunar, qbi, and Harmony.

Want to continue reading TWN? Please help us create this newsletter. We still need more volunteers to watch the Tor community and report important news. Please see the [project page](https://trac.torproject.org/projects/tor/wiki/TorWeeklyNews), write down your name and subscribe to the [team mailing list](https://lists.torproject.org/cgi-bin/mailman/listinfo/news-team) if you want to get involved!
