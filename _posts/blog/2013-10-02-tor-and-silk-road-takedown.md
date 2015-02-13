---
layout: post
title: "Tor and the Silk Road takedown"
permalink: tor-and-silk-road-takedown
date: 2013-10-02 20:36:37
author: arma
category: blog
status: closed
tags: ["download warnings", "fbi", "hidden services", "operational security", "silk road", "tor"]
---

We've had several requests by the press and others to talk about the Silk Road situation today. We only know what's going on by reading the same news sources everyone else is reading.

In this case we've been watching carefully to try to learn if there are any flaws with Tor that we need to correct. So far, nothing about this case makes us think that there are new ways to compromise Tor (the software or the network). The FBI says that their suspect made mistakes in operational security, and was found through actual detective work. Remember: Tor does not anonymize individuals when they use their legal name on a public forum, use a VPN with logs that are subject to a subpoena, or provide personal information to other services. See also the [list of warnings linked from the Tor download page](https://www.torproject.org/download/download#warning).

Also, while we've seen no evidence that this case involved breaking into the webserver behind the hidden service, we should take this opportunity to emphasize that Tor's hidden service feature (a way to publish and access content anonymously) won't keep someone anonymous when paired with unsafe software or unsafe behavior. It is up to the publisher to choose and configure server software that is resistant to attacks. Mistakes in configuring or maintaining a hidden service website can compromise the publisher's anonymity independent of Tor.

And finally, Tor's design goals include preventing even The Tor Project from tracking users; hidden services are no different. We don't have any special access to or information about this hidden service or any other. Because Tor is open-source and it comes with detailed design documents and research papers, independent researchers can verify its security.

Here are some helpful links to more information on these subjects:

Technical details of hidden services:  
 [https://www.torproject.org/docs/hidden-services](https://www.torproject.org/docs/hidden-services "https://www.torproject.org/docs/hidden-services")

Our abuse FAQ:  
 [https://www.torproject.org/docs/faq-abuse](https://www.torproject.org/docs/faq-abuse "https://www.torproject.org/docs/faq-abuse")

For those curious about our interactions with law enforcement:  
 [https://blog.torproject.org/category/tags/law-enforcement](https://blog.torproject.org/category/tags/law-enforcement "https://blog.torproject.org/category/tags/law-enforcement")  
 [https://www.torproject.org/docs/faq\#Backdoor](https://www.torproject.org/docs/faq#Backdoor "https://www.torproject.org/docs/faq#Backdoor")

Using Tor hidden services for good:  
 [https://blog.torproject.org/blog/using-tor-good](https://blog.torproject.org/blog/using-tor-good "https://blog.torproject.org/blog/using-tor-good")

Regarding the Freedom Hosting incident in August 2013, which is unrelated  
 as far as we can tell:  
 [https://blog.torproject.org/blog/hidden-services-current-events-and-free...](https://blog.torproject.org/blog/hidden-services-current-events-and-freedom-hosting "https://blog.torproject.org/blog/hidden-services-current-events-and-freedom-hosting")

Some general hints on staying anonymous:  
 [https://www.torproject.org/about/overview\#stayinganonymous](https://www.torproject.org/about/overview#stayinganonymous "https://www.torproject.org/about/overview#stayinganonymous")

The Tor Project is a nonprofit 501(c)(3) organization dedicated to providing tools to help people manage their privacy on the Internet. Our focus continues to be in helping ordinary citizens, victims of abuse, individuals in dangerous parts of the world, and [others](https://www.torproject.org/about/torusers) stay aware and educated about how to keep themselves secure online.

The global Tor team remains committed to building technology solutions to help keep the doors to freedom of expression open. We will continue to watch as the details of this situation unfold and respond when it is appropriate and useful.

For further press related questions please contact us at [execdir@torproject.org](mailto:execdir@torproject.org).
