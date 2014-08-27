---
layout: post
title: "New Firefox 17.0.4esr and Tor 0.2.4.11-alpha bundles"
permalink: new-firefox-1704esr-and-tor-02411-alpha-bundles
date: 2013-03-14
author: erinn
category: blog
tags: ["alpha release", "firefox", "tbb", "tor browser", "tor browser bundle"]
---

We've updated the stable and alpha Tor Browser Bundles with Firefox 17.0.4esr and Tor 0.2.4.11-alpha. These releases have numerous bug fixes and a new Torbutton as well.

[https://www.torproject.org/download](https://www.torproject.org/download "https://www.torproject.org/download")

**Tor Browser Bundle (2.3.25-5)**

- Update Firefox to 17.0.4esr
- Update NoScript to 2.6.5.8
- Update HTTPS Everywhere to 3.1.4
- Fix non-English language bundles to have the correct branding (closes: #8302)
- Firefox patch changes:

  - Remove "This plugin is disabled" barrier

    - This improves the user experience for HTML5 Youtube videos:  
 They "silently" attempt to load flash first, which was not so silent  
 with this barrier in place. (closes: #8312)
  - Disable NoScript's HTML5 media click-to-play barrier (closes: #8386)
  - Fix a New Identity hang and/or crash condition (closes: #6386)
  - Fix crash with Drag + Drop on Windows (closes: #8324)
- Torbutton changes:
  - Fix Drag+Drop crash by using a new TBB drag observer (closes: #8324)
  - Fix XML/E4X errors with Cookie Protections (closes: #6202)
  - Don't clear cookies at shutdown if user wants disk history (closes: #8423)
  - Leave IndexedDB and Offline Storage disabled. (closes: #8382)
  - Clear DOM localStorage on New Identity. (closes: #8422)
  - Don't strip "third party" HTTP auth from favicons (closes: #8335)
  - Localize the "Spoof english" button strings (closes: #5183)
  - Ask user for confirmation before enabling plugins (closes: #8313)
  - Emit private browsing session clearing event on "New Identity"

**Tor Browser Bundle (2.4.11-alpha-1)**

- Update Firefox to 17.0.4esr
- Update Tor to 0.2.4.11-alpha
- Update NoScript to 2.6.5.8
- Update HTTPS Everywhere to 4.0development.6
- Update PDF.js to 0.7.236
- Fix non-English language bundles to have the correct branding (closes: #8302)
- Firefox patch changes:

  - Remove "This plugin is disabled" barrier

    - This improves the user experience for HTML5 Youtube videos:  
 They "silently" attempt to load flash first, which was not so silent  
 with this barrier in place. (closes: #8312)
  - Disable NoScript's HTML5 media click-to-play barrier (closes: #8386)
  - Fix a New Identity hang and/or crash condition (closes: #6386)
  - Fix crash with Drag + Drop on Windows (closes: #8324)
- Torbutton changes:

  - Fix Drag+Drop crash by using a new TBB drag observer (closes: #8324)
  - Fix XML/E4X errors with Cookie Protections (closes: #6202)
  - Don't clear cookies at shutdown if user wants disk history (closes: #8423)
  - Leave IndexedDB and Offline Storage disabled. (closes: #8382)
  - Clear DOM localStorage on New Identity. (closes: #8422)
  - Don't strip "third party" HTTP auth from favicons (closes: #8335)
  - Localize the "Spoof english" button strings (closes: #5183)
  - Ask user for confirmation before enabling plugins (closes: #8313)
  - Emit private browsing session clearing event on "New Identity"

