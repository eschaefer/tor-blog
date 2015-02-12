---
layout: post
title: "Some thoughts on Hidden Services"
permalink: blog/some-thoughts-on-hidden-services
date: 2014-12-30
author: nickm
category: blog
tags: ["analysis","hidden services","media","philosophy"]
---

Hi! Nick here.

I ought to post my own responses to that Andy Greenberg article, too. (Especially since most everybody else around here is at [31c3](http://events.ccc.de/congress/2014/wiki/Static:Main_Page) right now, or sick with the flu, or both.)

When I saw the coverage of the hidden services study that was presented at CCC today, I was reminded of the media fallout from that old study from the 1990s that "proved" that a ridiculously high fraction of the internet was pornography...by looking at [Usenet](http://en.wikipedia.org/wiki/Usenet)\*, and by counting newsgroups and bytes. (You might remember it; it was the basis of the delightful TIME Magazine ["Cyberporn" cover](http://content.time.com/time/covers/0,16641,19950703,00.html).)

The 1990s researcher wasn't lying outright, but he and the press \*were\* conflating one question: "What fraction of Usenet groups are 'alt.sex' or 'alt.binaries' (file posting) groups" with two others: "What fraction of internet traffic is porn?" and "What fraction of internet-user hours are spent on porn?"

These are quite different things.

The presentation today focused on data about hidden service types and usage. Predictably, given the results from [Biryukov, Pustogarov, Thill, and Weinmann](http://arxiv.org/pdf/1308.6768v2.pdf), the researcher found that hidden services related to child abuse are only a small fraction of the total number of hidden service addresses on the network. And because of the way that hidden services work, traffic does not go through hidden service directories, but instead through [rendezvous points](https://gitweb.torproject.org/torspec.git/tree/rend-spec.txt) (randomly chosen Tor nodes): so no relay that knows the hidden service's address will learn the actual amount of traffic transmitted. But, as previously documented, abusive services represent a disproportionate fraction of usage... if you're measuring usage with hidden service directory requests.

Why might that be?

First, some background. Basically, a Tor client makes a hidden service directory request the first time it visits a hidden service that it has not been to in a while. (If you spend hours at one hidden service, you make about 1 hidden service directory request. But if you spend 1 second each at 100 hidden services, you make about 100 requests.) Therefore, obsessive users who visit many sites in a session account for many more of the requests that this study measures than users who visit a smaller number of sites with equal frequency.

There are other confounding factors as well. Due to bugs in older Tor implementations, a hidden service that is unreliable (or completely unavailable) will get many, many more hidden service directory requests than a reliable one. So if any abuse sites are unusually unreliable, we'd expect their users to create a disproportionately large number of hidden service directory requests.

Also, a very large number of hidden service directory requests are probably not made by humans! See [bug 13287](https://trac.torproject.org/projects/tor/ticket/13287): We don't know what's up with that. Could this be caused by some kind of anti-abuse organization running an automated scanning tool?

In any case, a methodology that looks primarily at hidden service directory requests will over-rate services that are frequently accessed from a Tor client that hasn't been there recently, and under-rate services that are used via [tor2web](https://tor2web.org/), and so on. It also depends a lot on how hidden services are configured, how frequently Tor hidden service directories go up and down, and what times of day they change introduction points in comparison to what time of day their users tend to be awake.

The greater the number of distinct hidden services a person visits, and the less reliable those sites are, the more hidden service directory requests they will trigger.

Suppose 10 people use hidden services to look at conspiracy theories, 100 people use hidden services to buy Cuban cigars, and 1000 people use it for online chat.

But suppose that the average cigar purchaser visits only one or two sites to make purchases, and the average chat user joins one or two networks, whereas the average conspiracy theorist needs to visit several dozen forums and wikis.

Suppose also that the average Cuban cigar purchaser makes about two purchases a month, the average chat user logs in once a day, and the average conspiracy theorist spends 3 hours a day crawling the hidden web.

And suppose that conspiracy theory websites come and go frequently, whereas cigar sites and chat networks are more stable.

In this analysis, even though there are far more people buying cigars, users who use it for obsessive behavior that spans multiple unreliable hidden services will be far overrepresented in the count of hidden service directory requests than users who use it for activities done less frequently and across fewer services. So any comparison of hidden service directory request counts will say more about the behavioral differences of different types of users than about their relative numbers, or the amount of traffic they generated.

In conclusion, let's spend a minute talking about freedom and philosophy. Any system that provides security on the Internet will inevitably see some use by bad people that we'd rather not help at all. After all, cars are used for getaways, and window shades conceal all kinds of criminality. The only way to make a privacy tool that nobody abuses is to make it so weak that people aren't willing to touch it, or so unusable that nobody can figure it out.

Up till now, many of the early adopters for Tor hidden services have been folks for whom the risk/effort calculations have been quite extreme, since--as I'd certainly acknowledge--the system isn't terribly usable for the average person as it stands. Roger noted earlier that hidden services amount to less than 2% of our total traffic today. Given their privacy potential, I think that's not even close to enough. We've got to work over the next year or more to develop hidden services to the point where their positive impact is felt by the average netizen, whether they're publishing a personal blog for their friends, using a novel communications protocol more secure than email, or reading a news article based on information that a journalist received through an anonymous submission system. Otherwise, they'll remain a target for every kind of speculation, and every misunderstanding about them will lead people to conclude the worst about privacy online. [Come lend a hand?](https://blog.torproject.org/blog/hidden-services-need-some-love)

(Also, no offense to Andy on this: he is a fine tech reporter and apparently a fine person. And no offense to Dr. Owen, who explained his results a lot more carefully than they have been re-explained elsewhere. Now please forgive me, I'm off to write some more software and get some sleep. Please direct all media inquiries to the email of "press at torproject dot org".)

\* Usenet was sort of like Twitter, only you could write paragraphs on it. ;)
