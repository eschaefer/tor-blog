---
layout: post
title: "Trip report, October FBI conference"
permalink: blog/trip-report-october-fbi-conference
date: 2012-12-16
author: arma
category: blog
tags: ["law enforcement", "talks", "trip report"]
---

In October I attended an FBI conference, as part of my work to try to keep Tor on good relations with law enforcement. My first goal is to remind them of all the good uses of Tor, so if they ever find themselves lobbying to outlaw anonymity online, they'll understand what they're giving up. The second goal is to make sure they understand what Tor is and how it works, so if they encounter it in their investigations they'll hassle our exit relay operators less. (Here's a great way that one FBI person explained it to me: "I've got 10 leads, and 48 hours before this case doesn't matter anymore. If you can help me understand which leads \*not\* to follow, I can do my job better.") My third goal is to help them be able to use Tor correctly for their own jobs — remember that diversity of users is part of what makes Tor safe for everybody to use.

Overall, we've been doing a pretty good job at teaching US-based law enforcement about Tor. At the end of the conference, one of the FBI agents took me aside and asked "surely you have \*some\* sort of way of tracking your users?" When I pointed at various of his FBI colleagues in the room who had told me they use Tor every day for their work, and asked if he'd be comfortable if we had a way of tracing \*them\*, I think he got it.

I met a nice man from the DEA who worked on the "Farmer's Market" bust. This was in the news a lot back in April, where apparently some people were selling drugs online, and using a Tor hidden service for their website. At the time I thought the news stories could be summarized simply as "idiot drug sellers accept paypal payments, get busted." It turns out they were pretty smart about how to accept paypal payments — they just had random Americans receive the paypal payments, take a cut, and then turn them into a Panama-based digital currency, and the Panama company didn't want to help trace where the money went. The better summary for the news stories should actually have been "idiot drug sellers use hushmail, get busted." Way before they switched to a Tor hidden service, the two main people used Hushmail to communicate. After a subpoena (and apparently a lot of patience since Canada still isn't quite the same as the US), Hushmail rolled over and gave up copies of all the emails. Many more details here:
http://www.scribd.com/doc/89690597/Willemsindictment-Filed-045

I should still note that Tor doesn't introduce any magic new silver bullet that causes criminals to be uncatchable when before they weren't. The Farmer's Market people ran their webserver in some other foreign country before they switched to a Tor hidden service, and just the fact that the country didn't want to cooperate in busting them was enough to make that a dead end. Jurisdictional arbitrage is alive and well in the world.

