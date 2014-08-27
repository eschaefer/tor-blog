---
layout: post
title: "Improving Tor's anonymity by changing guard parameters"
permalink: improving-tors-anonymity-changing-guard-parameters
date: 2013-10-16
author: arma
category: blog
tags: ["anonymity", "entry guards", "hidden services", "research"]
---

There are tensions in the Tor protocol design between the anonymity provided by entry guards and the performance improvements from better load balancing. This blog post walks through the research questions I raised in 2011, then summarizes answers from three recent papers written by researchers in the Tor community, and finishes by explaining what Tor design changes we need to make to provide better anonymity, and what we'll be trading off.

# Part one: The research questions

In Tor, each client selects a few relays at random, and chooses only from those relays when making the first hop of each circuit. This [entry guard](https://www.torproject.org/docs/faq#EntryGuards) design helps in three ways:

First, entry guards protect against the " [predecessor attack](http://freehaven.net/anonbib/#Wright:2004)": if Alice (the user) instead chose new relays for each circuit, eventually an attacker who runs a few relays would be her first and last hop. With entry guards, the risk of end-to-end correlation for any given circuit is the same, but the cumulative risk for all her circuits over time is [capped](http://freehaven.net/anonbib/#hs-attack06).

Second, they help to protect against the " [denial of service as denial of anonymity](http://freehaven.net/anonbib/#ccs07-doa)" attack, where an attacker who runs quite a few relays fails any circuit that he's a part of and that he can't win against, forcing Alice to generate more circuits and thus increasing the overall chance that the attacker wins. Entry guards greatly reduce the risk, since Alice will never choose outside of a few nodes for her first hop.

Third, entry guards raise the startup cost to an adversary who runs relays in order to trace users. Without entry guards, the attacker can sign up some relays and immediately start having chances to observe Alice's circuits. With them, new adversarial relays won't have the Guard flag so won't be chosen as the first hop of any circuit; and even once they earn the Guard flag, users who have already chosen guards won't switch away from their current guards for [quite a while](https://blog.torproject.org/blog/lifecycle-of-a-new-relay).

In August 2011, I posted these four [open research questions around guard rotation parameters](https://blog.torproject.org/blog/research-problem-better-guard-rotation-parameters):

1. **Natural churn** : For an adversary that controls a given number of relays, if the user only replaces her guards when the current ones become unavailable, how long will it take until she's picked an adversary's guard?
2. **Artificial churn** : How much more risk does she introduce by intentionally switching to new guards before she has to, to load balance better?
3. **Number of guards** : What are the tradeoffs in performance and anonymity from picking three guards vs two or one? By default Tor picks three guards, since if we picked only one then some clients would pick a slow one and be sad forever. On the other hand, picking only one makes users safer.
4. **Better Guard flag assignment** : If we give the Guard flag to more or different relays, how much does it change all these answers?

For reference, Tor 0.2.3's entry guard behavior is "choose three guards, adding another one if two of those three go down but going back to the original ones if they come back up, and also throw out (aka rotate) a guard 4-8 weeks after you chose it." I'll discuss in "Part three" of this post what changes we should make to improve this policy.

# Part two: Recent research papers

Tariq Elahi, a grad student in Ian Goldberg's group in Waterloo, began to answer the above research questions in his paper [Changing of the Guards: A Framework for Understanding and Improving Entry Guard Selection in Tor](http://freehaven.net/anonbib/#wpes12-cogs) (published at WPES 2012). His paper used eight months of real-world historical [Tor network data](https://metrics.torproject.org/data.html) (from April 2011 to December 2011) and simulated various guard rotation policies to see which approaches protect users better.

Tariq's paper considered a quite small adversary: he let all the clients pick honest guards, and then added one new small guard to the 800 or so existing guards. The question is then what fraction of clients use this new guard over time. Here's a graph from the paper, showing (assuming all users pick three guards) the vulnerability due to natural churn ("without guard rotation") vs natural churn plus also intentional guard rotation:

[![Vulnerability from natural vs intentional guard rotation](https://people.torproject.org/~arma/rotation-elahi.png)](https://people.torproject.org/~arma/rotation-elahi.png)

In this graph their tiny guard node, in the "without guard rotation" scenario, ends up getting used by about 3% of the clients in the first few months, and gets up to 10% by the eight-month mark. The more risky scenario — which Tor uses today — sees the risk shoot up to 14% in the first few months. (Note that the y-axis in the graph only goes up to 16%, mostly because the attacking guard is so small.)

The second paper to raise the issue is from Alex Biryukov, Ivan Pustogarov, and Ralf-Philipp Weinmann in Luxembourg. Their paper [Trawling for Tor Hidden Services: Detection, Measurement, Deanonymization](http://freehaven.net/anonbib/#oakland2013-trawling) (published at Oakland 2013) mostly focuses on other attacks (like how to censor or track popularity of hidden services), but their Section VI.C. talks about the "run a relay and wait until the client picks you as her guard" attack. In this case they run the numbers for a much larger adversary: if they run 13.8% of the Tor network for eight months there's more than a 90% chance of a given hidden service using their guard sometime during that period. That's a huge fraction of the network, but it's also a huge chance of success. And since hidden services in this case are basically the same as Tor clients (they choose guards and build circuits the same way), it's reasonable to conclude that their attack works against normal clients too so long as the clients use Tor often enough during that time.

I should clarify three points here.

First clarifying point: Tariq's paper makes two simplifying assumptions when calling an attack successful if the adversary's relay \*ever\* gets into the user's guard set. 1) He assumes that the adversary is also either watching the user's destination (e.g. the website she's going to), or he's running enough exit relays that he'll for sure be able to see the correponding flow out of the Tor network. 2) He assumes that the end-to-end correlation attack (matching up the incoming flow to the outgoing flow) is instantaneous and perfect. Alex's paper argues pretty convincingly that these two assumptions are easier to make in the case of attacking a hidden service (since the adversary can dictate how often the hidden service makes a new circuit, as well as what the traffic pattern looks like), and the paper I describe next addresses the first assumption, but the second one ("how successful is the correlation attack at scale?" or maybe better, "how do the false positives in the correlation attack compare to the false negatives?") remains an open research question.

Researchers generally agree that given a handful of traffic flows, it's easy to match them up. But what about the millions of traffic flows we have now? What levels of false positives (algorithm says "match!" when it's wrong) are acceptable to this attacker? Are there some simple, not too burdensome, tricks we can do to drive up the false positives rates, even if we all agree that those tricks wouldn't work in the "just looking at a handful of flows" case?

More precisely, it's possible that correlation attacks don't scale well because as the number of Tor clients grows, the chance that the exit stream actually came from a different Tor client (not the one you're watching) grows. So the confidence in your match needs to grow along with that or your false positive rate will explode. The people who say that correlation attacks don't scale use phrases like " [say your correlation attack is 99.9% accurate](http://archives.seul.org/or/dev/Sep-2008/msg00016.html)" when arguing it. The folks who think it does scale use phrases like "I can easily make my correlation attack arbitrarily accurate." My hope is that the reality is somewhere in between — correlation attacks in the current Tor network can probably be made plenty accurate, but perhaps with some simple design changes we can improve the situation. In any case, I'm not going to try to tackle that research question here, except to point out that 1) it's actually unclear in practice whether you're done with the attack if you get your relay into the user's guard set, or if you are now faced with a challenging flow correlation problem that could produce false positives, and 2) the goal of the entry guard design is to make this issue moot: it sure would be nice to have a design where it's hard for adversaries to get into a position to see both sides, since it would make it irrelevant how good they are at traffic correlation.

Second clarifying point: it's about the probabilities, and that's intentional. Some people might be scared by phrases like "there's an x% chance over y months to be able to get an attacker's relay into the user's guard set." After all, they reason, shouldn't Tor provide absolute anonymity rather than probabilistic anonymity? This point is even trickier in the face of centralized anonymity services that promise ["100% guaranteed"](https://svn.torproject.org/svn/projects/articles/circumvention-features.html#5) anonymity, when what they really mean is "we could watch everything you do, and we might sell or give up your data in some cases, and even if we don't there's still just one point on the network where an eavesdropper can learn everything." Tor's path selection strategy distributes trust over multiple relays to avoid this centralization. The trouble here isn't that there's a chance for the adversary to win — the trouble is that our current parameters make that chance bigger than it needs to be.

To make it even clearer: the entry guard design is doing its job here, just not well enough. Specifically, \*without\* using the entry guard design, an adversary who runs some relays would very quickly find himself as the first hop of one of the user's circuits.

Third clarifying point: we're considering an attacker who wants to learn if the user \*ever\* goes to a given destination. There are plenty of reasonable other things an attacker might be trying to learn, like building a profile of many or all of the user's destinations, but in this case Tariq's paper counts a successful attack as one that confirms (subject to the above assumptions) that the user visited a given destination once.

And that brings us to the third paper, by Aaron Johnson et al: [Users Get Routed: Traffic Correlation on Tor by Realistic Adversaries](http://freehaven.net/anonbib/#ccs2013-usersrouted) (upcoming at CCS 2013). This paper ties together two previous series of research papers: the first is "what if the attacker runs a relay?" which is what the above two papers talked about, and the second is "what if the attacker can watch part of the Internet?"

The first part of the paper should sound pretty familiar by now: they simulated running a few entry guards that together make up 10% of the guard capacity in the Tor network, and they showed that (again using historical Tor network data, but this time from October 2012 to March 2013) the chance that the user has made a circuit using the adversary's relays is more than 80% by the six month mark.

In this case their simulation includes the adversary running a fast exit relay too, and the user performs a set of sessions over time. They observe that the user's traffic passes over pretty much all the exit relays (which makes sense since Tor doesn't use an "exit guard" design). Or summarizing at an even higher level, the conclusion is that so long as the user uses Tor enough, this paper confirms the findings in the earlier two papers.

Where it gets interesting is when they explain that "the adversary could run a relay" is not the only risk to worry about. They build on the series of papers started by ["Location Diversity in Anonymity Networks"](http://freehaven.net/anonbib/#feamster:wpes2004) (WPES 2004), ["AS-awareness in Tor path selection"](http://freehaven.net/anonbib/#DBLP:conf:ccs:EdmanS09) (CCS 2009), and most recently ["An Empirical Evaluation of Relay Selection in Tor"](http://freehaven.net/anonbib/#ndss13-relay-selection) (NDSS 2013). These papers look at the chance that traffic from a given Tor circuit will traverse a given set of Internet links.

Their point, which like all good ideas is obvious in retrospect, is that rather than running a guard relay and waiting for the user to switch to it, the attacker should instead monitor as many Internet links as he can, and wait for the user to use a guard such that traffic between the user and the guard passes over one of the links the adversary is watching.

This part of the paper raises as many questions as it answers. In particular, all the users they considered are in or near Germany. There are also quite a few Tor relays in Germany. How much of their results here can be explained by pecularities of Internet connectivity in Germany? Are their results predictive in any way about how users on other continents would fare? Or said another way, how can we learn whether their conclusion shouldn't instead be "German Tor users are screwed, because look how Germany's Internet topology is set up"? Secondly, their scenario has the adversary control the Autonomous System (AS) or Internet Exchange Point (IXP) that maximally deanonymizes the user (they exclude the AS that contains the user and the AS that contains her destinations). This "best possible point to attack" assumption a) doesn't consider how hard it is to compromise that particular part of the Internet, and b) seems like it will often be part of the Internet topology near the user (and thus vary greatly depending on which user you're looking at). And third, like the previous papers, they think of an AS as a single Internet location that the adversary is either monitoring or not monitoring. Some ASes, like large telecoms, are quite big and spread out.

That said, I think it's clear from this paper that there \*do\* exist realistic scenarios where Tor users are at high risk from an adversary watching the nearby Internet infrastructure and/or parts of the Internet backbone. Changing the guard rotation parameters as I describe in "Part three" below will help in some of these cases but probably won't help in all of them. The canonical example that I've given in talks about "a person in Syria using Tor to visit a website in Syria" remains a very serious worry.

The paper also makes me think about exit traffic patterns, and how to better protect people who use Tor for only a short period of time: many websites pull in resources from all over, especially resources from centralized ad sites. This risk (that it greatly speeds the rate at which an adversary watching a few exit points — or heck, a few ad sites — will be able to observe a given user's exit traffic) provides the most compelling reason I've heard so far to ship Tor Browser Bundle with an ad blocker — or maybe better, with something like [Request Policy](https://www.requestpolicy.com/) that doesn't even touch the sites in the first place. On the other hand, Mike Perry still doesn't want to ship an ad blocker in TBB, since he doesn't want to pick a fight with Google and give them even more of a reason to block/drop all Tor traffic. I can see that perspective too.

# Part three: How to fix it

Here are five steps we should take, in rough order of how much impact I think each of them would have on the above attacks.

If you like metaphors, think of each time you pick a new guard as a coin flip (heads you get the adversary's guard, tails you're safe this time), and the ideas here aim to reduce both the number and frequency of coin flips.

**Fix 1: Tor clients should use fewer guards.**

The primary benefit to moving to fewer guards is that there are fewer coin flips every time you pick your guards.

But there's a second benefit as well: right now your choice of guards acts as a kind of fingerprint for you, since very few other users will have picked the same three guards you did. (This fingerprint is only usable by an attacker who can discover your guard list, but in some scenarios that's a realistic attack.) To be more concrete: if the adversary learns that you have a particular three guards, and later sees an anonymous user with exactly the same guards, how likely is it to be you? Moving to two guards helps the math a lot here, since you'll overlap with many more users when everybody is only picking two.

On the other hand, the main downside is increased variation in performance. Here's Figure 10 from Tariq's paper:

[![Average guard capacity for various numbers of guards](https://people.torproject.org/~arma/1guard-performance.png)](https://people.torproject.org/~arma/1guard-performance.png)

"Farther to the right" is better in this graph. When you pick three guards (the red line), the average speed of your guards is pretty good (and pretty predictable), since most guards are pretty fast and it's unlikely you'll pick slow ones for all three. However, when you only pick only one guard (the purple line), the odds go up a lot that you get unlucky and pick a slow one. In more concrete numbers, half of the Tor users will see up to 60% worse performance.

The fix of course is to raise the bar for becoming a guard, so every possible guard will be acceptably fast. But then we have fewer guards total, increasing the vulnerability from other attacks! Finding the right balance (as many guards as possible, but all of them fast) is going to be an ongoing challenge. See [Brainstorm tradeoffs from moving to 2 (or even 1) guards (ticket 9273)](https://trac.torproject.org/projects/tor/ticket/9273) for more discussion.

Switching to just one guard will also preclude deploying [Conflux](http://freehaven.net/anonbib/#pets13-splitting), a recent proposal to improve Tor performance by routing traffic over multiple paths in parallel. The Conflux design is appealing because it not only lets us make better use of lower-bandwidth relays (which we'll need to do if we want to greatly grow the size of the Tor network), but it also lets us dynamically adapt to congestion by shifting traffic to less congested routes. Maybe some sort of "guard family" idea can work, where a single coin flip chooses a pair of guards and then we split our traffic over them. But if we want to avoid doubling the exposure to a network-level adversary, we might want to make sure that these two guards are near each other on the network — I think the analysis of the network-level adversary in Aaron's paper is the strongest argument for restricting the variety of Internet paths that traffic takes between the Tor client and the Tor network.

This discussion about reducing the number of guards also relates to bridges: right now if you configure ten [bridges](https://www.torproject.org/docs/bridges), you round-robin over all of them. It seems wise for us to instead use only the first bridge in our bridge list, to cut down on the set of Internet-level adversaries that get to see the traffic flows going into the Tor network.

**Fix 2: Tor clients should keep their guards for longer.**

In addition to choosing fewer guards, we should also avoid switching guards so often. I originally picked "one or two months" for guard rotation since it seemed like a very long time. In Tor 0.2.4, we've changed it to "two or three months". But I think changing the guard rotation period to a year or more is probably much wiser, since it will slow down the curves on all the graphs in the above research papers.

I asked Aaron to make a graph comparing the success of an attacker who runs 10% of the guard capacity, in the "choose 3 guards and rotate them every 1-2 months" case and the "choose 1 guard and never rotate" case:

[![Vulnerability from natural vs intentional guard rotation](https://people.torproject.org/~arma/room-for-improvement.png)](https://people.torproject.org/~arma/room-for-improvement.png)

In the "3 guard" case (the blue line), the attacker's success rate rapidly grows to about 25%, and then it steadily grows to over 80% by the six month mark. The "1 guard" case (green line), on the other hand, grows to 10% (which makes sense since the adversary runs 10% of the guards), but then it levels off and grows only slowly as a function of network churn. By the six month mark, even this very large adversary's success rate is still under 25%.

So the good news is that by choosing better guard rotation parameters, we can almost entirely resolve the vulnerabilities described in these three papers. Great!

Or to phrase it more as a research question, once we get rid of this known issue, I'm curious how the new graphs over time will look, especially when we have a more sophisticated analysis of the "network observer" adversary. I bet there are some neat other attacks that we'll need to explore and resolve, but that are being masked by the poor guard parameter issue.

However, fixing the guard rotation period issue is alas not as simple as we might hope. The fundamental problem has to do with "load balancing": allocating traffic onto the Tor network so each relay is used the right amount. If Tor clients choose a guard and stick with it for a year or more, then old guards (relays that have been around and stable for a long time) will see a lot of use, and new guards will see very little use.

I wrote a separate blog post to provide background for this issue: " [The lifecycle of a new relay](https://blog.torproject.org/blog/lifecycle-of-a-new-relay)". Imagine if the ramp-up period in the graph from that blog post were a year long! People would set up fast relays, they would get the Guard flag, and suddenly they'd see little to no traffic for months. We'd be throwing away easily half of the capacity volunteered by relays.

One approach to resolving the conflict would be for the directory authorities to track how much of the past n months each relay has had the Guard flag, and publish a fraction in the networkstatus consensus. Then we'd teach clients to rebalance their path selection choices so a relay that's been a Guard for only half of the past year only counts 50% as a guard in terms of using that relay in other positions in circuits. See [Load balance right when we have higher guard rotation periods (ticket 9321)](https://trac.torproject.org/projects/tor/ticket/9321) for more discussion, and see [Raise our guard rotation period (ticket 8240)](https://trac.torproject.org/projects/tor/ticket/8240) for earlier discussions.

Yet another challenge here is that sticking to the same guard for a year gives plenty of time for an attacker to identify the guard and attack it somehow. It's particularly easy to identify the guard(s) for hidden services currently (since as mentioned above, the adversary can control the rate at which hidden services make new circuits, simply by visiting the hidden service), but similar attacks can probably be made to work against normal Tor clients — see e.g. the http-level refresh tricks in [How Much Anonymity does Network Latency Leak?](http://freehaven.net/anonbib/#tissec-latency-leak) This attack would effectively turn Tor into a network of one-hop proxies, to an attacker who can efficiently enumerate guards. That's not a complete attack, but it sure does make me nervous.

One possible direction for a fix is to a) isolate streams by browser tab, so all the requests from a given browser tab go to the same circuit, but different browser tabs get different circuits, and then b) stick to the same three-hop circuit (i.e. same guard, middle, and exit) for the lifetime of that session (browser tab). How to slow down guard enumeration attacks is a tough and complex topic, and it's too broad for this blog post, but I raise the issue here as a reminder of how interconnected anonymity attacks and defenses are. See [Slow Guard Discovery of Hidden Services and Clients (ticket 9001)](https://trac.torproject.org/projects/tor/ticket/9001) for more discussion.

**Fix 3: The Tor code should better handle edge cases where you can't reach your guard briefly.**

If a temporary network hiccup makes your guard unreachable, you switch to another one. But how long is it until you switch back? If the adversary's goal is to learn whether you ever go to a target website, then even a brief switch to a guard that the adversary can control or observe could be enough to mess up your anonymity.

Tor clients fetch a new networkstatus consensus every 2-4 hours, and they are willing to retry non-running guards if the new consensus says they're up again.

But I think there are a series of little bugs and edge cases where the Tor client abandons a guard more quickly than it should. For example, we mark a guard as failed if any of our circuit requests time out before finishing the handshake with the first hop. We should audit both the design and the source code with an eye towards identifying and resolving these issues.

We should also consider whether an adversary can \*induce\* congestion or resource exhaustion to cause a target user to switch away from her guard. Such an attack could work very nicely coupled with the guard enumeration attacks discussed above.

Most of these problems exist because in the early days we emphasized reachability ("make sure Tor works") over anonymity ("be very sure that your guard is gone before you try another one"). How should we handle this tradeoff between availability and anonymity: should you simply stop working if you've switched guards too many times recently? I imagine different users would choose different answers to that tradeoff, depending on their priorities. It sounds like we should make it easier for users to select "preserve my anonymity even if it means lower availability". But at the same time, we should remember the lessons from [Anonymity Loves Company: Usability and the Network Effect](http://freehaven.net/anonbib/#usability:weis2006) about how letting users choose different settings can make them more distinguishable.

**Fix 4: We need to make the network bigger.**

We've been working hard in recent years to get more relay capacity. The result is a more than four-fold increase in network capacity since 2011:

[![Vulnerability from natural vs intentional guard rotation](https://people.torproject.org/~arma/bandwidth-since-2011.png)](https://people.torproject.org/~arma/bandwidth-since-2011.png)

As the network grows, an attacker with a given set of resources will have less success at the attacks described in this blog post. To put some numbers on it, while the relay adversary in Aaron's paper (who carries 660mbit/s of Tor traffic) represented 10% of the guard capacity in October 2012, that very same attacker would have been 20% of the guard capacity in October 2011. Today that attacker is about 5% of the guard capacity. Growing the size of the network translates directly into better defense against these attacks.

However, the analysis is more complex when it comes to a network adversary. Just adding more relays (and more relay capacity) doesn't always help. For example, adding more relay capacity in a part of the network that the adversary is already observing can actually \*decrease\* anonymity, because it increases the fraction the adversary can watch. We discussed many of these issues in the [thread about turning funding into more exit relays](https://lists.torproject.org/pipermail/tor-relays/2012-July/001433.html). For more details about the relay distribution in the current Tor network, check out [Compass](https://compass.torproject.org/), our tool to explore what fraction of relay capacity is run in each country or AS. Also check out Lunar's [relay bubble graphs](https://metrics.torproject.org/bubbles.html).

Yet another open research question in the field of anonymous communications is how the success rate of a network adversary changes as the Tor network changes. If we were to plot the success rate of the \*relay\* adversary using historical Tor network data over time, it's pretty clear that the success rate would be going down over time as the network grows. But what's the trend for the success rate of the network adversary over the past few years? Nobody knows. It could be going up or down. And even if it is going down, it could be going down quickly or slowly.

(Read more in [Research problem: measuring the safety of the Tor network](https://blog.torproject.org/blog/research-problem-measuring-safety-tor-network) where I describe some of these issues in more detail.)

Recent papers have gone through enormous effort to get one, very approximate, snapshot of the Internet's topology. Doing that effort retroactively and over long and dynamic time periods seems even more difficult and more likely to introduce errors.

It may be that the realities of Internet topology centralization make it so that there are fundamental limits on how much safety Tor users can have in a given network location. On the other hand, researchers like Aaron Johnson are optimistic that "network topology aware" path selection can improve Tor's protection against this style of attack. Much work remains.

**Fix 5: We should assign the guard flag more intelligently.**

In point 1 above I talked about why we need to raise the bar for becoming a guard, so all guards can provide adequate bandwidth. On the other hand, having fewer guards is directly at odds with point 4 above.

My [original guard rotation parameters blog post](https://blog.torproject.org/blog/research-problem-better-guard-rotation-parameters) ends with this question: what algorithm should we use to assign Guard flags such that a) we assign the flag to as many relays as possible, yet b) we minimize the chance that Alice will use the adversary's node as a guard?

We should use historical Tor network data to pick good values for the parameters that decide which relays become guards. This remains a great thesis topic if somebody wants to pick it up.

# Part four: Other thoughts

What does all of this discussion mean for the rest of Tor? I'll close by trying to tie this blog post to the broader Tor world.

First, all three of these papers come from the [Tor research community](http://freehaven.net/anonbib/), and it's great that Tor gets such attention. We get this attention because we put so much effort into [making it easy](https://research.torproject.org/) for researchers to analyze Tor: we've worked closely with these authors to help them understand Tor and focus on the most pressing research problems.

In addition, don't be fooled into thinking that these attacks only apply to Tor: using Tor is still better than using any other tool, at least in quite a few of these scenarios. That said, some other attacks in the research literature might be even easier than the attacks discussed here. These are fast-moving times for anonymity research. "Maybe you shouldn't use the Internet then" is still the best advice for some people.

Second, the [Tails](https://tails.boum.org/) live CD doesn't use persistent guards. That's really bad I think, assuming the Tails users have persistent behavior (which basically all users do). See [their ticket 5462](https://labs.riseup.net/code/issues/5462).

Third, the network-level adversaries rely on being able to recognize Tor flows. Does that argue that using [pluggable transports](https://www.torproject.org/docs/pluggable-transports), with [bridges](https://www.torproject.org/docs/bridges), might change the equation if it stops the attacker from recognizing Tor users?

Fourth, I should clarify that I don't think any of these large relay-level adversaries actually exist, except as a succession of researchers showing that it can be done. (GCHQ apparently ran a small number of relays a while ago, but not in a volume or duration that would have enabled this attack.) Whereas I \*do\* think that the network-level attackers exist, since they already invested in being able to surveil the Internet for other reasons. So I think it's great that Aaron's paper presents the dual risks of relay adversaries and link adversaries, since most of the time when people are worrying about one of them they're forgetting the other one.

Fifth, there are still some ways to game the [bandwidth authority](https://gitweb.torproject.org/torflow.git/blob/HEAD:/NetworkScanners/BwAuthority/README.BwAuthorities) measurements (here's the spec [spec](https://gitweb.torproject.org/torflow.git/blob/HEAD:/NetworkScanners/BwAuthority/README.spec.txt)) into giving you more than your fair share of traffic. Ideally we'd adapt a design like [EigenSpeed](https://www.usenix.org/legacy/event/iptps09/tech/full_papers/snader/snader.pdf) so it can measure fast relays both robustly and accurately. This question also remains a great thesis topic.

And finally, as everybody wants to know: was this attack how "they" busted recent hidden services ( [Freedom Hosting](https://blog.torproject.org/blog/tor-security-advisory-old-tor-browser-bundles-vulnerable), [Silk Road](https://blog.torproject.org/blog/tor-and-silk-road-takedown), the attacks described in the latest [Guardian article](http://www.theguardian.com/world/2013/oct/04/nsa-gchq-attack-tor-network-encryption))? The answer is apparently no in each case, which means the techniques they \*did\* use were even \*lower\* hanging fruit. The lesson? Security is hard, and you have to get it right at many different levels.

