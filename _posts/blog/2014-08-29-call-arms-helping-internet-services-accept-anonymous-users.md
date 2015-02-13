---
layout: post
title: "A call to arms: Helping Internet services accept anonymous users"
permalink: call-arms-helping-internet-services-accept-anonymous-users
date: 2014-08-29 16:26:51
author: arma
category: blog
status: closed
tags: ["advocacy", "research"]
---

Looking for a way to help the Internet stay open and free? This topic needs some dedicated people to give it more attention — it could easily grow to as large a project as Tor itself. In the short term, OTF's [Information Controls Fellowship Program](https://www.opentechfund.org/labs/fellowships) has expressed interest in funding somebody to get this project going, and EFF's Eva Galperin has said she'd be happy to manage the person as an OTF fellow at EFF, with mentorship from Tor people. The first round of those proposals has a deadline in a few days, but if that timeframe doesn't work for you, this problem isn't going away: let us know and we can work with you to help you coordinate other funding.

The problem
-----------

We used to think there are two main ways that the Tor network can fail. First, legal or policy pressure can make it so nobody is willing to run a relay. Second, pressure on or from Internet Service Providers can reduce the number of places willing to host exit relays, which in turn squeezes down the anonymity that the network can provide. Both of these threats are hard to solve, but they are challenges that we've known about for a decade, and due in large part to strong ongoing collaborations we have a pretty good handle on them.

We missed a third threat to Tor's success: a growing number of websites treat users from anonymity services differently. Slashdot doesn't let you post comments over Tor, Wikipedia won't let you edit over Tor, and Google sometimes gives you a captcha when you try to search (depending on what other activity they've seen from that exit relay lately). Some sites like Yelp go further and refuse to even serve pages to Tor users.

The result is that the Internet as we know it is siloing. Each website operator works by itself to figure out how to handle anonymous users, and generally neither side is happy with the solution. The problem isn't limited to just Tor users, since these websites face basically the same issue with users from open proxies, users from AOL, users from Africa, etc.

Two recent trends make the problem more urgent. First, sites like Cloudflare, Akamai, and Disqus create bottlenecks where their components are used by many websites. This centralization impacts many websites at once when e.g. Cloudflare changes its strategy for how to handle Tor users. Second, services increasingly outsource their blacklisting, such that e.g. Skype refuses connections from IP addresses that run Tor exit relays, not because they worry about abuse via Tor (it's hard to use Skype over Tor), but because their blacklist provider has an incentive to be overbroad in its blocking. (Blacklist providers compete in part by having "the most complete" list, and in many cases it's hard for services to notice that they're losing contributions from now-missing users.)

Technical mechanisms do exist to let anonymous users interact with websites in ways that control abuse better. Simple technical approaches include "you can read but you can't post" or "you have to log in to post". More complex approaches track reputation of users and give them access to site features based on past behavior of the user rather than on past behavior of their network address. Several research designs suggest using [anonymous credentials](http://freehaven.net/anonbib/#oakland11-formalizing), where users anonymously receive a cryptographic credential and then prove to the website that they possess a credential that hasn't been blacklisted — without revealing their credential, so the website can't link them to their past behavior.

Social mechanisms have also proven effective in some cases, ranging from community moderation (I hear Wikipedia Germany manually approves edits from users who don't have sufficiently reputable accounts), to flagging behavior from Tor users (even though you don't know \*which\* Tor user it is) so other participants can choose how to interact with them.

But applying these approaches to real-world websites has not gone well overall. Part of the challenge is that the success stories are not well-publicized, so each website feels like it's dealing with the question in isolation. Some sites do in fact face quite different problems, which require different solutions: Wikipedia doesn't want jerks to change the content of pages, whereas Yelp doesn't want competitors to scrape all its pages. We can also imagine that some companies, like ones that get their revenue from targeted advertising, are fundamentally uninterested in allowing anonymous users at all.

A way forward
-------------

The solution I envision is to get a person who is both technical and good at activism to focus on this topic. Step one is to enumerate the set of websites and other Internet services that handle Tor connections differently from normal connections, and look for patterns that help us identify the common (centralized) services that impact many sites. At the same time, we should make a list of solutions — technical and social — that are in use today. There are a few community-led starts on the Tor wiki already, like [the DontBlockMe page](https://trac.torproject.org/projects/tor/wiki/org/projects/DontBlockMe) and a [List of Services Blocking Tor](https://trac.torproject.org/projects/tor/wiki/org/doc/ListOfServicesBlockingTor).

Step two is to sort the problem websites based on how amenable they would be to our help. Armed with the toolkit of options we found in step one, we should go to the first (most promising) site on the list and work with them to understand their problem. Ideally we can adapt one of the ideas from the toolkit; otherwise we'll need to invent and develop a new approach tailored to their situation and needs. Then we should go to the second site on the list with our (now bigger) toolkit, and so on down the list. Once we have some success stories, we can consider how to scale better, such as holding a conference where we invite the five best success cases plus the next five unsolved sites on our list.

A lot of the work will be building and maintaining social connections with engineers at the services, to help them understand what's possible and to track regressions (for example, every year or so Google gets a new engineer in charge of deciding when to give out Captchas, and they seem to have no institutional memory of how the previous one decided to handle Tor users). It might be that the centralization of Cloudflare et al can be turned around into an advantage, where making sure they have a good practices will scale to help many websites at once.

EFF is the perfect organization to lead this charge, given its community connections, its campaigns like [Who has your back?](https://www.eff.org/who-has-your-back-2014), and its more (at least more than Tor ;) neutral perspective on the topic. And now, when everybody is sympathetic about the topic of surveillance, is a great time to try to take back some ground. We have a wide variety of people who want to help, from scientists and research groups who would help with technical solutions if only they understood the real problems these sites face, to users and activists who can help publicize both the successful cases and the not-yet-successful cases.

Looking ahead to the future, I'm also part of an upcoming research collaboration with Dan Boneh, Andrea Forte, Rachel Greenstadt, Ryan Henry, Benjamin Mako Hill, and Dan Wallach who will look both at the technical side of the problem (building more useful ideas for the toolkit) and also the social side of the problem: how can we quantify the loss to Wikipedia, and to society at large, from turning away anonymous contributors? Wikipedians say "we have to blacklist all these IP addresses because of trolls" and "Wikipedia is rotting because nobody wants to edit it anymore" in the same breath, and we believe these points are related. The group is at the "applying for an NSF grant" stage currently, so it will be a year or more before funding appears, but I mention it because we should get somebody to get the ball rolling now, and hopefully we can expect reinforcements to appear as momentum builds.

In summary, if this call to arms catches your eye, your next steps are to think about what you most want to work on to get started, and how you would go about doing it. You can apply for an OTF fellowship, or we can probably help you find other funding sources as needed too.
