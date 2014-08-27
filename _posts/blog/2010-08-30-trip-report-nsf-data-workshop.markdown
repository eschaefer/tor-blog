---
layout: post
title: "Trip report, NSF data workshop"
permalink: trip-report-nsf-data-workshop
date: 2010-08-30
author: arma
category: blog
tags: []
---

On Friday (Aug 27), I attended the "Workshop on Cyber Security Data for Experimentation" organized by the National Science Foundation (NSF). The premise of the [workshop](http://www.gtisc.gatech.edu/nsf_workshop10_agenda.html) was that many academics need real-world data sets to solve problems, whereas industry is the place with the real-world data sets and they don't have any real reason to share. By getting the academics and the industry people talking, with government funders nearby, they hoped to better understand the problems and maybe move things forward.

I was there (and on the first panel) because of Tor's work on [gathering Tor network snapshots, performance data, and user statistics](https://metrics.torproject.org/). Tor's approach represents one way out of the trap where researchers never quite get the data they want, or if they do it isn't open enough (which hinders whether anybody else can reproduce their results).

They also asked me to do the wrapup for the workshop. Here are the eight insights that I presented there (with a little bit of commentary from me) -- each of them is a topic that came up during the workshop that I thought warranted more attention.

1) Researchers already have data, it's just not the data they think they want. Either they need to clean / understand / better analyze what they already have, or they need to figure out where they can gather the data themselves (universities sure have lots of users), or they can turn to organizations like PREDICT (or Tor) that are aggregating data sets for the purpose of making them available for researchers.

Too many data sets from industry come with restrictions. At best you'll get your data under some sort of bilateral agreement. Whatever happened to public open data that everybody can look at? After all, often you won't know what you want to look for until you've had some time with the data.

We need to better investigate the intersection of "what we can safely gather in an open way" (i.e. without gathering too many personal details) and "what questions we can answer with it" (if you sanitize the data too far, there's nothing interesting left). I guess the streetlights are brighter over the data sets from antivirus companies, networking companies, etc, so everybody wants to look there. But if it takes multiple years of workshops and everybody's still frustrated, maybe it's time to look at other options?

2) Data preservation questions. When a student moves on, it's common that nobody knows how to continue using what gets left behind. The industry side similarly finds internships too short to be a reliable investment: interns disappear right about the time they start to provide value.

3) Standardized data sets vs specialized data sets. On the one hand, we want standardized public open data sets (think traces for voice recognition), so everybody is doing research from the same starting point. On the other hand, many researchers want to develop specialized data sets to answer new questions -- they find that gathering new data in response to a specific question is a much better strategy. How should we reconcile these conflicting scientific goals?

4) Existing databases need labelling -- for example, if you're looking at a traffic flow and you want to identify what protocols were in use, you need somebody to annotate it with the ground truth (what protocols actually were in use) or you'll never know if your algorithms are producing useful answers. Metadata is critical, but it's expensive to build and maintain. Corporations tend to regard the labelling work as their competitive advantage and keep it to themselves.

5) "Building individual relationships is the only way to get your data." That was a quote from several people on the academia side, and nobody on the industry side disputed it. If you have to spend a few years interacting with the person who controls the data before you have a chance of seeing it, that sure doesn't seem to scale well.

6) "The goal of research is not to write papers. It's to solve problems." That's a quote from the industry side. They regard research that's intellectually interesting as often unrelated to the real-world problems that their company needs to solve. The incentives in academia are structured around publication, and we shouldn't confuse that with actually solving problems.

7) Internal Review Boards (IRBs) are uniformly not equipped to evaluate this sort of research. They ask questions like whether you're going to draw blood from your users (and get answers like "not intentionally, ha ha"). At the same time, there are serious legal, ethical, and technical questions that need to be considered for a lot of these data sets -- both in terms of gathering data and in terms of using data. Academics looking at these issues should check out the [Workshop on the Ethics of Computer Security Research](http://www.cs.stevens.edu/~spock/wecsr2011/).

8) Both sides took the opportunity to ask NSF for money. Some of the academics suggested that NSF could help to cover the cost of interns (one of the most successful ways to get industry data these days is to send one of your students as a "data envoy" for the summer; but as industry research groups tighten their budgets, competition for the remaining slots is increasingly fierce). The industry representatives on the other hand reiterated several times how much more cooperative they could be if somebody gave their shareholders a reason to look at sharing data as anything more than a risk.

Going back to the Tor perspective, there were also some good lessons to be learned from Doug Maughan's lunchtime talk. (Doug was the program manager for the DARPA program that funded Tor back in 2002-2003.) Doug has been coordinating a group called [PREDICT](https://www.predict.org/), which aggregates network operations data sets for security researchers. Despite having many terabytes of data, they're not getting much traction in the research world. Is it because they haven't done a good job marketing what they can offer? Do they need forums to build a community around their data? Do they not have the right data yet? Tor's [metrics and data](https://metrics.torproject.org/) project will be re-encountering these lessons in the coming years, so we should keep an eye on PREDICT.

As a final note, one of the NSF program managers found me afterwards and said that NSF should fund an EAGER (a small two-year grant) to combine a data-mining expert with the Tor data and see what insights can be extracted from it. If you are that data-mining expert, please contact us.

