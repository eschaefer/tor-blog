---
layout: post
title: "Experimental Defense for Website Traffic Fingerprinting"
permalink: blog/experimental-defense-website-traffic-fingerprinting
date: 2011-09-05
author: mikeperry
category: blog
tags: ["anonymity", "anonymity features", "attacks", "protecting users", "research", "surveillance", "traffic analysis"]
---

 **Updated 09/05/2011** : Add link to actual [implementation patch](https://gitweb.torproject.org/torbrowser.git/blob/maint-2.2:/src/current-patches/0006-Randomize-HTTP-pipeline-order-and-depth.patch) on gitweb

Website fingerprinting is the act of recognizing web traffic through surveillance despite the use of encryption or anonymizing software. The general idea is to leverage the fact that many web sites have specific fixed request patterns and response byte counts that are known beforehand. This information can be used to recognize your web traffic despite attempts at encryption or tunneling. Websites that have an abundance of static content and a fixed request structure tend to be vulnerable to this type of surveillance. Unfortunately, there is enough static content on most websites for this to be the case.

[Early work](http://guh.nu/projects/ta/safeweb/safeweb.pdf) was quick to determine that simple packet-based encryption schemes (such as wireless and/or VPN encryption) were insufficient to prevent recognition of traffic patterns created by popular websites in the encrypted stream. Later, a [small-scale study](http://research.microsoft.com/pubs/119060/WebAppSideChannel-final.pdf) determined that a lot of information could be extracted from HTTPS streams using these same approaches against specific websites.

Despite these early results, whenever researchers tried naively applying these techniques to Tor-like systems, they failed to come up with publishable results (meaning the attack did not work against Tor), due largely to the fixed 512 byte cell size, as well as the multiplexing of Tor client traffic over a single TLS connection.

However, last month, a group of researchers [succeeded in performing this attack](http://lorre.uni.lu/~andriy/papers/acmccs-wpes11-fingerprinting.pdf) where the others had failed. Their success hinged largely on their use of a simplified yet well-chosen feature set for training their classifiers. Where other researchers simply dumped packet sizes and timings into their classifiers and unsurprisingly got poor results against Tor traffic, this group extracted the time, quantity and direction of traffic, and discarded irrelevant control information such as TCP ACKs.

While the research methodology of the attack side of their work is particularly exemplary (certainly the most thorough study in website fingerprinting to date), their results are still likely insufficient to deploy against the network and expect to catch people engaging in single visits of forbidden websites. For such a use case, even their relatively low false positive rate is going to cause a lot of issues when deployed against large quantities of traffic. Concurrent use of multiple AJAX-enabled websites and/or other applications will also frustrate an attacker. Even without concurrent activity, their "open-world" experiment (the most realistic scenario for dragnet surveillance of Tor traffic) shows true positive accuracy of around 55%.

However, repeated observations over long periods of time are likely sufficient to develop certainty. It is also possible that extracting actual application data lengths from Tor TLS headers would add additional accuracy.

Hence, this is a rather nasty attack. It is basically a one-ended version of the age-old end-to-end correlation attack (where an adversary attempts to observe both the entrance to the network and the exits to correlate traffic flows). With the website fingerprinting attack, the adversary only needs to observe a single entry (a bridge, a guard node, or a regional firewall) of the network to begin gathering information about users who use that entry point.

However, because the attack is only one-ended, many defenses that would be useless against the full end-to-end attack can be considered. In the countermeasures section of their paper, the researchers point out that a Firefox addon that simply performs background HTTP requests concurrent to normal user activity was enough to foil their classifier.

We disagree with the background fetch approach because it seems that a slightly more sophisticated attack would train a separate classifier to recognize the background cover traffic and then subtract it before attempting to classify the remainder. In the face of this concern, it seems that the background request defense is not worth the additional network load until it can be further studied in detail.

Instead, we are deploying an [experimental defense](https://trac.torproject.org/projects/tor/ticket/3914) in [today's Tor Browser Bundle release](https://blog.torproject.org/blog/new-tor-browser-bundles-5) that is specifically designed to reduce the information available for feature extraction without adding overhead. The defense is to enable [HTTP pipelining](https://secure.wikimedia.org/wikipedia/en/wiki/HTTP_pipelining), and to randomize the pipeline size as well as the order of requests. The [source code to the implementation](https://gitweb.torproject.org/torbrowser.git/blob/maint-2.2:/src/current-patches/0006-Randomize-HTTP-pipeline-order-and-depth.patch) can be viewed on gitweb.

Since normal, non-randomized pipelining is still off by default to this day in Firefox, we are assuming that the published attack results are against serialized request/response behavior, which provides significantly more feature information to the attacker. In particular, we believe a randomized pipeline will eliminate or reduce the utility of the 'Size Marker', 'Number Marker', 'Number of Packets', and 'Occurring Packet Sizes' features on sites that support pipelining, due to the batching of requests and responses of arbitrary sizes. More generally, the randomized pipeline should obscure the request vs response size and request ordering information available to the classifier.

Our hope is that the randomized pipeline defense will therefore increase the duration of observation required to establish certainty that a site is being visited, by lowering the true positive rate and/or raising the false positive rate beyond what the researchers observed.

We do not expect this defense to be foolproof. We create it as a prototype, and request that future research papers do not treat the defense as if it were the final solution against website fingerprinting of Tor traffic. In particular, not all websites support pipelining (in fact, an unknown number may deliberately disable it to reduce load), and even those that do will still leak the initial response size as well as the total response size to the attacker. Pipelining may also be disabled by malicious or simply misconfigured exits.

However, the defense could also be improved. We did not attempt to determine the optimal pipeline size or distribution, and are relying on the research community to tweak these parameters as they evaluate the defense.

We could also take more extreme measures, such as building pipelining support into Tor exit nodes. Perhaps better still, we could deploy an [HTTP to SPDY translation service at exits](https://gitweb.torproject.org/torspec.git/blob/HEAD:/proposals/ideas/xxx-using-spdy.txt). The more efficient request bundling of [SPDY](http://dev.chromium.org/spdy) would likely obscure request vs response size information yet further. However, as these translations are potentially fragile as well as labor-intensive to implement and deploy, we are unlikely to take these measures without further feedback from and study by the research community.

Alternatively, or perhaps additionally, defenses could be deployed at the [obfsproxy plugin layer](https://gitweb.torproject.org/obfsproxy.git/blob/HEAD:/doc/protocol-spec.txt). Defenses there would not help against an adversary at the bridge or guard node, but would help against regional firewalls.

We would love to hear feedback from the research community about these approaches, and look forward to hearing more results of future attack and defense work along these and other avenues.

