---
layout: post
title: "October 2008 Progress Report"
permalink: october-2008-progress-report
date: 2008-12-01 19:43:12
author: phobos
category: blog
status: closed
tags: ["auto-updater", "censorship circumvention", "china", "crashes", "farsi", "torbutton", "translations", "vidalia"]
---

**Design**  
 We continued enhancements to the Chinese and Russian Tor website translations. We also have a second Chinese translator for the website now, so hopefully we will get more prompt translations there. Our Farsi translation from this summer is slowly becoming obsolete; we should solve that at some point.

We added a new "30 second summary" web page for Tor:  
 [https://www.torproject.org/30seconds](https://www.torproject.org/30seconds "https://www.torproject.org/30seconds")  
 and a new "easy download" page since the original is so complex:  
 [https://www.torproject.org/easy-download](https://www.torproject.org/easy-download "https://www.torproject.org/easy-download")

In the upcoming Vidalia 0.2.0 development release:  
 - Support changing UI languages without having to restart Vidalia.  
 - Updated Czech, Polish, Romanian and Turkish translations.

In the upcoming Vidalia 0.1.10 stable release:  
 - Add a prettier dialog for prompting people for their control port password that also includes a checkbox for whether the user wants Vidalia to remember the entered password, a Help button, and a Reset button (Windows only).  
 - Fix a crash bug that occurred when the user clicks 'Clear' in the message log toolbar followed by 'Save All'.  
 - Uncheck the Torbutton options by default in the Windows bundle installer if Firefox is not installed.  
 - Add an Windows bundle installer page that warns the user that they should install Firefox, if it looks like they haven't already done so.

It looks like Australia is soon to be joining the ranks of countries with a nationwide filtering regime:  
 [http://arstechnica.com/news.ars/post/20081016-net-filters-required-for-a...](http://arstechnica.com/news.ars/post/20081016-net-filters-required-for-all-australians-no-opt-out.html "http://arstechnica.com/news.ars/post/20081016-net-filters-required-for-all-australians-no-opt-out.html")

**Proposals**  
 We finished the first iteration of our auto-updater spec:  
 [https://svn.torproject.org/svn/updater/trunk/specs/thandy-spec.txt](https://svn.torproject.org/svn/updater/trunk/specs/thandy-spec.txt "https://svn.torproject.org/svn/updater/trunk/specs/thandy-spec.txt")  
 We detail our current auto-updater progress below. [**read more »**](https://blog.torproject.org/blog/october-2008-progress-report)
