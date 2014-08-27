---
layout: post
title: "Google Summer of Code 2008 review"
permalink: google-summer-code-2008-review
date: 2009-03-09
author: Sebastian
category: blog
tags: ["Google Summer of Code", "gsoc", "gsoc 2008"]
---

As we started preparing to apply for the Google Summer of Code 2009, we realized that we haven't reported how last year's Summer of Code went for us.

Tor's 2008 Google Summer of Code was a victim of Tor's increasing growth! We've got a lot more people involved now, and we have a lot more projects we want to tackle. But that also means we need to work harder at coordinating everything, and that's not as smooth as we'd hoped.

Tor had the luxury to receive seven slots for students. GSoC 2008 overall, was a success; as the students and projects contributed a lot to the Tor project. Also, here I am, a former GSoC student writing a blog post for the project.

Below is an overview over the GSoC 2008 projects and a summary of their results.

_Domenik Bork: Configuration of Hidden Services with User Authorization in Vidalia_  
Support for creating hidden services using a GUI was lacking from [Vidalia](http://vidalia-project.net), making it very hard for Vidalia users to correctly set up their own. It was necessary to change Tor's configuration file manually, and many users are overwhelmed by the task of even locating that file. Domenik created a new tab in the Vidalia settings to allow the creation and configuration of hidden services, and worked on the necessary UI changes to allow the creation of the new hidden services with user authorization (currently available only in alpha versions of Tor). As soon as the next stable Tor version lands, users will be able to set up their hidden services with user authorization with more convenience.

_Fallon Chen: Improving Tor Path Selection_  
When Tor decides on a path for a new circuit, many factors come into play. Currently, latency does not factor into the equation a whole lot, but it is really important for the user experience. On the other hand, always choosing the fastest connection will harm anonymity. Fallon tried to find a model to reduce circuit establishment times, without affecting anonymity too much. During her project, she gathered a lot of data that helps shaping the current development of Tor. She discovered that a Pareto distribution is a good model for Tor circuit establishing times. Unfortunately, she had to quit working before much actual code could be produced; nevertheless, her research is the basis for the current development of Tor's path selection. She was also involved in the writing of [proposal 151](https://svn.torproject.org/svn/tor/trunk/doc/spec/proposals/151-path-selection-improvements.txt), which Mike Perry is currently implementing. The goal of the proposal is to allow Tor clients to automatically detect useful values for configuration options depending on the user's environment (mobile satellite connection vs. broadband, or changing conditions).

_Aleksei Gorny: Tor Exit Scanner Improvements_  
To prevent exit nodes from maliciously (or unintentionally) interfering with traffic passed through them, we have [SoaT (Snakes on a Tor)](https://svn.torproject.org/svn/torflow/trunk/NetworkScanners/README.ExitScanning) to automatically detect nodes that misbehave. It was Aleksei's task to extend SoaT to make it more useful, especially to make it execute tests automatically, so that eventually directory authorities can use its input to flag bad nodes appropriately. The result of the project is the foundation of our ongoing work there, and a functional version exists to be evaluated now.

_Sebastian Hahn: Extending PuppeTor_  
During my project, I worked on extending [PuppeTor](https://git.torproject.org/checkout/puppetor/master/) to allow forming virtual networks that can run centrally coordinated tests (similar to buildbot, except with a test suite). I produced a version that allows basic tests to be run, but the API became incompatible with the pre-existing PuppeTor. Also, in its state immediately after the summer of code, writing tests was rather more difficult than with the original version. After the summer, we decided that there should be no two different versions of PuppeTor, and I continue to do work on top of the version produced during the summer. It will eventually be deployed as the new PuppeTor and used for regression testing as well as performance/anonymity evaluations. One of the specific challenges that both student and mentor learned from here was a lack of communication about what the result should look like. I ended up developing something that wasn't what some of the developers had originally envisioned, which caused quite a bit of extra work.

_Simon Johansson: A Translation wiki for our website_  
The Tor Project has been working over the past year to set up web-based tools to help volunteers translate our applications into other languages. We finally hit upon [Pootle](http://translate.sourceforge.net/wiki/pootle/index), and we have a fine [web-based translation engine](https://translation.torproject.org/) in place for Vidalia, Torbutton, and Torcheck. However, Pootle only translates strings that are in the "po" format, and our website uses [wml files](https://www.torproject.org/translation). Simon's project was to come up with a way to convert our wml files into po strings and back, so they could be handled by Pootle. Unfortunately, communication between Simon and his mentor didn't happen often enough, and in the end we got very little useful work out of this project. Nevertheless, many components of the Tor project can now be [translated by using Pootle](https://www.torproject.org/translation-overview).

_Camilo Viecco: Providing Blossom functionality to Vidalia_  
 [Blossom](https://svn.torproject.org/svn/blossom/trunk/) allows to choose that the user prefers to exit from a specific country. The same can be achieved by manually changing Tor's configuration file, but Vidalia, our Tor configuration tool, did not have a way to easily let users select a country to exit from. Camilo's task was to integrate this functionality into Vidalia, so that mainstream users can benefit without needing to figure out how to use Blossom. During his work, a completely functional branch was created that can be used to achieve the goals. Due to some changes in the Vidalia UI, his work couldn't be merged into mainline Vidalia completely. Instead, his back-end changes will be cherry-picked into mainline as soon as the UI work is finished.

_Christian Wilms: Performance Enhancing Measures for Tor Hidden Services_  
Hidden services are a very useful feature in Tor that allows anyone to host a location-hidden service. Unfortunately, accessing them is often a rather slow process. Based on a [paper](http://freehaven.net/anonbib/#loesing2008performance) that he and Karsten Loesing had written, Christian started out by measuring connection times to hidden services under various conditions. He found and fixed quite a few bugs in the process. During the remainder of the summer, Christian worked on a larger-scale change to reduce connection times, and his work could be used as a basis for a later patch to fix the remaining issues.

The summary is that Tor took too many students last summer; as overall we were about 50% successful with project completion. Better mentoring, including being stricter with students and weekly progress reports, could have been very helpful for our students. I experienced it myself: towards the end of the summer I still had a lot of stuff on my plate that I needed to rush through. By having fewer students and better communication between mentors and students, and involving students more with the Tor project as a whole, we should be able to get even more out of the next summer, if Google invites us to participate again. Maybe the next GSoC blog post will be written by a GSoC 2009 student?

As a last note, next time around we plan to work more closely with the [EFF](https://www.eff.org) (our sponsor organization for GSoC). In particular, we'd like to accept a few students to work with Peter Eckersley on Switzerland and other projects organized by EFF's engineers.

