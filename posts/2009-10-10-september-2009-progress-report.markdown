---
layout: post
title: "September 2009 Progress Report"
permalink: september-2009-progress-report
date: 10/10/2009
author: phobos
category: blog
tags: ["advocacy", "bug fixes", "censorship circumvention", "china", "doj", "fbi", "iran", "performance improvements", "senators"]
---

Here's what the Tor Project accomplished in September 2009.

**New Hires**

- Carolyn Anhalt is our new Translation and Community Manager. Carolyn has years of experience managing and growing content translation, as well as wrangling online communities and developing volunteer moderators and support roles from the community. She’s fluent or conversant in a number of languages, such as: Russian, French, English, German, Italian, and Welsh. Carolyn’s initial goals are to grow the translator community to keep everything Tor translated, work out better translation tools for translators, and to generally assist translators.
- Karen Reilly joins us as our Development Director. Karen has years of experience in growing both community-based and foundation-based funding, as well as helping to fulfill the mission of organizations through outreach and community-building. Karen’s initial goals are to further develop community funding, work with our current donors, help create an annual report, and expand Tor’s outreach efforts.

**New Funding**

- Tor and Drexel University receive a grant from the National Science Foundation to research “Privacy-preserving measurements of the Tor network to improve performance and anonymity”.
- Tor and ITT receive a grant from the Naval Research Laboratory to research “Tor Networks Trust-Based Routing Research & Design Support”.

**New Releases**

- On September 23rd, we released Tor version 0.2.2.3-alpha. [https://blog.torproject.org/blog/tor-0223alpha-released](https://blog.torproject.org/blog/tor-0223alpha-released "https://blog.torproject.org/blog/tor-0223alpha-released")
- On September 21, we released Tor version 0.2.2.2-alpha. [https://blog.torproject.org/blog/tor-0222alpha-released](https://blog.torproject.org/blog/tor-0222alpha-released "https://blog.torproject.org/blog/tor-0222alpha-released")
- On September 7, we released Vidalia 0.2.4. [https://blog.torproject.org/blog/vidalia-024-released](https://blog.torproject.org/blog/vidalia-024-released "https://blog.torproject.org/blog/vidalia-024-released")
- On September 11, we released Tor Browser Bundle version 1.2.9. [https://blog.torproject.org/blog/tor-browser-bundle-129-released](https://blog.torproject.org/blog/tor-browser-bundle-129-released "https://blog.torproject.org/blog/tor-browser-bundle-129-released")

**Design, develop, and implement enhancements that make  
Tor a better tool for users in censored countries.**

- Jacob Appelbaum and Nathan Frietas developed a fully functional Tor for the Android mobile operating system. It is currently being tested before being released to the Android Marketplace. This Android application uses mainline Tor as written in C, rather than porting/creating a Tor client in Java. Others have started discussions and coding around using Java to create a Tor-compatible client. A new mailing list was created to encourage this community to grow, [http://archives.seul.org/tor/java/](http://archives.seul.org/tor/java/ "http://archives.seul.org/tor/java/").
- Damian Johnson further developed arm, [https://svn.torproject.org/svn/arm/trunk/](https://svn.torproject.org/svn/arm/trunk/ "https://svn.torproject.org/svn/arm/trunk/"). Arm is a command line application for monitoring Tor relays, providing real time status information such as the current configuration, bandwidth usage, message log, connections, etc. This uses a curses interface much like ’top’ does for system usage. The application is intended for command-line aficionados, ssh connections, and anyone stuck with a tty terminal for checking their relay’s status.
- Added two new Tor website and software distribution mirrors. Update list of current mirrors to reflect their current status of how current the mirrors are compared to the main torproject.org website.

**Architecture and technical design docs for Tor enhancements  
related to blocking-resistance.**

- A paper entitled, “On the risks of serving whenever you surf: Vulnerabilities in Tor’s blocking resistance design”, discussing risks in running a bridge is to be relased at Workshop on Privacy in the Electronic Society (WPES 2009), [http://freehaven.net/anonbib/#wpes09-bridge-attack](http://freehaven.net/anonbib/#wpes09-bridge-attack "http://freehaven.net/anonbib/#wpes09-bridge-attack").
- Started development of “marco” to quickly scan for Tor relay and brige reachability from a client machine. This utility was used successfully by volunteers inside Iran and China to determine how much of the Tor network is blocked and how such blocking is occurring.

**Outreach and Advocacy**

- Roger, Paul Syverson, and Andrew gave a Tor lecture to the US Federal Bureau of Investigation Operational Technology Division as part of their quarterly series of talks on new technology. Had a follow-on conversation with a Supervisory Special Agent about how to use Tor tools safely in the field.
- Roger and Andrew had a meeting with the US Department of Justice Child Exploitation and Obscenity Section to present what Tor is and how it works. We also discussed issues and challenges in their usage of, and prosecuting criminals using, Tor.
- Roger and Andrew met with a Senior Policy Advisor from Senator Harry Reid’s office to discuss online privacy and anonymity.
- Roger is working with a freshman class at KAIST in South Korea to develop Tor bridge relay distribution strategies. More information can be found at [https://blog.torproject.org/blog/bridge-distribution-strategies](https://blog.torproject.org/blog/bridge-distribution-strategies "https://blog.torproject.org/blog/bridge-distribution-strategies").

**Preconfigured privacy (circumvention) bundles for USB or LiveCD.**

- On September 11, we released Tor Browser Bundle version 1.2.9. [https://blog.torproject.org/blog/tor-browser-bundle-129-released](https://blog.torproject.org/blog/tor-browser-bundle-129-released "https://blog.torproject.org/blog/tor-browser-bundle-129-released")

**Bridge relay and bridge authority work.**

- Deployed a temporary workaround for a vidalia/tor bug where bridges don’t work if you provide a fingerprint and the bridge authority is unreachable. Discovered this bug on September 25 when China blocked the bridge authority.
- Started fixing bridge statistics that have been broken in all 0.2.2.x versions. Plan to test the fixes in the next few days and include the changes in 0.2.2.5-alpha.

**Scalability, load balancing, directory overhead, efficiency.**

- A research paper on scaling our directory design, “Scalable onion routing with Torsk” is to be presented at CCS 2009, [http://freehaven.net/anonbib#ccs09-torsk](http://freehaven.net/anonbib#ccs09-torsk "http://freehaven.net/anonbib#ccs09-torsk").
- Deployed Mike Perry’s Bandwidth Authority code to the Directory Authorities. The bandwidth authorities are now voting on measured bandwidth from relays and giving out this information in extra-info fields to Tor clients. Tor 0.2.1 and 0.2.2 clients make routing decisions based on these extra-info data. This should spread traffic across relays and improve overall performance of the Tor network.
- Included the results of Mike’s bandwidth scanner in the votes of gabelmoo. Helped evaluating the (impressive) performance improvements as seen by torperf, [https://git.torproject.org/checkout/metrics/master/report/performance/to...](https://git.torproject.org/checkout/metrics/master/report/performance/torperf-2009-09-22.pdf "https://git.torproject.org/checkout/metrics/master/report/performance/torperf-2009-09-22.pdf"). Initial results imply a 30-50% increase in performance.
- Evaluated how the reduction of circuit windows from 1000 to 101 cells affects performance. The last report includes 40 KiB, 50 KiB, and 1 MiB downloads, [https://git.torproject.org/checkout/metrics/master/report/circwindow/cir...](https://git.torproject.org/checkout/metrics/master/report/circwindow/circwindow-2009-09-20.pdf "https://git.torproject.org/checkout/metrics/master/report/circwindow/circwindow-2009-09-20.pdf").
- Evaluated how Mike’s buildtimes patch influences Tor performance, [https://git.torproject.org/checkout/metrics/master/report/buildtimes/bui...](https://git.torproject.org/checkout/metrics/master/report/buildtimes/buildtimes-2009-09-22.pdf "https://git.torproject.org/checkout/metrics/master/report/buildtimes/buildtimes-2009-09-22.pdf").
- Wrote a script that parses descriptor archives to tell whether an IP address was a Tor relay at a given time, [https://svn.torproject.org/svn/projects/archives/trunk/exonerator/HOWTO](https://svn.torproject.org/svn/projects/archives/trunk/exonerator/HOWTO "https://svn.torproject.org/svn/projects/archives/trunk/exonerator/HOWTO").
- Restarted the autonaming script on September 20, so that gabelmoo will be naming relays again soon.
- Fixed the remaining bugs in the proposal 166 implementation. Relays can now include their statistics in extra-info descriptors. Further testing this on select relays for a few more days. Soon will ask people on or-dev to turn on statistics as soon as tests are successful and 0.2.2.4-alpha is out.

**Translation work, ultimately a browser-based approach.**

- Released Runa’s code to allow website translation from our Translation Portal, [https://translation.torproject.org](https://translation.torproject.org "https://translation.torproject.org"). Runa wrote up her ideas and Google Summer of Code experiences at [http://blog.torproject.org/blog/website-translation-support-translationt...](http://blog.torproject.org/blog/website-translation-support-translationtorprojectorg "http://blog.torproject.org/blog/website-translation-support-translationtorprojectorg").
- Continued work on website to translation portal code.
- 17 Polish website updates.
- 27 Italian website updates.
- Romanian and Chinese updates to the check.torproject.org website.
- 1 update to German torbutton translation.
- 23 updates to Romanian torbutton translation.
- 115 updates to Polish torbutton translation.
- 115 updates to Mandarin Chinese torbutton translation.

