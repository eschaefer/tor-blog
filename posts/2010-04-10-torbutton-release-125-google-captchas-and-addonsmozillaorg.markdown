---
layout: post
title: "Torbutton Release 1.2.5, Google Captchas, and addons.mozilla.org"
permalink: torbutton-release-125-google-captchas-and-addonsmozillaorg
date: 04/10/2010
author: mikeperry
category: blog
tags: ["captchas", "data retention", "firefox", "google", "logging", "mozilla", "torbutton"]
---

Torbutton 1.2.5 has been released. You can download it from [the torbutton homepage](https://www.torproject.org/torbutton/). It has also been submitted to [addons.mozilla.org](https://addons.mozilla.org/en-US/firefox/addon/2275/), though it may take a while for Mozilla to review the addon.

In addition to the numerous bug fixes mentioned in the [changelog](https://gitweb.torproject.org//torbutton.git?a=blob;hb=HEAD;f=src/CHANGELOG), one of the new features of this release is to provide the ability to automatically redirect to an alternate search engine when Google presents you with a captcha. The current options are [IxQuick](https://www.ixquick.com), [Bing](http://www.bing.com), [Yahoo](http://search.yahoo.com), and [Scroogle](https://ssl.scroogle.org). Since it supports SSL, and appears to have a [progressive stance on user privacy](https://www.ixquick.com/eng/protect-privacy.html), IxQuick is the current default.

For those unaware, Google's search engine has rate limiting features that cause it to [present captchas](http://googleonlinesecurity.blogspot.com/2007/07/reason-behind-were-sorry-message.html) and sometimes even outright ban IP addresses that issue large numbers of search queries, especially if some of these queries appear to be searching for software vulnerabilities or unprotected comment areas.

The Tor Project has had multiple discussions with Google over the past 2 years about potential workarounds on either Torbutton or Google's side to reduce the number of captchas and ban pages presented to Tor users while issuing normal natural language queries.

Unfortunately, we were unable to come to a solution or any form of compromise that would reduce the number of captchas and outright bans seen by regular Tor users. We hope that this workaround will enhance the experience of Tor users while still allowing them to use Google for queries that don't result in a ban.

In addition, potentially identifying information (such as language, OS version, and Firefox version) will be stripped off of Google Search Box queries by default. This was a major problem for users of Debian and Ubuntu, which have decided to augment their rebranded Firefox implementations to provide an excessive amount of information to Google for some reason.

Furthermore, this release will also only update Torbutton via Tor by default to address concerns with the data retention policies of [addons.mozilla.org](https://addons.mozilla.org/), as well as to prevent censored users from being revealed as Tor users during the Torbutton update download, which happens over http.

While Mozilla does have a [blanket privacy policy](http://www.mozilla.com/en-US/privacy-policy.html) covering all of their websites, they currently do not have a clear data retention or sanitization policy on [data that is collected and retained](https://addons.mozilla.org/en-US/statistics/addon/2275) during the use of addons.mozilla.org and during the addon update process. Mozilla has informed us that they are working hard to improve their practices and develop a good privacy and data retention policy specific to addons.mozilla.org. However, until such a policy emerges, we have decided that it is best to ensure that Tor users' privacy is protected during the update process via the use of our network.

Data retention concerns aside, the fact that addon update downloads are performed over HTTP can allow censorship regimes to detect the Torbutton download, and to prevent it from happening. For the safety of our censored users, these updates must happen over Tor by default until Mozilla also supports SSL for its addon update downloads. The integrity of the addon is verified by downloading a SHA1 hash over SSL, so this approach should not expose users to exit node tampering.

We have investigated having Torbutton only update via our servers, but this is infeasible for three reasons. First, censored users often cannot reach our servers, so they would be forced to use Tor anyway to safely update. Second, addons hosted on addons.mozilla.org are not permitted to provide a custom update url, so we would have to maintain two versions, or delist Torbutton from that site. Third, future versions of Firefox are expected to ping addons.mozilla.org anyway for statistics gathering purposes.

The unfortunate side effect is that performing these updates via Tor likely also means that the count of Torbutton users on the addons.mozilla.org site will gradually tend downward, and the Torbutton addon will be listed lower in response to searches on the site, since it will appear that we only have a number of users equal to the number of Tor exit nodes once everyone has upgraded.

Not a lot of cheerful news, but as always, we're doing our best to work with what we have.

The complete changelog for this release is as follows:

- bugfix: bug 1169: Fix blank popup conflict with CoolPreviews
- bugfix: bug 1246: Fix IST and other HH:30 timezone issues.
- bugfix: bug 1219: Fix the toggle warning loop issue on settings change.
- bugfix: bug 1321: Fix a session restore bug when closing the last window
- bugfix: bug 1302: Update useragent to FF3.6.3 on WinNT6.
- bugfix: bug 1157: Add logic to handle torbutton crashed state conflicts
- bugfix: bug 1235: Improve the 'changed-state' refresh warning message
- bugfix: bug 1337: Bind alert windows to correct browser window
- bugfix: bug 1055: Make the error console the default log output location
- bugfix: bug 1032: Fix an exception in the localhost proxy filter
- misc: Always tell a website our window size is rounded even if it's not
- misc: Add some suggestions to warning about loading external content
- new: Add option to always update Torbutton via Tor. On by default
- new: Redirect Google queries elsewhere on captcha (default ixquick)
- new: Strip identifying info off of Google searchbox queries

