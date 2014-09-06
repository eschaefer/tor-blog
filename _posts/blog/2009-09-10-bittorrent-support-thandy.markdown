---
layout: post
title: "BitTorrent support for Thandy"
permalink: blog/bittorrent-support-thandy
date: 2009-09-10
author: Sebastian
category: blog
tags: ["BitTorrent", "google", "Google Summer of Code", "gsoc", "thandy"]
---

As a returning [Google Summer of Code](http://socghop.appspot.com/org/home/google/gsoc2009/eff) student for the second year in a row, I was thrilled to hear that I had been accepted again.

My task was to add [BitTorrent](http://www.bittorrent.com/) support to [Thandy](https://git.torproject.org/checkout/thandy/master/), the secure automated updater [developed](http://google-opensource.blogspot.com/2009/03/thandy-secure-update-for-tor.html) by the Tor project, along with setting up and testing the necessary infrastructure. The goal is to better mitigate load spikes following the release of new software versions and allowing volunteers to easily help users to fetch Tor.

Of course, working wasn't without its own challenges. My mentor and I live in different parts of the world, and real-time communication was often difficult to achieve due to timezone differences. Another big challenge was staying motivated during the first month, where university demanded a lot of attention. The situation improved substantially after the mid-term evaluation, when school-related work became less time consuming and I could focus on SoC entirely. During the whole time, I communicated with some of Tor's other SoC students, helping, encouraging and sharing some great laughs with each other. I feel that the community aspect of GSoC worked out much better this year.

During the summer, it became apparent that following through with the original plan of using the [C++ libtorrent implementation by rasterbar](http://www.rasterbar.com/products/libtorrent/index.html) would be difficult, due to various platform-independence issues and a huge resulting binary. Especially the last point made it clear that we wouldn't be able to use that for our netinstaller, one of the most important reasons to develop Thandy. Eventually, I settled on the original BitTorrent implementation, patched by Debian to work around some issues with newer versions of Python.

It was great to see that this year, all my code has been merged into the Thandy source. I think my experience from last year saved me from making the same mistakes again, by focusing on small parts that work instead of re-designing major aspects of the software.

Overall, I'm very happy with how my Summer of Code turned out to be, and I hope to participate again (either as student or even mentor)!

