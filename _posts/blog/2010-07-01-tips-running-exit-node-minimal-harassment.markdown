---
layout: post
title: "Tips for Running an Exit Node with Minimal Harassment"
permalink: blog/tips-running-exit-node-minimal-harassment
date: 2010-07-01
author: mikeperry
category: blog
tags: ["anonymity advocacy", "distributed trust", "education", "performance"]
---

 **Updated 06/30/2010** : Mention Reduced Exit Policy, ISP Shopping Tips, and Abuse Response Templates

**Updated 08/30/2010** : Update exit policy with svn, git, hg, Kerberos, remote admin panels, IRC, others

**Updated 01/12/2011** : Suggest creation of LLC for large exit nodes, provide links to ARIN forms and process.

I have noticed that a lot of new exit nodes have recently appeared on the network. This is great news, since exit nodes are typically on the scarce side. Exits usually occupy 30-33% of network by capacity, but are currently at a whopping 38.5% (156 MBytes/sec out of 404 total).

However, I want to make sure that these nodes stay up and don't end up being shut down due to easily preventable abuse complaints. I've run a number of exit nodes on a few different ISPs and not only have I lived to tell about it, I've have not had one shut down yet. Moreover, I've only received about 4 abuse complaints in as many years of running exit nodes. This is in stark contrast to other node operators following a [more reactive strategy](https://blog.torproject.org/blog/five-years-exit-node-operator). I'm convinced this is largely because I observe the following pro-active guidelines. This guide is primarily US centric. Operators in other countries may have slightly different best practices (such as registering with RIPE and not ARIN).

**1. Inform your potential ISP(s)**
In general, running an exit node from your home Internet connection is not recommended, unless you are prepared for increased attention to your home. In the USA, there have been no equipment seizures due to Tor exits, but there have been phone calls and visits. In other countries, people have had all their home computing equipment seized for running an exit from their home internet connection. So you will need to [find a good colo](https://trac.torproject.org/projects/tor/wiki/doc/GoodBadISPs) and save your home connection for bridge or middle node use. Plus, bandwidth will be much cheaper in a colo center anyway.

Pick an ISP you can trust, and let them know exactly what is going on. A good first email is to ask them if they have an [AUP](https://secure.wikimedia.org/wikipedia/en/wiki/Acceptable_use_policy) you can read if you can't find one online. You should also ask them if they can provide the services mentioned below in this document, such as additional IP addresses, [SWIP](https://secure.wikimedia.org/wikipedia/en/wiki/Shared_Whois_Project), and reverse DNS, and if these services might cost extra.

In a follow up email, you should explain Tor to them, and why it is important to the Internet, the world, and to you, their potential customer. Giving them links to our [Tor Users](https://www.torproject.org/torusers.html.en), [Tor Overview](https://www.torproject.org/overview.html.en), [Tor Legal FAQ](https://www.torproject.org/eff/tor-legal-faq.html.en) and [Tor Abuse FAQ](https://www.torproject.org/faq-abuse.html.en) is typically immensely helpful. Mentioning China and the current conflict in Iran are also likely to be helpful. If your ISP is your University, you may also want to peruse [this set of recommendations](https://trac.torproject.org/projects/tor/wiki/doc/TorGuideUniversities) specific to dealing with University administrators.

If your ISP does not approve, all is not lost: you can look into running a middle node, or a much less visible [bridge node](https://www.torproject.org/bridges). It is better to learn this up front, rather than have your Internet connection shut down on you without warning. Exit bandwidth is often scarce, but any node is better than no node.

**2. Get a separate IP for the node. Do not route your own traffic via this IP**
While it may be tempting to mix in your traffic with your node's exit traffic for cover, this is best avoided. Having a separate IP allows your ISP to more easily recognize that abuse complaints and DMCA notices can be forwarded to you to be quickly responded to with a [boilerplate response](https://trac.torproject.org/projects/tor/wiki/doc/TorAbuseTemplates), as opposed to cutting off your Internet access or providing your personal information to the copyright cartels.

**3. Get recognizable Reverse DNS for this IP**
Setting a good reverse DNS name for your exit IP helps to prevent knee-jerk reactions from sysadmins and DoS kiddies alike who run into bad apples coming from your node IP. Something like tor-exit.yourdomain.org or tor-proxy-readme.yourdomain.org is the best bet.

**4. Set up a Tor Exit Notice**
Once you have a good reverse DNS name, you should put some content there that explains what Tor is for those who see the name and try to visit it via http. If you run your DirPort on port 80 with Tor 0.2.1.x or newer, you can use the Tor config option "DirPortFrontPage" to display a notice explaining that you are running an exit node. A sample one is provided in [contrib/tor-exit-notice.html](https://gitweb.torproject.org/tor.git/blob_plain/HEAD:/contrib/operator-tools/tor-exit-notice.html) in the source distribution. This way, when someone sees tor-proxy-readme.yourdomain.org in their logs, they hopefully will get the hint and read the notice before flaming you. Be sure to update the contact info and other places marked with FIXME in the notice.

**5. Get ARIN registration (if possible)**
If you can get your ISP to [SWIP](https://secure.wikimedia.org/wikipedia/en/wiki/Shared_Whois_Project) your IP block to display a contact and abuse email that you control, this can go a long way to reducing aggravation that they may feel from dealing with the occasional abuse complaint, because the vast majority of the few complaints that are still made will go to you instead of them.

Having your own SWIP allocation is so important to your success that it is worth specifically offering to pay the ISP extra for it if they initially refuse. [RWHOIS](https://secure.wikimedia.org/wikipedia/en/wiki/Rwhois#RWhois) is another possibility, but it should be considered a second choice, since most people just check the SWIP record.

To get a proper SWIP record, you should first [create an account at ARIN](https://www.arin.net/public/register_1.xhtml) and create [POC handles](https://www.arin.net/public/secure/poc/create/begin.xhtml) and the [ORG IDs](https://www.arin.net/public/secure/org/create/orgInfo.xhtml) for yourself. You must then get your ISP to submit a [resource request template](https://www.arin.net/resources/request.html) that references your POC handles and ORG IDs.

Templates at ARIN change periodically, so some ISPs may be reluctant to do the paperwork for you if it means changing their submission scripts. Again, offering to pay for this service is a good idea, if they initially stall or refuse.

**6. Consider a Reduced Exit Policy**
If your node is in the USA, you should consider using a reduced exit policy. Excessive bittorrent abuse over Tor unfortunately means you will likely receive a deluge of DMCA abuse complaints. We (including the very smart lawyers at [the EFF](https://www.eff.org)) believe Tor nodes qualify as [transmission providers under DMCA 512(a)](http://www.chillingeffects.org/dmca512/faq.cgi#QID564), not 512(c). This makes them exempt from "notice and takedown" procedures, including the need to issue "putback" responses. The EFF has even prepared a [template response for improper DMCA 512(c) takedown notices](https://www.torproject.org/eff/tor-dmca-response.html) that you can use.

However, your ISP may see things differently. If the abuse complaints are arriving in their staff's inbox, they may just want them to stop coming so they do not have to spend resources dealing with them, regardless of their merit. If they still won't provide SWIP registration, you can try a reduced exit policy. Other operators have had great success with [using a reduced exit policy](https://trac.torproject.org/projects/tor/wiki/doc/ReducedExitPolicy) consisting of ports 20-23, 43, 53, 79-81, 88, 110, 143, 194, 220, 443, 464-465, 543-544, 563, 587, 706, 749, 873, 902-904, 981, 989-995, 1194, 1220, 1293, 1500, 1723, 1863, 2082-2083, 2086-2087, 2095-2096, 3128, 3389, 3690, 4321, 4643, 5190, 5050, 5222-5223, 5900, 6666-6667, 6679, 6697, 8000, 8008, 8080, 8087-8088, 8443, 8888, 9418, 9999, 10000, and 19638. In fact, the operator of 4 of our fastest exit nodes [has reported](http://archives.seul.org/or/talk/Jun-2010/msg00149.html) that after switching to this policy from the default, the bittorrent DMCA complaints ceased immediately.

With that list, the only abuse complaints you should see will come from occasional comment spam (ports 80 and 443), email spam to misconfigured email servers (port 465 and 587 are supposed to be for authenticated SMTP only), and misconfigured NNTP servers (port 563 is authenticated NNTPS). You may want to review [Moritz Bartl's abuse complaint template set](http://www.wiredwings.com/wiki/Torservers.net_Main_Page#Abuse), as well as the [Tor Abuse Template set](https://trac.torproject.org/projects/tor/wiki/doc/TorAbuseTemplates), and the [Tor Abuse FAQ](https://www.torproject.org/faq-abuse.html.en#TypicalAbuses) for information on how to handle these rare cases, when they do come up.

**7. Rate limit and optionally QoS your node**
I've recently conducted [some measurements](https://blog.torproject.org/blog/torflow-node-capacity-integrity-and-reliability-measurements-hotpets) that showed that nodes that used Tor's BandwidthRate config option to set a limit slightly below their actual capacity were much more reliable than those that did not. Along these lines, it may also be useful to use this [Linux-based QoS script](https://gitweb.torproject.org/tor.git/blob_plain/HEAD:/contrib/linux-tor-prio.sh) to prioritize your Tor IP traffic below other traffic on your machine. Similar QoS can also be achieved via [DDWRT](http://www.dd-wrt.com/), [openwrt](http://openwrt.org/) and of course via commercial routers. If you do use QoS other than that script, you should ensure that you provide Tor with a reasonable minimum bandwidth so that it does not starve when you do other things. Somewhere between 33 and 50% of your connection is a reasonable minimum value.

**8. Consider creating an LLC to run your node**
If you are a [high capacity exit node operator](http://www.mail-archive.com/or-talk@freehaven.net/msg14159.html), you should consider forming an LLC or similar corporate entity for several reasons.

First, as a high capacity exit node, you may wish to [collect donations](http://www.torservers.net/donate.html) from others who are unable to run exits themselves but would still like to support the effort. Creating a separate entity with a separate bank account is a really wise idea once outside money becomes involved.

Second, corporate entities provide you with some level of shielding against headaches. Typically, you are required to list a legal representative to act on your behalf to accept legal service and to answer complaints (an Agent for Service of Process). In the United States, this point of contact is the only public piece of information you are required to give anyone about your corporate entity. This point of contact doesn't have to be you, and organizations exist to provide this service at nominal fees ($50/yr). This means that if someone decides to pay a visit, they are visiting this publicly listed legal point of contact, as opposed to your home.

Third (but related to the above), a corporate entity immediately implicitly signals that you are legally savvy and not easily intimidated by empty legal threats. For example: for some reason, some companies see legal threats as better solutions to crawling abuse than say, [implementing a captcha](https://code.google.com/apis/recaptcha/intro.html). No one has yet brought suit against any Tor operator, but having a corporate entity as that operator tells any potential trigger-happy litigants that you are not likely to be easy pickings.

In the US, the cost of setting up an LLC with good privacy protections is between $100-$1000/yr, depending upon the state you incorporate in and the services you contract from independent providers (such as preparing and filing the paperwork for you, and phone+mail forwarding). States that have laws that make this process easy are Nevada, New Mexico, Wyoming, Montana, and to a lesser extent Delaware. States to avoid include Massachusetts and California (though the latter cannot be avoided if your ISP is also in California -- you must pay a $900 'franchise fee' to CA if you do most of your business there, regardless of incorporation).

You do not have to be a resident of a state to incorporate there. In fact, in most of the states listed above, you do not even have to be a US citizen. It is also never too late to switch your existing exit nodes from your personal control into the hands of a newly formed LLC. All you need to do is inform your ISP, and have the newly formed LLC begin paying the bill from its bank account.

We do not want to recommend specific services here, because we have not personally used them all, but full-service remote incorporation services for those states are easy to find on the web.

That's it! Happy operating!

