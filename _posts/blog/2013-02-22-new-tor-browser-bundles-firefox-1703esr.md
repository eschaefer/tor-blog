---
layout: post
title: "New Tor Browser Bundles with Firefox 17.0.3esr"
permalink: new-tor-browser-bundles-firefox-1703esr
date: 2013-02-22 01:10:49
author: erinn
category: blog
status: closed
tags: ["firefox", "tbb", "tor", "tor browser", "tor browser bundle", "torbutton"]
---

We've updated all of the bundles with Firefox 17.0.3esr. This includes significant changes to Torbutton and its interaction with Firefox, in addition to many new patches being added to Firefox, which are outlined below.

**Very important**: if you've been using the Tor Browser Bundles with Firefox 10.0.x, you must not attempt to overwrite it with the new bundle. Open these into their own directory and do not copy any profile material from older TBB versions.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Tor Browser Bundle (2.3.25-4)**

Update Firefox to 17.0.3esr

Downgrade OpenSSL to 1.0.0k

Update libpng to 1.5.14

Update NoScript to 2.6.5.7

Firefox patch changes:

Exempt remote @font-face fonts from font limits (and prefer them).  
 (closes: [\#8270](https://trac.torproject.org/projects/tor/ticket/8270))

-   Remote fonts (aka "User Fonts") are not a fingerprinting threat, so  
     they should not count towards our CSS font count limits. Moreover,  
     if a CSS font-family rule lists any remote fonts, those fonts are  
     preferred over the local fonts, so we do not reduce the font count  
     for that rule.
-   This vastly improves rendering and typography for many websites.

Disable WebRTC in Firefox build options. (closes: [\#8178](https://trac.torproject.org/projects/tor/ticket/8178))

-   WebRTC isn't slated to be enabled until Firefox 18, but the code  
     was getting compiled in already and is capable of creating UDP Sockets  
     and bypassing Tor. We disable it from build as a safety measure.

Move prefs.js into omni.ja and extension-overrides. (closes: [\#3944](https://trac.torproject.org/projects/tor/ticket/3944))

-   This causes our browser pref changes to appear as defaults. It also  
     means that future updates of TBB should preserve user pref settings.

Fix a use-after-free that caused crashing on MacOS (closes: [\#8234](https://trac.torproject.org/projects/tor/ticket/8234))

Eliminate several redundant, useless, and deprecated Firefox pref settings

Report Firefox 17.0 as the Tor Browser user agent

Use Firefox's click-to-play barrier for plugins instead of NoScript

Set the Tor SOCKS+Control ports to 9150, 9151 respectively on all platforms

-   This fixes a SOCKS race condition with our SOCKS autoport configuration  
     and HTTPS-Everywhere's Tor test. Firefox 17 appears to cache proxy  
     settings per URL now, which resulted in a proxy error for  
     check.torproject.org if we lost the race.

Torbutton was updated to 1.5.0. The following issues were fixed:

-   Remove old toggle observers and related code (closes: [\#5279](https://trac.torproject.org/projects/tor/ticket/5279))
-   Simplify Security Preference UI and associated pref updates (closes: [\#3100](https://trac.torproject.org/projects/tor/ticket/3100))
-   Eliminate redundancy in our Flash/plugin disabling code (closes: [\#1305](https://trac.torproject.org/projects/tor/ticket/1305))
-   Leave most preferences under Tor Browser's control (closes: [\#3944](https://trac.torproject.org/projects/tor/ticket/3944))
-   Disable toggle-on-startup and crash detection logic (closes: [\#7974](https://trac.torproject.org/projects/tor/ticket/7974))
-   Disable/remove toggle-mode code and related observers (closes: [\#5279](https://trac.torproject.org/projects/tor/ticket/5279))
-   Add menu hint to Torbutton icon (closes: [\#6431](https://trac.torproject.org/projects/tor/ticket/6431))
-   Make Torbutton icon flash a warning symbol if TBB is out of date (closes: [\#7495](https://trac.torproject.org/projects/tor/ticket/7495))
-   Perform version check every time there's a new tab. (closes: [\#6096](https://trac.torproject.org/projects/tor/ticket/6096))
-   Rate limit version check queries to once every 1.5hrs max. (closes: [\#6156](https://trac.torproject.org/projects/tor/ticket/6156))
-   misc: Allow WebGL and DOM storage.
-   misc: Disable independent Torbutton updates
-   misc: Change the recommended SOCKSPort to 9150 (to match TBB)

The following Firefox patch changes are also included in this release:

Isolate image cache to url bar domain (closes: [\#5742](https://trac.torproject.org/projects/tor/ticket/5742) and [\#6539](https://trac.torproject.org/projects/tor/ticket/6539))

Enable DOM storage and isolate it to url bar domain (closes: [\#6564](https://trac.torproject.org/projects/tor/ticket/6564))

Include nsIHttpChannel.redirectTo API for HTTPS-Everywhere (closes: [\#5477](https://trac.torproject.org/projects/tor/ticket/5477))

Misc preference changes:

-   Disable DOM performance timers (dom.enable\_performance) (closes: [\#6204](https://trac.torproject.org/projects/tor/ticket/6204))
-   Disable HTTP connection retry timeout (network.http.connection-retry-timeout) (closes: [\#7656](https://trac.torproject.org/projects/tor/ticket/7656))
-   Disable full path information for plugins (plugin.expose\_full\_path) (closes: [\#6210](https://trac.torproject.org/projects/tor/ticket/6210))
-   Disable NoScript's block of remote WebFonts (noscript.forbidFonts) (closes: [\#7937](https://trac.torproject.org/projects/tor/ticket/7937))

**Tor Browser Bundle (2.4.10-alpha-2)**

Update Firefox to 17.0.3esr

Downgrade OpenSSL to 1.0.0k

Update libpng to 1.5.14

Update NoScript to 2.6.5.7

Firefox patch changes:

Exempt remote @font-face fonts from font limits (and prefer them).  
 (closes: [\#8270](https://trac.torproject.org/projects/tor/ticket/))

-   Remote fonts (aka "User Fonts") are not a fingerprinting threat, so  
     they should not count towards our CSS font count limits. Moreover,  
     if a CSS font-family rule lists any remote fonts, those fonts are  
     preferred over the local fonts, so we do not reduce the font count  
     for that rule.
-   This vastly improves rendering and typography for many websites.

Disable WebRTC in Firefox build options. (closes: [\#8178](https://trac.torproject.org/projects/tor/ticket/8178))

-   WebRTC isn't slated to be enabled until Firefox 18, but the code  
     was getting compiled in already and is capable of creating UDP Sockets  
     and bypassing Tor. We disable it from build as a safety measure.

Move prefs.js into omni.ja and extension-overrides. (closes: [\#3944](https://trac.torproject.org/projects/tor/ticket/3944))

-   This causes our browser pref changes to appear as defaults. It also  
     means that future updates of TBB should preserve user pref settings.

Fix a use-after-free that caused crashing on MacOS (closes: [\#8234](https://trac.torproject.org/projects/tor/ticket/8234))

Eliminate several redundant, useless, and deprecated Firefox pref settings

Report Firefox 17.0 as the Tor Browser user agent

Use Firefox's click-to-play barrier for plugins instead of NoScript

Set the Tor SOCKS+Control ports to 9150, 9151 respectively on all platforms

-   This fixes a SOCKS race condition with our SOCKS autoport configuration  
     and HTTPS-Everywhere's Tor test. Firefox 17 appears to cache proxy  
     settings per URL now, which resulted in a proxy error for  
     check.torproject.org if we lost the race.

Torbutton was updated to 1.5.0. The following issues were fixed:

-   Remove old toggle observers and related code (closes: [\#5279](https://trac.torproject.org/projects/tor/ticket/5279))
-   Simplify Security Preference UI and associated pref updates (closes: [\#3100](https://trac.torproject.org/projects/tor/ticket/3100))
-   Eliminate redundancy in our Flash/plugin disabling code (closes: [\#1305](https://trac.torproject.org/projects/tor/ticket/1305))
-   Leave most preferences under Tor Browser's control (closes: [\#3944](https://trac.torproject.org/projects/tor/ticket/3944))
-   Disable toggle-on-startup and crash detection logic (closes: [\#7974](https://trac.torproject.org/projects/tor/ticket/7974))
-   Disable/remove toggle-mode code and related observers (closes: [\#5279](https://trac.torproject.org/projects/tor/ticket/5279))
-   Add menu hint to Torbutton icon (closes: [\#6431](https://trac.torproject.org/projects/tor/ticket/6431))
-   Make Torbutton icon flash a warning symbol if TBB is out of date (closes: [\#7495](https://trac.torproject.org/projects/tor/ticket/7495))
-   Perform version check every time there's a new tab. (closes: [\#6096](https://trac.torproject.org/projects/tor/ticket/6096))
-   Rate limit version check queries to once every 1.5hrs max. (closes: [\#6156](https://trac.torproject.org/projects/tor/ticket/6156))
-   misc: Allow WebGL and DOM storage.
-   misc: Disable independent Torbutton updates
-   misc: Change the recommended SOCKSPort to 9150 (to match TBB)

