---
layout: post
title: "A Critique of Website Traffic Fingerprinting Attacks"
permalink: critique-website-traffic-fingerprinting-attacks
date: 2013-11-07 15:37:23
author: mikeperry
category: blog
status: closed
tags: ["machine learning", "research", "statistics", "traffic analysis"]
---

Website traffic fingerprinting is an attack where the adversary attempts to recognize the encrypted traffic patterns of specific web pages without using any other information. In the case of Tor, this attack would take place between the user and the Guard node, or at the Guard node itself.

There are two models under which these attacks are typically studied: The "closed world" scenario, and the "open world" scenario. In the "closed world" scenario, the only traffic patterns the classifier ever sees are for web pages that it has already been trained on, and it typically must successfully label all of them. This is meant to simulate situations where users only use Tor for viewing a small set of censored web pages and nothing else. The "open world" scenario is slightly more realistic in that it attempts to examine the ability of the adversary to recognize a few censored pages out of a much larger set of uncensored pages, some of which it has never seen before.

It is important to note that in both models, these papers are reporting results on their ability to classify individual **pages** and not overall websites, despite often using the terms website and webpage interchangeably.

The most comprehensive study of the statistical properties of this attack against Tor was done by Panchenko et al. In their "closed world" study, they evaluated their success rates of classifying 775 web pages. In their "open world" study, they classified a handful of censored pages in 5000 page subsets of 1,000,000 total web pages.

Since then, a series of smaller scale follow-on attack papers have claimed improved success rates since Panchenko's study, and in at least two instances these papers even claimed to completely invalidate any attempt at defense based only on partial results.

While there may have been some improvements in classifier accuracy in these papers over Panchenko, defenses were "broken" and dismissed primarily by taking a number of shortcuts that ignore basic properties of machine learning theory and statistics in order to enable their claims of success.

Despite these subsequent improvements in these attacks, we are still skeptical of the efficacy of this attack in a real world scenario, and believe that only minimal defenses will be needed to ensure the attack continues to be unusable in practice.

This post will be divided into the following areas: First, we will attempt to distill the adversary model used by this body of work, and describe the adversary's goals. Then, we will review the basic properties of machine learning theory and statistics that govern classifier accuracy and real-world performance. Next, we will make these properties concrete by briefly discussing additional real-world sources of hidden complexity in the website traffic fingerprinting problem domain. We will then specifically enumerate both the useful contributions and the shortcuts taken by various work to date. Finally, we will conclude with suggestions and areas for improvement in future work.

Pinning Down the Adversary Model
--------------------------------

Website traffic fingerprinting attack papers assume that an adversary is for some reason either unmotivated or unable to block Tor outright, but is instead very interested in detecting patterns of specific activity inside Tor-like traffic flows.

The exact motivation for this effort on behalf of the adversary is typically not specified, but there seem to be three possibilities, in order of increasing difficulty for the adversary:

1.  The adversary is interested in blocking specific censored webpage traffic patterns, while still leaving the rest of the Tor-like traffic unmolested (perhaps because Tor's packet obfuscation layer looks like something legitimate that the adversary wants to avoid blocking).
2.  The adversary is interested in identifying all of the users that visit a small, specific set of targeted pages.
3.  The adversary is interested in recognizing every single web page a user visits.

  
Unfortunately, it seems that machine learning complexity theory and basic statistics are heavily stacked against all three of these goals.

Theoretical Issues: Factors Affecting Classification Accuracy
-------------------------------------------------------------

Machine Learning theory tells us that the accuracy of a classifier is affected by four main factors: the size of the hypothesis space (ie the information-theoretic complexity of the classification categories), the accuracy of feature extraction and representation (the bias in the hypothesis space), the size of the instance space (the world size), and the number of training examples provided to the classifier.

Bounds have actually been established on the effect of each of these areas to the likelihood of achieving a given accuracy rate, and any good undergraduate course in Machine Learning will cover these topics in detail. For a concise review of these accuracy bounds, we recommend Chapters 5 and 7 of [Machine Learning by Tom Mitchell](http://www.amazon.com/Machine-Learning-Tom-M-Mitchell/dp/0070428077).

The brief summary is this: as the [number and/or complexity of classification categories](https://en.wikipedia.org/wiki/VC_dimension) increases while reliable feature information does not, the classifier eventually runs out of descriptive feature information, and either true positive accuracy goes down or the false positive rate goes up. This error is called the [bias in the hypothesis space](http://www.cs.washington.edu/education/courses/csep573/98sp/lectures/lecture8/sld050.htm). In fact, even for unbiased hypothesis spaces, the number of training examples required to achieve a reasonable error bound is [a function of](https://en.wikipedia.org/wiki/Probably_approximately_correct_learning#Equivalence) the number and complexity of the classification categories.

It turns out that the effects of all of these factors are actually observable in the papers that managed to study a sufficient world size.

First, for the same world size and classifier technique, every work that examined both the open and closed worlds reports much higher accuracy rates for the open world than for the closed world. This is due to the higher hypothesis space complexity involved in labeling every page in the closed world, as opposed to labeling only a very small subset of censored targets in the open world. This confirms the above machine learning theory, and tells us that that an adversary that is attempting to recognize every single web page in existence is going to have a very difficult time getting any accuracy, as compared to one who is classifying only a select interesting subset.

It is also clearly visible in [Panchenko's large-scale open world study](http://freehaven.net/anonbib/cache/wpes11-panchenko.pdf) that increasing the world size contributes to a slower, but still steady decline in open world accuracy in Figure 4 below. The effect of the hypothesis space complexity (increased number of pages to classify) on the open world can also be seen in the rising false positive rates of Figure 5 below (this rise may seem small, but in the next section we will show how even tiny increases in false positives are in fact devastating to the attack).

![](https://people.torproject.org/~mikeperry/images/Fig4.png) ![](https://people.torproject.org/~mikeperry/images/Fig5.png)

Every other attack paper since then has neglected to use world sizes large enough to observe these effects in sufficient detail, but again, machine learning theory tells us they are still there, just beyond the published data points.

Practical Issues: False Positives Matter. A Lot.
------------------------------------------------

Beyond classifier accuracy and the factors that affect it, the practical applicability of the website traffic fingerprinting attack is also affected by some basic statistical results. These statistics (which [have been examined](http://www.raid-symposium.org/raid99/PAPERS/Axelsson.pdf) in other computer security-related application domains of machine learning) show that false positives end up destroying the effectiveness of classification unless they are vanishingly small (much less than 10\^-6).

It actually turns out that false positives are especially damaging to this attack, perhaps even more so than most other application domains. In the website traffic fingerprinting attack, false positive results are a built-in property of the world: if one or more pages' traffic patterns are similar enough to a target page's pattern to trigger a false positive, these sets of pages will always be misclassified as the target page every time that traffic pattern is present. Unlike end-to-end timing correlation, the adversary does not get to benefit from information derived from repeated visits (except in narrow, contrived scenarios that we will address in our literature review below).

What's more is that this also means that small world sizes directly impact the false positive rate. As you increase the world size, the likelihood of including a page that matches a traffic stream of your target page also increases.

To demonstrate the damaging effects of false positives on the attack, we will now consider the effects of false positives on the adversary's two remaining feasible goals: flagging users who visit a specific controversial web page over Tor, and censoring only a subset of Tor-like traffic.

In the event where the adversary is attempting to recognize visits to highly sensitive material (such as a specific web page about a particular protest action) and is interested in gathering a list of suspects who visit the web page, it is easy to see that even with very high accuracy rates, the suspect list quickly grows without bound.

To see this, note that the probability of at least one false positive over N independent page loads is given by **1 - (1-fp)\^N**, where fp is the probability of a false positive.

Even with a false positive rate as low as 0.2% (which is typical for this literature, and again is also lower than reality due to small world sizes), after performing just N=100 different page loads, 18% of the userbase will be falsely accused of visiting targeted material at least once. After each user has performed N=1000 different page loads, 86.5% of that user base will have been falsely accused of visiting the target page at least once. In fact, many of these users will be falsely accused much more frequently than that (as per the [Binomial Distribution](https://en.wikipedia.org/wiki/Binomial_distribution#Probability_mass_function)).

If instead of trying to enumerate specific visitors, the adversary is trying to interfere with the traffic patterns of certain web pages, the accuracy value that matters is the Bayesian Detection Rate, which is the probability that a traffic pattern was actually due to a censored/target page visit given that the detector said it was recognized. This is written as **P(Censored|Classified)**.

Using Bayes Theorem, it is possible to convert from the true and false positive rates of **P(Classified|Censored)** and **P(Classified|\~Censored)** to the Bayesian Detection Rate of **P(Censored|Classified)** like so:

     P(Censored|Classified) =  P(Classified|Censored)*P(Censored) /   (P(Censored)*P(Classified|Censored) +     P(~Censored)*P(Classified|~Censored)) 

Under conditions of low censorship (0.1% -- such as when the Tor traffic successfully blends in with a large volume of innocuous Internet traffic, or when Tor is used for both censorship circumvention and general privacy), with a true positive rate of 0.6 and a false positive rate of 0.005, we have:

     P(Censored|Classified) = 0.6*.001/(.001*0.6+.999*.005) P(Censored|Classified) = 0.10 P(~Censored|Classified) = 1 - P(Censored|Classified) P(~Censored|Classified) = 0.90 

This means that when a traffic pattern is classified as a censored/target page, there is a 90% chance that the classifier is actually telling the adversary to interfere with an unrelated traffic stream, and only a 10% chance that the classifier was actually correct.

This phenomenon was [explored in detail](http://www.raid-symposium.org/raid99/PAPERS/Axelsson.pdf) in the Intrusion Detection System literature, and is the reason why anomaly and classification-based antivirus and IDS systems have failed to materialize in the marketplace (despite early success in academic literature).

Practical Issues: Multipliers of World Size are Common
------------------------------------------------------

Beyond the above issues, there are a number of additional sources of world size and complexity in the website traffic fingerprinting problem domain that are completely unaddressed by the literature.

Again, it is important to remember that despite the use of the word "website" in their titles, these attacks operate on classifying instances of traffic patterns created by single ***pages***, and not entire ***sites***. For some sites, there may be little difference between one page and another. For many sites, the difference between component pages is significant.

It is also important to note that the total number of pages on the web is actually quite larger than the number of items indexed by Google (which is quite a bit larger than even the 1,000,000 page crawl used by Panchenko). In particular, the effects of dynamically generated pages, unindexed pages, rapidly updated pages, interactive pages, and authenticated webapps have been neglected in these studies, and their various possible traffic patterns contribute a very large number of additional web traffic patterns to the world, especially when the different manners in which users interact with them are taken into account.

Beyond this, each page actually also has at least 8 different common traffic patterns consisting of the combination of the following common browser configurations: Cached vs non-cached; Javascript enabled vs disabled; adblocked vs non-adblocked. In each of these combinations, different component resources are loaded for a given page. In fact, the cached vs non-cached property is not just binary: arbitrary combinations of content elements on any given page may be cached by the browser from a previous visit to a related resource. What's more, in Tor Browser, either restarting the browser or using the "New Identity" button causes all of this caching state to be reset.

In addition, similarities between non-web and web traffic also complicate the problem domain. For just one example, it is likely that an open tab with a Twitter query in it generates similar traffic patterns to a Tor-enabled XMPP or IRC client.

All of these factors increase the complexity of the hypothesis space and the instance space, which as we demonstrated above, will necessarily reduce the accuracy of the attack in both theory and practice.

Literature Review: Andriy Panchenko et al
-----------------------------------------

Title: **[Website Fingerprinting in Onion Routing Based Anonymization Networks](http://freehaven.net/anonbib/cache/wpes11-panchenko.pdf)**

As mentioned previously, Panchenko's work (actually the first work to successfully apply website traffic fingerprinting to Tor) is still the most comprehensive study to date.

Here is a brief list of its strengths:

1.  The world sizes are huge.

    5000 page subsets of 1,000,000 pages may still have representational issues compared to the real world, but this is still the largest study to date.

2.  Careful feature extraction (hypothesis space construction).
    The reason why this work succeeded where earlier works failed is because rather than simply toss raw data into a machine learning algorithm, they were extremely careful with the representation of data for their classifiers. This likely enabled both the efficiency that allowed such a large world size, and reduced the bias in the hypothesis space that would otherwise lead to low accuracy and high false positives at such large world sizes.
3.  In the "open world", they varied the type of censored target sites to evaluate accuracy.

    Instead of merely picking the target pages that were easiest to classify (such as video sites), they varied the type of target pages and explored the effects on both true and false positive accuracy. None of the other literature to date has examined this effect in detail.

4.  They are careful to tune their classifiers to minimize false positives.

    Modern classifiers typically allow you to trade off between false positives and false negatives. Given how deeply false positives impact the adversary's goals, this is very important.

5.  They demonstrate knowledge of all of the factors involved in PAC theory and practical classifier accuracy.
    All of the other papers to date simply omit one or more of the following: data on feature extraction, the contribution of individual features to accuracy, the number of training examples, the effect of target size on both the open and closed world, the effect of target page types on accuracy, and the effects of world size on accuracy.

While impressive, it does miss a few details:

1.  It fails to acknowledge that false positives are a property of specific sites.

    In reality, nearly every false positive they experienced in a given subset of 5000 pages is a false positive that will likely appear in a classifier that is run against the entire 1,000,000 page dataset. They probably should have tallied the total false positives over multiple runs for this reason, and analyzed their properties.

2.  It still fails to provide a realistic adversary model in order to justify claims that the attack actually accomplishes what the adversary wants.

Literature Review: Kevin P. Dyer et al
--------------------------------------

Title: **[Peek-a-Boo, I Still See You: Why Efficient Traffic Analysis Countermeasures Fail](http://freehaven.net/anonbib/cache/oakland2012-peekaboo.pdf)**

This work attempts to evaluate several defenses against the website traffic fingerprinting attack, and also attempts to evaluate an "idealized best case" defense called BuFLO.

On the positive side, the work makes the following contributions:

1.  It creates an ideal high-overhead tunable defense (BuFLO) that can be compared against other practical defenses.
2.  It is quite clear about its definitions of accuracy and experimental setup.
3.  [Source code is provided](https://kpdyer.com/publications/oakland2012-peekaboo-0.1.tar.gz)!

  
However, the work had the following rather serious shortcomings:

1.  Close world only, and a very small closed world at that.

    This is the single largest issue with this attack paper. You cannot claim that all defenses are broken forever if a classifier is only able to somewhat correctly classify 500 pages or less (and only 128 pages in their defense studies!), even in a closed world.

2.  Exaggerated claims give no credit to (or detailed analysis of) relative strengths of defenses.

    Despite the fact that their exaggerated claims are made possible due to their small world size of only 128 pages, the authors do not acknowledge that some light weight defenses **did** in fact do far better than others in their experiments. In light of the fact that their world size was woefully small, the authors work would have been substantially more humble in terms of acknowledging the effectiveness of some defenses, and should have spent more time focusing on why some defenses did better against some classifiers, what the overhead costs were, and what classifier features were most impacted by each defense.

3.  It does not give statistics on which sites suffer high rates of misclassification.

    Even in their small world size, is it likely that they stumbled upon a few pages that ended up consistently misclassified. Which were these? How often does that happen out of arbitrary 128 page subsets?

4.  Features are evaluated, but not in terms of their contribution to accuracy.
    There are several standard ways of evaluating the contribution of features to accuracy under various conditions. The authors appeared to employ none of them.

Literature Review: Xiang Cai et al
----------------------------------

Title: **[Touching from a Distance: Website Fingerprinting Attacks and Defenses](http://freehaven.net/anonbib/cache/ccs2012-fingerprinting.pdf)**

This work also attempts to evaluate several additional defenses against the website traffic fingerprinting attack, proposes a Hidden Markov Model extension of the attack to classify web sites in addition to pages, and also attempts to evaluate the BuFLO defense from the "Peek-a-boo" paper, as well as a lower-overhead variant.

On the positive side, the following useful contributions were made:

1.  A low-resource "congestion sensitive" version of Dyer et al's BuFLO defense is presented.

    This defense is also tunable, and deserves a more fair evaluation than was given to it by its own creators. Hopefully they will follow up on it.

2.  An automatic feature extraction mechanism is built in to the classifier.
    The work uses an edit distance algorithm to automatically extract features (pairwise transposition, insertion, deletions and substitutions) rather than manual specification and extraction.

However, this paper also shares many of the Peek-a-boo paper's shortcomings above, and has some of its own.

1.  Minimal edit distance classifiers are ideally suited for a closed world.

    The DLSVM classifier finds the shortest edit distance between a single testing instance and the model instances from training. This is a useful heuristic for a closed world, where you know that your training instance will match \*something\* from your model, but how well does it fare when you have to tune a cutoff to decide when a given traffic stream's edit distance is too large to be among your censored target pages? It seems likely that it is still better than Panchenko's classifier in the open world, but this has not been proven conclusively, especially since the effect of site uniqueness on the classifier was not examined.

2.  Glosses over effects of defenses on edit distance components.

    Even though edit distance classifiers do not have explicit features, they still have implicit ones. It would be useful to study the effect of low-resource defenses on the most information-heavy components of the edit distances. Or better: to analyze how to tailor their BuFLO variant to target these components in an optimal way.

3.  Defenses were not given a fair analysis.

    In the specific case of both Tor Browser's pipeline defense and [HTTPOS](%20<a%20href=), an analysis of the actual prevalence of pipelining and server side support for the HTTPOS feature set was not performed. Nor were statistics on actual request combination and reordering given, nor were the effects on the feature components analyzed.

4.  Navigation-based Hidden Markov Models are user-specific, and will also suffer from Garbage-In Garbage-Out false positive properties.
    While a Hidden Markov Model would appear to provide increased accuracy by being able to utilize multiple observations, the reality of web usage is that users' navigation patterns are not uniform and will vary by individual and social group, especially for news/portal sites and for social networks. For example, people often navigate off of Twitter to view outside links, and some people share more links than others. It is quite likely that the HMM will consider any link portal (or any repetitive background network activity) that has an occasional false positive match for Twitter to be mistaken for such intermittent Twitter usage.

Literature Review: Tao Wang and Ian Goldberg
--------------------------------------------

Title: **[Improved Website Fingerprinting on Tor](http://freehaven.net/anonbib/cache/wpes13-fingerprinting.pdf)**

This paper improves upon the work by Cai et al by statistically removing Tor flow control cells, improving the training performance of the classifier, and by performing a small-scale open world study of edit distance based classifiers. It also provides some limited analysis of difficult to classify sites.

The paper has the following issues:

1.  A broken implementation of Tor Browser's defense was studied, despite warnings to the contrary.

    Last year, [we discovered serious issues](https://trac.torproject.org/projects/tor/ticket/8470) with the HTTP Pipeline randomization defense that were introduced during the transition from Firefox 4 to Firefox 10, and that other issues may have been present in the Firefox 4 version as well. These issues were corrected during the transition to Firefox 17, and the pipeline randomization defense was vastly improved, but the authors still chose to evaluate the broken version, despite our offers for assistance. Moreover, like previous work, an analysis of the actual prevalence of server-side pipelining support and request combination and reordering was not performed.

2.  Small world size.

    This paper studies a smaller closed world size than the previous edit distance based work (100 pages instead of 1000), and uses only 1000 pages for its open world study.

3.  Target site types were not varied in the open world.
    Unlike Panchenko's work, the types of sites chosen as censored targets were fixed, not varied. This makes it hard to evaluate the effects of types of sites with either very distinct or more typical traffic patterns on the accuracy of their classifier.

[Source code is provided](https://cs.uwaterloo.ca/~t55wang/), however, so it may be possible to revisit and correct some of these issues, at least.

Concluding Remarks: Suggestions for Future Work
-----------------------------------------------

This post is not meant to dismiss the website traffic fingerprinting attack entirely. It is merely meant to point out that defense work has not been as conclusively studied as these papers have claimed, and that defenses are actually easier than is presently assumed by the current body of literature.

We believe that the theoretical and practical issues enumerated in this post demonstrate that defenses do not need to be terribly heavy-weight to be effective. It is likely that in practice, relatively simple defenses will still substantially increase the false positive rate of this attack when it is performed against large numbers of web pages (and non-web background traffic), against large volumes of Tor-like traffic, against large numbers of users, or any combination thereof.

We therefore encourage a re-evaluation of existing defenses such as [HTTPOS](http://freehaven.net/anonbib/cache/LZCLCP_NDSS11.pdf), SPDY and pipeline randomization, and [Guard node adaptive padding](https://trac.torproject.org/projects/tor/ticket/7028), [Traffic Morphing](http://freehaven.net/anonbib/cache/morphing09.pdf), as well as the development of additional defenses.

It is possible that some types of pages (especially those on video sites, file locker sites, and sites with very large content elements) may make natural false posties rare, especially when classified among smaller, more typical pages. For instance, it is unlikely to be possible to generate false positives when the classifier needs only to distinguish between pages from Wikipedia versus Youtube, but it is likely that generic large content and video downloads can be obfuscated such that it is hard to recognize the specific video or download site with minimal relative overhead.

As in the work done by Panchenko, we also suggest evaluating each of your classifier's explicit or implicit features for their [relative contribution to overall accuracy](https://en.wikipedia.org/wiki/Feature_selection) (especially among similar classes of sites) as this will help guide the padding and obfuscation behaviors of any defenses you or others might devise. The high-information component features or edit distances can be analyzed and used as input to a statistically adaptive padding defense, for example.

In any event, please do contact us if you're interested in studying these or other defenses in Tor Browser or Tor itself.

If you are not interested in helping improve the defenses of Tor, do not have time to perform such evaluations in a thorough manner, or have already previously published a website traffic fingerprinting attack paper yourself, we request that you publish or at least provide us with the source code and the data sets involved in your attack, so that we or others can reproduce your results and evaluate potential defenses as well.

Concluding Remarks: Dual Purpose Defenses
-----------------------------------------

It turns out that some defenses against the website traffic fingerprinting attack are also useful against the end-to-end correlation attack. In particular, defenses that increase the rate of false positives of website traffic fingerprinting using padding and other one-ended schemes is very likely to increase the rate of false positives for end-to-end correlation, especially under situations where either limited record-keeping capacity, sample-based analysis, or link-level encryption reduce connection and inter-packet timing information.

If a defense introduces false positive between many different web pages in website traffic fingerprinting by manipulating the traffic patterns at the entrance of the Tor network but not the exit, it will be very likely to introduce false positives during correlation between the entrance and exit traffic of simultaneous downloads of these same pages. As in website traffic fingerprinting, it turns out that even a small amount of false positives will [frustrate a dragnet adversary attempting end-to-end correlation](http://archives.seul.org/or/dev/Sep-2008/msg00016.html).

End-to-end correlation is a much more difficult problem, and we may not ever solve the problem of repeated observations. However, we likely can increase the number and duration of successful observations that correlation attacks will require to build high confidence, especially if the user base grows very large, and if the web moves to higher adoption rates of TLS (so that HTTP identifiers are not available to provide long-term linkability at exit nodes).

Promising defenses include [Adaptive Padding](https://trac.torproject.org/projects/tor/ticket/7028), [Traffic Morphing](http://freehaven.net/anonbib/cache/morphing09.pdf), and various [transformation and prediction proxies](http://dev.online6.eu/spdytor/) at the exit node (which could also help performance while we're at it).
