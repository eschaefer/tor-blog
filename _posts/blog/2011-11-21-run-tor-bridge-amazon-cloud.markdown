---
layout: post
title: "Run Tor as a bridge in the Amazon Cloud"
permalink: run-tor-bridge-amazon-cloud
date: 2011-11-21
author: Runa
category: blog
tags: ["bridge relays", "cloud", "tor", "tor cloud"]
---

The Tor Cloud project gives you a user-friendly way of deploying bridges to help users access an uncensored Internet. By setting up a bridge, you donate bandwidth to the Tor network and help improve the safety and speed at which users can access the Internet.

Bridges are Tor relays that aren't listed in the main directory. This means that to use a bridge, you'll need to locate one first. And because there is no complete public list of all the bridges, they are also harder to block. A bridge will act as the first hop in a circuit, and will only forward traffic on to other relays in the Tor network.

Setting up a Tor bridge on Amazon EC2 is simple and will only take you a couple of minutes. The images have been configured with automatic package updates and port forwarding, so you do not have to worry about Tor not working or the server not getting security updates.

You should not have to do anything once the instance is up and running. Tor will start up as a bridge, confirm that it is reachable from the outside, and then tell the bridge authority that it exists. After that, the address for your bridge will be given out to users.

To help new customers get started in the cloud, Amazon is introducing a free usage tier. The Tor Cloud images are all micro instances, and new customers will be able to run a free micro instance for a whole year. The Tor Cloud images have been configured with a bandwidth limit, so customers who don't qualify for the free usage tier should only have to pay an estimated $30 a month.

For more information, see the [Tor Cloud](https://cloud.torproject.org/) website.

**UPDATE** : Some users have asked about the AWS free usage tier and pointed out that it only includes 15 GB of bandwidth out per month. I have updated the Tor Cloud website (changes should go live soon) with the following:  
_  
The Tor Cloud images have been configured to use no more than 40 GB of bandwidth out per month. We have estimated that customers who do not qualify for the free usage tier will pay up to $30 a month. Customers who qualify for the free usage tier, but who run bridges that use more than 15 GB of bandwidth out per month, will pay up to $3 per month.  
_  
I hope that this better clarifies the cost of running a bridge in the Amazon cloud, let me know if you have any questions.

