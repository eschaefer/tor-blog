---
layout: post
title: "November 2009 Progress Report"
permalink: blog/november-2009-progress-report
date: 2009-12-15
author: phobos
category: blog
tags: ["advocacy", "censorship circumvention", "performance", "progress report", "tor in java", "translation"]
---

 **New releases, new hires, new funding**

Bruce Leidl joins to work on developing Tor in Java. Bruce will write a fully functional Tor in Java in order to provide a solid foundation for other java-based projects; such as Tor on mobile platforms like Maemo and Android.

On November 2nd we released Vidalia 0.2.6. [https://blog.torproject.org/blog/vidalia-026-released](https://blog.torproject.org/blog/vidalia-026-released "https://blog.torproject.org/blog/vidalia-026-released")

On November 20th, we released Tor Browser Bundle 1.2.10. [https://blog.torproject.org/blog/tor-browser-bundle-1210-released](https://blog.torproject.org/blog/tor-browser-bundle-1210-released "https://blog.torproject.org/blog/tor-browser-bundle-1210-released")

On November 19th, we released Tor 0.2.2.6-alpha. [https://blog.torproject.org/blog/tor-0226-alpha-released](https://blog.torproject.org/blog/tor-0226-alpha-released "https://blog.torproject.org/blog/tor-0226-alpha-released")

**Design, develop, and implement enhancements that make
Tor a better tool for users in censored countries.**

Roger met with his class at KAIST working on bridge deployment strategies. A few teams developed some creative strategies. Roger is continuing to work with the leading teams to further refine their ideas before publishing.

Improved our email autoresponder, get-tor, to handle non-english character sets. Implemented gettor+(language)@ addressing to allow users to request tor browser bundle packages in their native language. Added support for languages with a right to left orientation, such as farsi.

**Grow the Tor network and user base. Outreach.**

- Andrew spoke at CASCON 2009 about Tor and its research. A few researchers from IBM and University of Waterloo were interested in furthering research. [https://www-927.ibm.com/ibm/cas/cascon/](https://www-927.ibm.com/ibm/cas/cascon/ "https://www-927.ibm.com/ibm/cas/cascon/")
- Andrew and Roger attended Blogfest Asia 2009, HK BloggerCon, and the Privacy and Security Workshop series in Hong Kong and met with many bloggers, activists, and media people from all over Asia. Andrew wrote up his experiences at [https://blog.torproject.org/blog/blogfest-asia-2009](https://blog.torproject.org/blog/blogfest-asia-2009 "https://blog.torproject.org/blog/blogfest-asia-2009").
- Jacob spoke at Internet Dagarna 2009 in Stockholm, Sweden. [http://www.internetdagarna.se/](http://www.internetdagarna.se/ "http://www.internetdagarna.se/")
- Jacob spoke at SUNET gathering in Stockholm, Sweden.
- Jacob helped organize and run Hackers Conference in California. [http://www.think.org/conference/](http://www.think.org/conference/ "http://www.think.org/conference/")
- Karen met with National Iranian-American Council, [http://www.niacouncil.org/](http://www.niacouncil.org/ "http://www.niacouncil.org/"), to discuss ways Tor can help NIAC succeed in helping improve Human Rights and Democracy in Iran.
- Andrew had a conversation with Freedom House which resulted in some instructional videos being produced to help users install and configure Tor. [https://blog.torproject.org/blog/installing-and-using-tor](https://blog.torproject.org/blog/installing-and-using-tor "https://blog.torproject.org/blog/installing-and-using-tor")

**Bridge relay and bridge authority work.**
We distributed bridge addresses to networks of people in China and Iran to let Tor users continue to work without issues.

Karsten worked to remove sensitive data from collected meta-data about bridges. We can publish our bridge data archives to [http://archive.torproject.org](http://archive.torproject.org "http://archive.torproject.org") soon. This data could help understand bridge quantity, usage of bridges around the world, and other information from possible data analysis.

**Scalability, load balancing, directory overhead, efficiency.**

Included in the Tor 0.2.2.6-alpha release is the beginning of microdescriptors.

> Directory authorities can now agree on and publish small summaries of router information that clients can use in place of regular server descriptors. This transition will eventually allow clients to use far less bandwidth for downloading information about the network. Begins the implementation of Proposal 158: ”Clients
> download consensus + microdescriptors”.

**More reliable (e.g. split) download mechanism.**

Continuing to update the email autoresponder, get-tor, to handle split downloads on request. Split Tor Browser Bundles work well. Creation and maintenance of Mac OS X split dmgs is due in December 2009.

**Translation work, ultimately a browser-based approach.**

- Pushed live Runa’s work on integrating the website to our translation portal, [https://translation.torproject.org/](https://translation.torproject.org/ "https://translation.torproject.org/").
- Runa fine tuned the translation portal to website scripts.
- Runa updated the documentation for translators to reflect these tor translation portal updates.
- Added our email autoresponder, get-tor, to the translation portal.
- Began live testing of website translations through the Tor Translation Portal.
- 28 updated Polish website translations.
- 15 updated Chinese website translations.
- 11 updated Italian website translations.
- 1 French translation of get-tor.
- Full Norwegian translation of tor browser bundle.
- Full Norwegian translation of the website.
- Full Burmese translation of the website.
- Full Burmese translation of torcheck.
- Updated Spanish torbutton translations.
- Updated Chinese torbutton translations.
- Updated Chinese torcheck translations.
- 18 updated German website translations.

