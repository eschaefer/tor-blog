---
layout: post
title: "Tor Metrics - Google Summer of Code 2010"
permalink: tor-metrics-google-summer-code-2010
date: 2010-10-14
author: kjbbb
category: blog
tags: ["gsoc", "gsoc2010", "metrics"]
---

Although it has been a while since GSoC ended, I want to give a quick run-down of my project and how everything went over the summer. The plan was to migrate the [Tor metrics portal](https://metrics.torproject.org/index.html "tor metrics portal") from the file based system to a database driven one. This allows us to have a more dynamic website and a better interface to derive our statistics and visuals from. I spent most of my time designing the database schema (which had to be carefully optimized due to the amount of data we have), and the remainder of the time working on things such as [dynamic graphs](https://metrics.torproject.org/graphs.html "dynamic graphs") and migrating the website to Java Server Pages. Thankfully, I finished almost everything I had planned to do, and it seems as though my work this summer is being put to good use! A significant amount of my metrics code has been merged, which is certainly a good feeling.

While I did not have any specific research questions in mind, I was able to uncover some interesting things by exploring the wealth of data in front of me. One of the things I promised to deliver was relay churn - a statistic to show the stability of the network. The Y axis, or the "churn ratio" is rather abstract, but it tells us the percentage of unique router fingerprints from one cohort that appear in the following cohort. Unfortunately, it requires a significant amount of database power to produce (large table scans are necessary when grouping routers by time period - the smaller the interval the longer the operation takes). However, the logic is clear and is easily accomplished from the database. The churn graphs may find their way onto the website, but the underlying processes may need to be optimized further. Either way, a database system ought to open a few doors for us in regards to some of the interesting things we can easily explore. See some of the churn graphs [here](https://blog.torproject.org/files/relay-churn-week.png), and [here](https://blog.torproject.org/files/relay-churn-month.png "relay churn month").

In addition to the back-end and database work, I explored [ggplot2](http://had.co.nz/ggplot2/) and the [R](http://www.r-project.org/) language - the tools used to generate the graphs on the metrics portal. Currently, R communicates with the database to generate graphs on demand (I settled on a [Postgres driver](http://code.google.com/p/rpostgresql/) for R which was part of GSoC 2008). The goal was to make the graphs parametizable so a user can request a custom or unique graph. The graphs are then served from [Rserve](http://rosuda.org/Rserve/) and Apache Tomcat. A few examples of the parametizable graphs are currently live on the metrics website which were implemented by Karsten.

Congratulations to the rest of the GSoC'ers John, Kory, and Harry for their successful projects. I want to give a big thank you to @KarstenLoesing for being such a great guide for my foray into the Tor Project and open-source development. It has been a great learning experience. Many thanks to Tor and Google for the opportunity!

<thead><tr>
<th>Attachment</th>
<th>Size</th> </tr></thead><tbody>
 <tr class="odd">
<td><a href="https://blog.torproject.org/files/relay-churn-month.png">relay-churn-month.png</a></td>
<td>18.33 KB</td> </tr>
 <tr class="even">
<td><a href="https://blog.torproject.org/files/relay-churn-week.png">relay-churn-week.png</a></td>
<td>16.78 KB</td> </tr>
</tbody>

