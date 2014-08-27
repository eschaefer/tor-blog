---
layout: post
title: "Whither website translations"
permalink: whither-website-translations
date: 2011-09-28
author: phobos
category: blog
tags: ["bugs", "polyglot internet", "translators", "website translations"]
---

As of [svn commit 25130](https://lists.torproject.org/pipermail/tor-commits/2011-September/035605.html) we no longer have our web pages translated. We continue to translate tor, vidalia, aurora/firefox, our manual pages, and other documentation included with the various bundles. We're also going to create a new, simplified user manual that can be translated and included in our various packages.

I thank our translators, both past and current, and continue to be impressed at the community we've built up around translating all things Tor. We appreciate it, our users appreciate, and I appreciate it.

Why did we do this?

- We spend a lot of time managing the translated pages on the website.
- The English pages are frequently updated, thereby invalidating all of the other languages.
- The switch to [Transifex](https://www.transifex.net/start/) hasn't made more translators appear, especially for the languages we may care about the most.
- The translators for many languages that have a right-to-left orientation complain that the transifex interface is a nightmare to use and refuse to update.
- Lots of users simply use google translate, or read English anyway.
- Getting translated software into the hands of people is more important than them reading our web pages (especially if the documentation is translated and available locally)
- Our translations for right to left languages, such as Arabic and Farsi, were growing out of date and required far more technical skill to do than more translators are capable of handling. This involved editing the raw perl templating system we used.
- And, according to our webserver logs, our translated website traffic is less than 2% of total GET requests, nevermind page views.

We may go back to the old model, which was svn or git commits directly to the repository for translations. It seemed this model attracted a few dedicated translators for some interesting languages. These languages were always kept current with the English pages. Another option is automated translation, such as something Bayesian that understands the difference between the snack cookie and a web browser cookie.

If you have suggestions or other ideas how to improve our translations, feel free to respond to [ticket 4082](https://trac.torproject.org/projects/tor/ticket/4082).

I still look forward to universal translators, helping me to understand the [polyglot Internet](http://www.ethanzuckerman.com/blog/the-polyglot-internet/). There is so much content out there that isn't in languages I understand. I hope universal translators can greatly improve in a short time.

