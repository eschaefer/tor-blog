---
layout: post
title: "Investigating http proxy performance with Tor"
permalink: blog/investigating-http-proxy-performance-tor
date: 2009-08-19
author: phobos
category: blog
tags: ["caching", "faster firefox", "faster tor", "open research", "performance", "polipo", "privoxy", "socks5", "tor browser bundle", "vidalia bundle"]
---

A while ago there was a thread on [OR-TALK](http://archives.seul.org/or/talk/) that devolved into

> "why does Tor still ship ancient privoxy?"

and

> "why are you shipping polipo with the Tor Browser Bundle instead of current privoxy?"

For those interested, the thread is here, [http://archives.seul.org/or/talk/Jul-2009/msg00063.html](http://archives.seul.org/or/talk/Jul-2009/msg00063.html "http://archives.seul.org/or/talk/Jul-2009/msg00063.html").

Scott had a good argument for why we should update the bundles to the latest privoxy, and I agree, we should. But then I started thinking about why we needed a proxy at all. Almost all browsers support socks5 direct, isn't that faster than a middleman proxy?

This got me thinking about why polipo is in the TBB, but not the other packages. The TBB "feels faster" when using Tor than using the installed Tor, Vidalia, and Privoxy. However, I couldn't find any actual testing of performance of polipo vs. privoxy vs. socks5 direct.

So I did it myself, in a loose manner. I wanted to quantify "feels faster".

The raw data from all the testing is :

- Tamper Data as xml,
- proxy config files,
- and results in a spreadsheet.

This is all contained in [http://freehaven.net/~phobos/polipo-v-privoxy.tar.gz](http://freehaven.net/~phobos/polipo-v-privoxy.tar.gz "http://freehaven.net/~phobos/polipo-v-privoxy.tar.gz") {.asc). There is a README as well. And yes, the ruby script is a quick and dirty hack.

I tested a few scenarios:

1) native [polipo](http://www.pps.jussieu.fr/~jch/software/polipo/) and [privoxy](http://www.privoxy.org/) without using Tor.
2) polipo and privoxy forwarding to Tor localhost:9050.
3) firefox socks5 direct to Tor via localhost:9050.

The summary of results:

- Native polipo is 54.5% faster on average than native privoxy. This could be due to polipo's caching, http 1.1 pipelining, and it can serve bits as fast as they come in from the network. Privoxy needs to load the whole page, scan it, and then send it to the client. Even if privoxy filtering is disabled, it still works the same way.
- Polipo caching shines with Tor usage. Performance is still about 40% faster with polipo than privoxy. Common images are cached, and served from the memory cache in single-digit millisecond ranges. Privoxy needs to wait for Tor to wholly deliver the bits. Caching is faster, this we know already. However, from a user perspective, it's just faster to load pages.
- socks5 in Firefox 3.5.2 did better than I expected. It was about twice as slow as polipo, but still twice as fast as privoxy. I chalk this up to the tor circuit variability more than anything else.
- I tried testing a click to a second page to see how much polipo caching helps people reading different pages on the same site. It helps, but not as much as I expected. Polipo ranged from slower than privoxy to 40-100% faster. Too much variability to make a real determination.

Caveats: Testing under tor is highly variable. I used the same circuits for both the polipo and privoxy tests to minimize variability. However, I can't control node load and congestion.

Out of 23 get requests for the Torproject.org/index.html.en, 17 are for the country flags. Perhaps we should load these last at the bottom of the page, or do something else to speed up the torproject page load.

As I was doing this, I kept thinking of other ways to do it better;

- time requests and bits between tor, the http proxy, and the browser. How long does each request take to get from the browser, to the proxy, to tor and back across each layer? how much latency does each piece of software add to the request and delivery?
- automate testing and let it run on a normal tor client over weeks. This will average out tor network variability and show "typical" user experience.
- Pick a sampling of the top 100 websites by visits worldwide and measure their performance with the three methods, fully instrumented as in #1.
- Do user experience measurements. Pay/ask/bribe people to sit in front of a computer, video record their browsing and feedback, and ask for a rating of each configuration (socks5, polipo, privoxy, and a placebo).
- re-run #2 and run gcov to watch the code paths used in each piece of software, and figure out what can be optimized for performance.
- test various "private browsing modes" through tor to see which browser is faster; firefox, safari, chromium, torfox, or torora.
- how can we better tune polipo caching dynamically based on system ram config? Does having 1GB of cache provide significant benefits over the default?

I'm sure there are lots of things wrong with my measurements, minimal analysis, and results.

Constructive criticism is welcome.

