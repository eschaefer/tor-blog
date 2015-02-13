---
layout: post
title: "Ahmia search after GSoC development"
permalink: ahmia-search-after-gsoc-development
date: 2014-09-07 22:35:23
author: juha
category: blog
status: closed
tags: ["ahmia", "ahmia.fi", "crawling", "GSoC 2014", "hidden services", "onion", "search engine"]
---

The Google Summer of Code (GSoC) was an excellent opportunity to improve on the Ahmia search engine. With Google's stipend and friendly mentoring from The Tor Project, I was able to concentrate on development of my search engine project. Thank you all!

[GSoC 2014](https://trac.torproject.org/projects/tor/wiki/doc/gsoc) is over, but I am sticking around to continue developing and maintaining Ahmia.

Here is the current status of ahmia after GSoC development:

Introduction
------------

Ahmia is [open-source search engine software](https://github.com/juhanurmi/ahmia/) for Tor hidden service websites. You can test the running search engine at [ahmia.fi](https://ahmia.fi/search/).

Building a search engine for anonymous web sites running inside the Tor network is an interesting problem. Tor enables web servers to [hide their location](https://www.torproject.org/docs/hidden-services) and Tor users can connect to these authenticated hidden services while the server and the user both stay anonymous. However, finding web content is hard without a good search engine and therefore a search engine is needed for the Tor network.

Web search engines are needed to navigate and search the web. There were no search engines for searching hidden service web content, so I decided to build a search engine specially for Tor. I registered ahmia.fi and started development on it as a side project in 2010.

This development involved programming and testing web crawlers, thinking of ways to find hidden service addresses (since the protocol does not allow enumeration), learning about the Tor community, and implementing a filtering policy. Moreover, I implemented [an API](https://ahmia.fi/documentation/) that empowers other Tor services that publish content to integrate with Ahmia.

As a result, Ahmia is a working search engine that indexes, searches and catalogs content published on Tor Hidden Services. Furthermore, it is an environment to share meaningful statistics, insights and news about the Tor network itself.

Interesting Summer of Code
--------------------------

One of my best memories from the summer is the Tor Project's Summer 2014 Developers meeting that was hosted by Mozilla in Paris, France. I have always admired the people who are working on the Tor Project.

I also loved the coding itself. Finally I had time to improve the Ahmia search engine and its many features. [I did a lot of work](https://github.com/juhanurmi/ahmia/commits/master) and liked it.

Some journalist were very interested in my work: Carola Frediani asked if I could analyze the content of hidden services. I coded a script that fetches every front page's HTML, I gathered all the keywords, headers and description texts and made a simple word cloud visualization.

![Hidden website content visualization.](https://ahmia.fi/static/visuals/content.png)

It is a simple way to glance what is published on the hidden websites.

Carola found this data useful and used it in her presentation at [www.sotn.it](http://www.sotn.it "www.sotn.it") on June 11th.

Technical design of ahmia
-------------------------

The Ahmia web service is written using the Django web framework. As a result, the server-side language is Python. On the client-side, most of the pages are plain HTML. There are some pages that require JavaScript, but the search itself works without client-side JavaScript.

The components of Ahmia are:

-   Django front-end site
-   PostgreSQL database for the site
-   Custom scripts to download data about hidden services
-   Django-Haystack connection to Solr database
-   Apache Solr for the crawled data
-   OnionBot crawler that gathers data to Solr database

![Technical architecture.](https://raw.githubusercontent.com/juhanurmi/ahmia/master/technical_architecture.png)

[See installation and developing tutorial](https://github.com/juhanurmi/ahmia/blob/master/README.md)

Search
------

The full-text search is implemented using Django-Haystack. The search is using crawled website data that is saved to Apache Solr.

OnionDir
--------

[OnionDir](https://ahmia.fi/address/) is a list of known online hidden service addresses. A separate script gathers this list and fetches information fields from the HTML (title, keywords, description etc.). Furthermore, users can freely edit these fields.

We've also started a convention where hidden service admins can add a file to their website, called [description.json](https://ahmia.fi/documentation/descriptionProposal/), to offer an official description of their site in Ahmia.

As a result, this information is shown in [the OnionDir page](https://ahmia.fi/address/#/search=Description%20downloaded%20directly%20from%20the%20hidden%20service.) and over 80 domains are already using this method.

Statistics
----------

We are gathering statistics from hidden services. As a result, we can represent and share [meaningful data about hidden services](https://ahmia.fi/documentation/) and [visualize it](https://ahmia.fi/stats/viewer).

We are gathering three types of popularity data:

1.  Tor2web nodes share their visiting statistics to Ahmia
2.  Number of public WWW backlinks to hidden services
3.  Number of clicks in the search results

The click counter tells the total number of clicks on a search result in ahmia.fi

Filtering
---------

We have decided to filter any sites related to child porn from our search results. Ahmia is removing everything related to these websites. These websites may not be actual child porn sites. They are rather sites where users can post content (forums, file and image uploads etc.) and as the result there have been, momentarily at least, some suspicious content that has not been moderated in a reasonable period of time. Ahmia.fi does not have the time to monitor these sites carefully and we are banning sites from our public index if we see any evidence of child abuse. Of course, the ban is removed if the site itself contacts us and we review the website to be OK.

In practice, Ahmia calculates the MD5 sums of the banned domains for use as a filtering policy. Moreover, we are sharing this list and Tor2web nodes can use the list to filter out pages.

At the moment, there seems to be 1228 hidden website domains online and 7 of them has been filtered because they are possibly sharing child porn content.

OnionBot
--------

[OnionBot](https://github.com/juhanurmi/ahmia/tree/master/onionbot) is a crawler for hidden service websites based on the Scrapy framework. It crawls the Tor network and passes data to the search database. OnionBot requires the Tor software (using Tor2web mode) and Polipo. The results are saved to Apache Solr.

Apache Solr
-----------

Apache Solr is a popular, open source enterprise search platform. Its major features include powerful full-text search, hit highlighting, faceted search, and near real-time indexing.

The [schema.xml](https://github.com/juhanurmi/ahmia/blob/master/solr/schema.xml) file contains all of the details about which fields your documents can contain, and how those fields should be dealt with when adding documents to the index, or when querying those fields.

Security measures for privacy
-----------------------------

In the software

-   We do not log any IP addresses, see [Apache configuration](https://github.com/juhanurmi/ahmia/tree/master/apache2)
-   We are gathering real-time clicks, however, this data is not shown accurately

In the host ahmia.fi

-   Backend servers are run separately and they do not have any knowledge about the end-users
-   All servers are hosted in countries with strong privacy laws. For example, Finland and the Netherlands
-   Communication between servers is encrypted
-   Only a few trustworthy people know the locations of the back-end servers and are able to access them

Future work
-----------

GSoC 2014 was fun and productive!

There is a lot more to do. However, I do not have time to do everything myself. Of course, I am coding when I have time and maintaining the search engine.

In addition, I am going to write a scientific article about the implementation.

Is there anyone who would be interested in developing Ahmia.fi?

Is anyone familiar with Solr and would know how to tweak it for full text search?

Furthermore, any kind of help would be most welcome. There are always Linux admin duties, HTML/CSS design, bug fixing, Django development, etc...

**For further information, please don't hesitate to contact me by e-mail: juha.nurmi@ahmia.fi**
