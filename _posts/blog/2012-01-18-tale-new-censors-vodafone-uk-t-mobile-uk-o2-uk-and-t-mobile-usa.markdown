---
layout: post
title: "A tale of new censors - Vodafone UK, T-Mobile UK, O2 UK, and T-Mobile USA"
permalink: blog/tale-new-censors-vodafone-uk-t-mobile-uk-o2-uk-and-t-mobile-usa
date: 2012-01-18
author: ioerror
category: blog
tags: ["filtering censorship website tmobile vodafone o2"]
---

The [right to read](http://www.gnu.org/philosophy/right-to-read.html) is a fictional story but it warns of a future that has already started to arrive; it paints a picture where information is controlled with a heavy hand and simply reading, let alone speaking is an extremely dangerous activity. In the words of William Gibson, _"The future is already here — it's just not very evenly distributed"_. Restrictions on the right to read though the Internet perfectly match this observation. A lot should be said about perceptions of censorship, and it is often thought that places like Syria or Iran are unique. Generally, people in the West hold that those countries obviously censor as is consistent with facts of life in a supposedly non-free country. This probably holds a lot of truth but it absolutely fails to address the core of the issue — these countries and those networks are not unique.

In fact, we find uncensored networks to almost be an abnormal state. The so-called free countries in the West often shape and tamper with network traffic. They often also log data and even [collaborate with governments](https://www.eff.org/cases/nsa?tid=534). Generally, people don't see evidence of this and as a result, they often perceive that their Internet connections aren't monitored or censored. These days are quickly coming to an end and while it sounds like hyperbole, here are examples in the United Kingdom and in the United States of America.

Recently it has come to our attention that our [primary website](http://www.torproject.org/) is filtered by Vodafone in the UK, by 3 (three.co.uk) in the UK, by O2 in the UK, and by T-Mobile in the UK and the USA. It used to be the case that we only saw filtering and censorship events in places like Egypt, Syria, or Iran and now we're going to explore what those attacks look like in the context of the UK and the USA.

When a visitor uses a pre-paid account on the T-Mobile USA network and attempts to visit [http://www.torproject.org/](http://www.torproject.org/ "http://www.torproject.org/"), they are redirected to [a block page](https://blog.torproject.org/files/tmobile-pre-paid-censorship_0.png). This is enabled by default without user's affirmative consent and only savvy privileged users may even attempt to disable this censorship. There is an [informational page about the T-Mobile censorship system](http://support.t-mobile.com/docs/DOC-2144) and it explains that this censorship may be disabled. We've heard reports that attempts to disable the censorship are not always successful and this certainly doesn't bode well for an easy and censorship-free Internet experience.

The T-Mobile USA network censorship appears to be simple to bypass: it appears to only trigger when a client sends Host: torproject.org on TCP port 80 and visitors that use [HTTPS](https://www.torproject.org/) will probably not notice or be obviously impacted by their censorship.

This kind of censorship raises all kinds of interesting questions. I suspect it raises US legal and social questions as well. The Tor Project is a registered 501c3 non-profit corporation in the state of Massachusetts, and the block was experienced in California. Does this count as interfering with interstate commerce? What duty of care does T-Mobile USA have when it relies on systems or infrastructure funded by the public? What duty of care do they have as a common carrier?

Similarly, when a user on the UK Vodafone network visits [http://www.torproject.org/](http://www.torproject.org/ "http://www.torproject.org/") they are greeted by [a block page as well](https://blog.torproject.org/files/www.torproject.org-vodafone.png). You can visit this [block page](http://online.vodafone.co.uk/dispatch/Portal/ContentControlServlet?type=restricted) without directly using their networks. Detecting their filters is straightforward and we see tampering at the sixth hop.

Here is a tcptraceroute to TCP port 80 of torproject.org from an Ubuntu machine connected to the Internet via Vodafone UK:
`
Tracing the path to www.torproject.org (86.59.30.36) on TCP port 80 (www), 30 hops max
 1 192.168.1.1 2.379 ms 1.011 ms 1.313 ms
 2 10.252.225.61 90.998 ms 133.672 ms 95.963 ms
 3 10.252.224.186 78.865 ms 91.722 ms 91.415 ms
 4 * * *
 5 10.203.64.130 88.502 ms 73.259 ms 80.765 ms
 6 www.torproject.org (86.59.30.36) [open] 77.927 ms 152.599 ms 96.399 ms
`

Here is a normal traceroute to torproject.org from an Ubuntu machine connected to the internet via Vodafone UK:
`
traceroute to www.torproject.org (86.59.30.36), 30 hops max, 60 byte packets
 1 192.168.1.1 (192.168.1.1) 9.669 ms 9.583 ms 9.460 ms
 2 10.252.225.61 (10.252.225.61) 98.084 ms 98.046 ms 98.224 ms
 3 10.252.224.219 (10.252.224.219) 98.760 ms 109.326 ms 109.261 ms
 4 host203.msm.che.vodafone (10.203.64.154) 109.087 ms 127.554 ms 127.426 ms
 5 * * *
 6 * * *
 7 * * *
 8 * * *
 9 85.205.0.110 (85.205.0.110) 180.920 ms 180.692 ms 180.652 ms
10 85.205.0.109 (85.205.0.109) 180.659 ms 180.473 ms *
11 85.205.116.5 (85.205.116.5) 260.480 ms * 85.205.116.1 (85.205.116.1) 152.107 ms
12 92.79.213.157 (92.79.213.157) 152.265 ms 152.099 ms 151.808 ms
13 92.79.209.210 (92.79.209.210) 151.453 ms 151.124 ms 92.79.203.254 (92.79.203.254) 151.129 ms
14 vin-145-254-19-130.arcor-ip.net (145.254.19.130) 157.978 ms vin-145-254-19-126.arcor-ip.net (145.254.19.126) 119.699 ms 129.820 ms
15 te3-1-vix-iec-c2.ix.sil.at (193.203.0.6) 129.999 ms 136.314 ms 136.338 ms
16 86.59.118.145 (86.59.118.145) 136.033 ms 135.826 ms 135.666 ms
17 www.torproject.org (86.59.30.36) 151.282 ms 118.185 ms 114.603 ms
`

We've additionally found that pre-paid T-Mobile UK accounts also experience censorship that is similar to T-Mobile USA. Detection of their filter is possible with some of the techniques that I've demonstrated, and it is quite trivial to see that TCP port 80 and 443 are treated in a special way.

Here is a tcptraceroute to TCP port 80 of torproject.org from an Ubuntu machine connected to the Internet via T-Mobile UK:
`
Tracing the path to torproject.org (38.229.72.14) on TCP port 80 (www), 30 hops max
 1 * * *
 2 10.126.241.49 305.721 ms 429.908 ms 449.875 ms
 3 10.70.16.221 480.031 ms 339.890 ms 429.951 ms
 4 10.70.17.87 480.447 ms 449.365 ms 439.979 ms
 5 vescum.torproject.org (38.229.72.14) [open] 459.935 ms 659.964 ms 449.849 ms
`

Here is a tcptraceroute to TCP port 443 of torproject.org from an Ubuntu machine connected to the Internet via T-Mobile UK:
`
Tracing the path to torproject.org (86.59.30.36) on TCP port 443 (https), 30 hops max
 1 * * *
 2 10.126.241.53 357.474 ms 360.016 ms 389.772 ms
 3 10.70.16.217 490.136 ms 409.878 ms 359.945 ms
 4 10.70.17.87 469.956 ms 489.883 ms 389.868 ms
 5 www.torproject.org (86.59.30.36) 410.024 ms 420.494 ms 399.888 ms
 6 10.70.17.66 389.470 ms 429.923 ms 339.861 ms
 7 10.70.16.50 430.002 ms 349.850 ms 450.012 ms
 8 10.70.17.103 339.900 ms 389.836 ms 390.031 ms
 9 149.254.199.162 369.851 ms * 924.522 ms
10 10.126.168.218 420.035 ms 379.878 ms 409.968 ms
11 xe-1-3-2-19.lon10.ip4.tinet.net (77.67.73.209) 469.942 ms 480.002 ms 499.940 ms
12 xe-5-3-0.vie20.ip4.tinet.net (89.149.180.6) 399.851 ms 379.892 ms 379.929 ms
13 silver-server-gw.ip4.tinet.net (77.67.82.234) 419.899 ms 479.926 ms 449.923 ms
14 www.torproject.org (86.59.30.36) 389.925 ms 449.789 ms 549.993 ms
15 www.torproject.org (86.59.30.36) [open] 419.869 ms 469.997 ms 479.839 ms
`

Compare with a normal traceroute to torproject.org from an Ubuntu machine connected to the Internet via T-Mobile UK:
`
traceroute to torproject.org (38.229.72.14), 30 hops max, 60 byte packets
 1 * * *
 2 10.126.241.49 (10.126.241.49) 99.671 ms 99.856 ms 159.584 ms
 3 10.70.16.221 (10.70.16.221) 179.672 ms 190.046 ms 159.760 ms
 4 10.70.16.50 (10.70.16.50) 190.250 ms 179.356 ms 90.611 ms
 5 10.70.17.103 (10.70.17.103) 90.565 ms 110.275 ms 90.508 ms
 6 149.254.199.162 (149.254.199.162) 110.476 ms 110.449 ms 110.391 ms
 7 10.126.168.214 (10.126.168.214) 70.022 ms 70.062 ms 60.303 ms
 8 xe-1-3-2-19.lon10.ip4.tinet.net (77.67.73.209) 60.322 ms 69.380 ms 69.383 ms
 9 * * *
10 limelight-lon-gw.ip4.tinet.net (213.200.77.118) 59.798 ms 60.535 ms 179.659 ms
11 tge11-1.fr4.lga.llnw.net (69.28.172.149) 240.999 ms 221.715 ms 221.191 ms
12 tge14-4.fr4.ord.llnw.net (69.28.189.53) 230.570 ms 229.966 ms 210.814 ms
13 tge7-1.fr3.ord.llnw.net (69.28.172.41) 210.575 ms 200.446 ms 199.453 ms
14 ve8.fr3.ord4.llnw.net (68.142.80.130) 169.521 ms 148.181 ms 168.037 ms
15 cymru.tge6-3.fr3.ord4.llnw.net (68.142.73.198) 248.264 ms 229.474 ms 249.066 ms
16 vescum.torproject.org (38.229.72.14) 249.289 ms 249.234 ms 259.448 ms
`

In the examples above we see that T-Mobile UK treats TCP port 80 in a special manner and effectively stops users from reaching our web site. This is an attack against users who attempt to connect to our infrastructure. This attack, while primitive, demonstrates an active and malicious action on the part of the above named Internet providers.

We've additionally seen reports of the UK O2 network blocking connections to [http://www.torproject.org/](http://www.torproject.org/ "http://www.torproject.org/") in exactly the same way that Vodafone UK blocks access. The O2 filter has been covered in the [popular media in the recent past](http://www.wired.co.uk/news/archive/2011-03/04/o2-mobile-web-filtering) and we're sad to hear that they've decided to include Tor's website in their race to the bottom.

In all the above cases we do not see DNS tampering but rather outright [Man-In-The-Middle attacks](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) against connections to our web server. These censorship systems do not currently implement a Man-In-The-Middle attack against the SSL services offered by our web server. It is not much of a stretch of the imagination to think that such an action may be a future plan; we've [seen](https://blog.torproject.org/blog/detecting-certificate-authority-compromises-and-web-browser-collusion) it [elsewhere](https://blog.torproject.org/blog/diginotar-damage-disclosure).

Current users of the Tor network are not impacted by this filtering, but these networks are attempting to deny new users the ability to start using Tor without extensive efforts. You can [view their filter page](https://bango.net/O2AV/wUnsuccessful.aspx?action=sessionTimeout&httpsRedirect=1) without using their service; the [exact block page](https://bango.net/O2AV/mUnsuccessful.aspx?action=noMSISDN&httpsRedirect=1&httpsRedirect=1) is also available externally. It appears that it is possible for users to disable this censorship by providing a credit card as a proof of age. This is not exactly a privacy-friendly tactic. The O2 Twitter account [contacted me](https://twitter.com/#!/O2/status/159560963106947072) and said they were willing to review their censorship policy for torproject.org but they did not offer to remove the censorship entirely.

This trend of providing partially censored Internet in what we all think of as free countries is alarming. Are we supposed to look the other way because the mobile Internet isn't the same as the "real" Internet? Should we worry that Vodafone's capabilities and behavior here remind us of [what they did in Egypt last year](http://www.rawstory.com/rs/2011/01/28/vodafone-confirms-role-egypts-cellular-internet-blackout/)? It would seem that the war over network neutrality is far from won.

(Investigation and research thanks go to Andrew Lewman, Steven Murdoch and Runa Sandvik of the [Tor Project](https://www.torproject.org/), SiNA of [RedTeam LLC](http://www.redteam.io/), Jim Killock, Lee Maguire, Peter Bradwell of the [Open Rights Group](http://www.openrightsgroup.org/) and their project [blocked.org.uk](http://blocked.org.uk/) and Richard Clayton from the [University of Cambridge](http://www.cl.cam.ac.uk/~rnc1/).)

<thead><tr>
<th>Attachment</th>
<th>Size</th> </tr></thead><tbody>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/www.torproject.org-vodafone.png">www.torproject.org-vodafone.png</a></td>
<td>235.81 KB</td> </tr>
 <tr class="even">
<td><a href="https://blog.torproject.org/files/tmobile-pre-paid-censorship_0.png">tmobile-pre-paid-censorship.png</a></td>
<td>317.21 KB</td> </tr>
</tbody>

