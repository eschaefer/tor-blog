---
layout: post
title: "Improving Private Browsing Modes: \"Do-Not-Track\" vs Real Privacy by Design"
permalink: blog/improving-private-browsing-modes-do-not-track-vs-real-privacy-design
date: 2011-06-13
author: mikeperry
category: blog
tags: ["chrome", "dnt", "do not track", "firefox", "incognito", "privacy by design", "private browsing", "tor browser", "torbutton"]
---

 **Updated 06/16/2011** : Break off window.name into its own linkability issue. While ultimately it should be handled identically to the referer, that was not clear in the original text.
**Updated 07/01/2011** : Add link to article about 81% consumer polling rate in favor of some form of Do Not Track...

As I said in my [previous post](https://blog.torproject.org/blog/toggle-or-not-toggle-end-torbutton), the Tor Project hopes to work on [a set of patches](https://trac.torproject.org/projects/tor/ticket/2871) that effectively improves the Private Browsing Mode of Firefox. Long term, we'd love to merge these patches upstream, and/or see them obsoleted by better implementations.

To help keep everyone on the same page with respect to this effort, I've decided to take some time to describe what we envision as our ideal private browsing mode.

Hopefully, such a mode would be useful for more than just Tor users. Indeed, there are many ways to obtain varying levels of IP address privacy once you have solid browser support for privacy by design. The average user is quite capable of going to a cafe and enabling private mode, and this ability can be explained to them in a single sentence by the UI. Arguably they can also obtain low-grade IP privacy simply by tethering to their cell phone, whose IP typically changes regularly. I am told that frequent IP rotation is also the norm for residential connections in Germany and much of the EU to deter services and malware. This is not to mention all of the commercial single-hop VPN and proxy privacy services out there that fail to provide actual browser privacy in their tools.

We believe that the [attention surrounding the "Do-Not-Track" header](http://thehill.com/blogs/hillicon-valley/technology/168871-survey-shows-consumers-want-government-to-protect-their-privacy-online) also indicates that network privacy is an important feature. However, we believe that it must be provided by design, as opposed to via a humble request to the adversary that is impossible to audit or enforce, especially outside of the United States. In his [presentation](http://w2spconf.com/2011/papers/balaSlides.pdf) at [W2SP](http://w2spconf.com/2011/), [Balachander Krishnamurthy](http://www.research.att.com/~bala/papers/) compared the "Do-Not-Track" request header to the real-world equivalent of leaving your door unlocked with a posted notice that reads "Do-Not-Rob". While many people actually do post "No Trespassing" and similar signs, no one expects these signs to replace actual security measures.

Unfortunately, right now the only usable and effective web privacy option for the average user is to install an [ad-blocker](http://adblockplus.org/) or [similar software](http://www.ghostery.com/). Personally, I see the need for an ad-blocker to achieve privacy as a huge failure of the web itself. If web tracking, profiling, and behavioral targeting is so extreme that it cannot be avoided except by blocking all ads, then the prevailing revenue model of the web is unsustainable. We must figure out a way to do non-intrusive, content-relevant advertising while still providing privacy, without relying on regulatory action that is unlikely to be enforceable.

Ok, so enough preaching. What does privacy by design look like? I'm going to describe a list of 7 key properties, some of which the major browser vendors already have or are working towards, but so far are not uniformly deployed in any browser, including even our own Tor Browser.

1. **Make local privacy optional**
2. **Avoid Linkability: Minimize privacy options, plugins and addons**
3. **Avoid Linkability: Isolate all non-private mode identifiers and state**
4. **Avoid Linkability: Isolate state per top-level domain**
5. **Avoid Linkability: Reduce fingerprintable attributes**
6. **Avoid Linkability: Reduce default referer information**
7. **Avoid Linkability: Restrict window.name to referer policy**

# Make local privacy optional

The browser vendors got it half right the first time around. There are many users who consider local storage privacy to be the primary feature they want from private browsing mode. However, we believe that local privacy is actually an orthogonal feature to network privacy: some users want both, but some only want one or the other.

Therefore, we believe that users should be given the option in private browsing mode to choose if they want to record browsing history or not. Many users will want to use private mode regularly, and will only be concerned about ad network tracking as opposed to local storage (ie similar to the "Do-Not-Track" header's use case). These users will still want history and "awesome bar" functionality to work for them. Almost all users will want to maintain access to their bookmarks and previously stored history from within the mode.

# Avoid Linkability: Minimize privacy options, plugins, and addons

Beyond the choice to store history and activity on disk, there [should not be](https://trac.torproject.org/projects/tor/ticket/3100) numerous global options provided to private browsing modes.

Each option that detectably alters browser behavior can be used as a fingerprinting tool on the part of ad networks. Similarly, [all extensions should be disabled in the mode except as an opt-in basis](http://blog.chromium.org/2010/06/extensions-in-incognito.html).

Instead of global browser privacy options, [privacy decisions should be made per top-level url-bar domain](https://wiki.mozilla.org/Privacy/Features/Site-based_data_management_UI) to eliminate the possibility of linkability between domains. For example, when a plugin object (or a JavaScript access of window.plugins) is present in a page, the user should be given the choice of allowing that plugin object **for that top-level url-bar domain only** . The same goes for exemptions to third party cookie policy, geo-location, and any other privacy permissions.

If the user has indicated they do not care about local history storage, these permissions can be written to disk. Otherwise, they should remain memory-only.

# Avoid Linkability: Isolate all non-private identifiers and state

All major browsers already make some effort to isolate explicit identifier state between non-private and private browsing (despite protest that their threat model does not actually require it). Obviously, privacy by design requires that this effort be continued.

The ability to link users between private and non-private browsing modes via explicit identifiers, browser state, or TLS state should be considered a flaw in the mode. After all, the user may have gone to a wifi cafe to obtain IP address privacy, expecting identifier privacy from their browser. It is not fair to [the user](https://wiki.mozilla.org/Security/Anonymous_Browsing#Use_Cases) to abjectly fail to protect them in this case.

# Avoid Linkability: Isolate state to top-level domain

However, users who want continuous "Do-Not-Track"-style privacy will likely use the mode regularly, possibly even exclusively, to avoid behavior advertising and associated tracking. [These users](https://wiki.mozilla.org/Security/Anonymous_Browsing#The_Paranoid) will also want to reduce the linkability between arbitrary sites they visit.

This is a particular concern for Tor as many activists use web-based email, social networking sites, and other web services for organizing. Their activity in Tor Browser on one site should not trivially de-anonymize their activity on another site to ad networks and exits.

To provide this property, all identifiers and state must be isolated to the top-level url bar domain, [starting with cookies](https://wiki.mozilla.org/Thirdparty), but extending to [the cache](http://www.safecache.com/), DOM Storage, client certificates, and HTTP auth.

The benefit of this approach comes not only in the form of reduced linkability, but also in terms of simplified privacy UI. If all stored browser state and permissions become associated with the top-level url-bar domain, the six or seven different pieces of privacy UI governing these identifiers and permissions can become just [one piece of UI](https://bugzilla.mozilla.org/show_bug.cgi?id=565965#c21), possibly with a context-menu option to drill down into specific types of state.

We also believe that such an identifier model makes privacy relationships much more clear to the average user. Instead of having various disjoint relationships with and permissions for hundreds of omnipresent third-party domains, users will have one relationship with each of the top-level url-bar domains that they choose to interact with and authenticate to.

Obviously, the downside of this enhanced protection against identifier linkability is that third party services that rely on third party cookie transmission may be impeded by this model. Long term, the hope is for standardized, in-browser support for services federated login and "Like" buttons. Google Chrome has actually implemented a feature called [Web-Send](http://web-send.org/) that provides this functionality in a [privacy preserving way](http://web-send.org/features.html). They have even written a legacy HTML5 version that provides the same privacy properties, save for the need to trust [http://webintroducer.net](http://webintroducer.net "http://webintroducer.net") for DOM Storage.

We are also trying to introduce the notion of "protected cookies" in the alpha Tor Browser series, to allow users to specify they want to maintain a relationship with certain sites but not with others. To simplify this experience, we've currently entirely disabled Third Party Cookies in Tor Browser, but we believe that this may end up breaking mashup and federated login sites that might still be able to function under the more lenient double-keyed cookie model.

Several other interim steps are possible in the meantime. One could imagine iframe attributes that cause the browser chrome to request that a site be granted permission to set top-level cookies, or even a fully automated client-side mechanism that performs this promotion automatically for selected sites on mouse-click (such a mechanism is actually being prototyped by researchers right now).

# Avoid Linkability: Reduce fingerprintable attributes

Once the linkability via explicit identifiers is eliminated, it becomes important to address the linkability that is possible through [browser fingerprinting](https://wiki.mozilla.org/Fingerprinting).

Fingerprinting is a difficult issue to address, but that difficulty does not preclude a best-effort from being made at eliminating or mitigating the major culprits.

Luckily, [the major culprit](https://wiki.mozilla.org/Fingerprinting#Data) is plugin-provided information. Once plugins are restricted to only permitted top-level domains, fingerprinting linkability gets effectively reduced to the information available via CSS, Javascript, and HTTP headers.

The largest culprits in CSS and Javascript are [resolution and media information](https://trac.torproject.org/projects/tor/ticket/2875) (especially those properties that also provide information about the device and display as opposed to limiting information to the properties of the rendering window itself), the [number of fonts that can be loaded per origin](https://trac.torproject.org/projects/tor/ticket/2872), [time-based fingerprints](https://trac.torproject.org/projects/tor/ticket/3059), and [WebGL device information](https://trac.torproject.org/projects/tor/ticket/3323).

It is likely that we need another Panopticlick-style study that focuses exclusively on CSS and Javascript to determine the relative importance of these components, but most of them can be addressed without serious breakage of functionality.

# Avoid Linkability: Reduce default referer information

So far, the Tor Project has refrained from restricting referer primarily because we believe that restricting referer actually becomes less necessary if identifiers are isolated and linkability has been reduced.

However, non-Tor users do have one important element of linkability: IP address. Even those that have an alternate Internet connection may still be bound to a single alternate IP. These users probably actually benefit in a real way from a restricted referer. It turns out a lot of [information is already smuggled or leaked via referrer](http://w2spconf.com/2011/papers/privacyVsProtection.pdf) and URL parameters to third party sites, either deliberately or accidentally.

Referer restriction could take multiple forms, but we believe more site flexibility is key. Sites actually have no way to restrict referer for most element types currently, and conversely, sites will always be able to subvert referer restrictions by smuggling the same data in POST or URL parameters.

Therefore, we believe that referers should be restricted by default in private browsing mode using a same-origin policy where sites from different origins get either no referer, or a referer that is truncated to the top-level domain. However, sites should also be allowed to request an exemption to this rule on a per-site basis using an html attribute, which could trigger a chrome permissions request, or simply be granted automatically (on the assumption that they could just URL smuggle the data).

While this may not seem like much of a protection, at least it allows us to differentiate negligence from deliberate information sharing, and to restrict information leakage in the default scenario. Again, because this data can always be transmitted between elements either directly or via a back-channel, it is better it be visible and apparent than covert.

# Avoid Linkability: Restrict window.name to referer policy

Window.name poses many of the same conflicts as referer information. It gives sites a way to pass data between pages in the navigation lifespan of a tab. Sites can [use window.name to store data](http://www.thomasfrank.se/sessionvars.html), but are given no way to clear it easily. Hence it becomes very hard to differentiate deliberate data exchange from accidental leakage.

Just like referer, it is obvious that window.name should be empty whenever the URL bar is rewritten by the user. There should be no legitimate, functional need for data exchange between two arbitrary random user-typed URL bar domains in any situation. Window.name on user-entered URLs should be cleared regardless of any changes to existing referer policy.

Similarly, sites could be given the option to allow transmission of window.name to third party iframe elements, but the default should be to isolate window.name to the same origin policy. We do not believe this second step is required for Tor usage, but it may be helpful to non-Tor users, for similar reasons as the referer leakage.

As such, [our current plan](https://trac.torproject.org/projects/tor/ticket/3414) is to bind window.name's lifespan to the Referer header contents in our addon implementations.

# Conclusion

We believe that privacy can be a differentiating feature for browsers. Even [early studies](http://crypto.stanford.edu/~dabo/pubs/abstracts/privatebrowsing.html) revealed that many users immediately began using private browsing modes regularly, either by mistake or deliberately.

We believe that [many of these users](https://wiki.mozilla.org/Security/Anonymous_Browsing#Use_Cases) deliberately use private browsing in cafes and on other alternate Internet connections assuming that they are being protected from ad tracking and behavioral analysis. We welcome user studies to determine what users actually expect and want from private browsing modes for the definitive answer, but obviously we're pretty convinced what the outcome will be.

Privacy by design represents the technical realization of "Do-Not-Track": the ability to actually opt-out (prevent) a complete behavior profile from being built to record and model your specific web viewing habits.

In order for a private browsing mode to succeed in actually providing privacy by design, it must reduce activity linkability in all forms. Six out of the seven items mentioned above are really linkability issues at their core. Reducing the ability of the adversary to link private activity to non-private activity and also to other private activity is what privacy by design is all about. This reduction in linkability is what prevents a behavioral profile from being constructed.

The Tor Project looks forward to a day where privacy by design becomes a key feature of major browsers. We would love to be able to ship a vastly simplified browser extension that contains only a compiled Tor binary and some minimal addon code that simply "upgrades" the user's private browsing mode into a fully functional anonymous mode. The ability to do this would vastly simplify our package offerings, and make it significantly easier to get our software into censored and oppressed regions.

However, until then, we must do our best to attempt to provide software that we believe will provide the privacy and security that users have come to expect from us. For now, this means shipping our own browser.

