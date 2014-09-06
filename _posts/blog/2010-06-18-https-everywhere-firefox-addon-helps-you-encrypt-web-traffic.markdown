---
layout: post
title: "HTTPS Everywhere Firefox addon helps you encrypt web traffic"
permalink: blog/https-everywhere-firefox-addon-helps-you-encrypt-web-traffic
date: 2010-06-18
author: mikeperry
category: blog
tags: ["plaintext communications", "privacy", "tor"]
---

Today the EFF and the Tor Project are launching a public beta of a new Firefox extension called [HTTPS Everywhere](https://eff.org/https-everywhere/).

This Firefox extension was inspired by the launch of Google's encrypted search option. We wanted a way to ensure that every search our browsers sent was encrypted, including the search box and URL bar features. At the same time, we were also able to encrypt most or all of the browser's communications with other popular sites that support SSL, but don't provide it by default.

Our approach is based on the [NoScript STS](http://hackademix.net/2009/09/23/strict-transport-security-in-noscript/) implementation, but is more expressive in the manner in which [HTTPS-enforcing rules are written](https://www.eff.org/https-everywhere/rulesets).

This tends to work more effectively than NoScript because many sites on the web offer some limited support for encryption over HTTPS, but make it difficult to use. For instance, they may not offer all pages and applications via HTTPS, or may only allow HTTPS activity via alternate subdomains that require URL rewriting and redirection. In particular, Google's SSL search and Wikipedia both require rather complex URL rewriting and exception filters to work properly.

HTTPS Everywhere should also perform more securely than DOM-based mechanisms such as the GreaseMoney-based [SSL Certificates Pro](http://userscripts.org/scripts/show/72944) and the Google Chrome-based [KB Enforcer](https://chrome.google.com/extensions/detail/flcpelgcagfhfoegekianiofphddckof?hl=en). These addons perform redirection at the DOM level, which causes many HTTP fetches to leak prior to the redirect to HTTPS.

We currently provide rule sets for Google Search, Wikipedia, Twitter, Facebook, The New York Times, The Washington Post, IxQuick, and many more popular sites. It is also possible to [add user-defined rule files](https://www.eff.org/https-everywhere/rulesets), and/or to submit rules to us for inclusion in future versions.

Note that some of these sites still include a lot of content from third party domains that are not available over HTTPS. As always, if the browser's lock icon is broken or carries an exclamation mark, you may remain vulnerable to adversaries that use active attacks or traffic analysis to compromise your privacy and security.

