---
layout: post
title: "To Toggle, or not to Toggle: The End of Torbutton"
permalink: blog/toggle-or-not-toggle-end-torbutton
date: 2011-05-02
author: mikeperry
category: blog
tags: ["firefox", "tor browser", "tor browser bundle", "torbutton", "usability"]
---

In a random bar about two years ago, a Google Chrome developer asked me why Torbutton didn't just launch a new, clean Firefox profile/instance to deal with the tremendous number of state separation issues. Simply by virtue of him asking me this question, I realized how much better off Chrome was by implementing Incognito Mode this way and how much simpler it must have been for them overall (though they did not/do not deal with anywhere near as many issues as Torbutton does)...

So I took a deep breath, and explained how the original use model of Torbutton and my initial ignorance at the size of the problem had led me through a series of incremental improvements to address the state isolation issue one item at a time. Since the toggle model was present at the beginning of this vision quest, it was present at the end.

I realized at that same instant that in hindsight, this decision was monumentally stupid, and that I had been working harder, not smarter. However, I thought then that since we had the toggle model built, we might as well keep it: it allowed people to use their standard issue Firefoxes easily and painlessly with Tor.

I now no longer believe even this much. I think we should completely do away with the toggle model, as well as the entire idea of Torbutton as a separate piece of user-facing software, and rely solely on the Tor Browser Bundles, except perhaps with the addition of standalone Tor+Vidalia binaries for use by experts and relay operators.

The Tor Browser Bundles will include Torbutton, but we will no longer recommend that people use Torbutton without Tor Browser. Torbutton will be removed from addons.mozilla.org, and the Torbutton download page will clearly state that it is for experts only. If serious unfixed security issues begin to accumulate against the toggle model, we will stop providing Torbutton xpis at all.

I believe this shift must be done for a few reasons: some usability, some technical. Since I feel the usability issues trump the technical ones, I'll discuss them first.

Unfortunately, the Tor Project doesn't really have funding to conduct official usability studies to help us make the best choice, but I think that even without them, it is pretty clear that this migration is what we must do to improve the status quo.

I think the average user is horribly confused by both the toggle model and the need to install additional software into Firefox (or conversely, the need to \*also\* install Tor software onto their computers after they install Torbutton). I also think that the average user is not likely to use this software safely. They are likely to log in to sites over Tor that they shouldn't, forget which tor mode they are in, and forget which mode certain tabs were opened under. These are all nightmare situations for anonymity and privacy.

On the technical side, several factors are forcing us in the direction of a short-term fork of Firefox. The over-arching issue is that the set of bugfixes required to maintain the toggle model is a superset of those required to maintain the browser model. [Trac report #39](https://trac.torproject.org/projects/tor/report/39) lists the bugs we must fix for the browser model, where as to maintain the toggle model, we must fix bugs from [trac report #14](https://trac.torproject.org/projects/tor/report/14) in addition to the bugs in [report #39](https://trac.torproject.org/projects/tor/report/39).

A similar issue exists with [bugs that must be fixed in Firefox](https://www.torproject.org/torbutton/en/design/#FirefoxBugs). The Firefox API bugs that need to be addressed to properly support the toggle model include rather esoteric and complicated issues that few groups other than Tor will find useful.

This means more resistance from Mozilla to get the toggle mode bugs fixed or even merged, less likelihood the fixes will be used elsewhere, and more danger they will succumb to bitrot. As a result, the lag time between fix and deployment for low-priority Firefox bugs can be as long as 3 years. See [Bug 280661](https://bugzilla.mozilla.org/show_bug.cgi?id=280661) for an example.

The Tor Browser bugs on the other hand are more directly usable by Firefox in its own Private Browsing Mode, which makes them more likely to merge quicker, and be maintained long-term. Also, because we are releasing our own Firefox-based browser, we will also have more control over experimenting with them and deploying these fixes to our users rapidly, as opposed to waiting for the next major Firefox release.

So, we can either invest effort in improving the UI of Torbutton to better educate users to understand our particular rabbit-hole tunnel-vision of design choices, and also solving crazier Firefox bugs; or we can reconsider our user model and try to simplify our software.

We don't have the manpower (ie: enough me) to do both. This means we should go with the simpler, easier option.

We do face a small number of barriers and downsides associated with this plan. We are collecting the issues we need to address ASAP as child tickets of this bug:
 [https://trac.torproject.org/projects/tor/ticket/2880](https://trac.torproject.org/projects/tor/ticket/2880 "https://trac.torproject.org/projects/tor/ticket/2880")

Overall, the downsides seem to mostly apply to expert users and how they will adapt the custom Tor setups they have built. We don't anticipate a lot of long term issues with this group, as most of the configuration options of Torbutton will remain available, and users should still be able to install custom addons and configure their Tor Browser profile however they need (even to the point of running it side-by-side to a system tor instance that is used for non-web applications).

[Additional discussion](https://lists.torproject.org/pipermail/tor-talk/2011-April/020077.html) about this issue has occurred on the tor-talk mailinglist.

Hopefully this announcement doesn't ruin your day!

