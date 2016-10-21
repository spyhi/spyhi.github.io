---
layout: essay
type: essay
title: Making the Modern Web with Meteor
date: 2016-10-20
labels:
  - Meteor
  - Web Development
  - Web Frameworks
---

<img class="ui fluid image" src="../images/Meteor-First-Impression-Cover.jpg">

The web continues to evolve quickly, responding to the expectations of end-users for more and more powerful web applications that can compare to native apps on either the desktop or mobile phones. Though in terms of functionality, the web (especially the parts powered by goliaths such as Google and Facebook) has long been able to hold its own against desktop applications. However, they always had one shortcoming--the need to make constant HTTP requests in order to work with any sort of data. Until recently, the average internet speed in the US was only 10 Mbps (that's mega_bits_, not mega_bytes_). Even now, in the age of Netflix-driven growth in bandwidth, the average connection is hovering somewhere between 50-100 Mbps (again, _bits_), which simply can't compare to the 3-6 Gbps (bits) of the average SATA drive, or the 6400 MB/s (bytes here, not bits) of the aging DRR3 RAM standard. AJAX could minimize the amount of data necessary to transfer, but average connection speed still proved to be a major bottleneck compared to native applications.

Cue Meteor, a responsive web development framework that introduces two key innovations: Top-to-bottom use of JavaScript, and the introduction of "miniMongo."

MiniMongo in particular is an important and exciting new technology. In essence, Meteor replicates a portion of the server-side Mongo database on the client, allowing web applications using this paradigm to operate at speeds comparable to those of native apps. When information is requested or changed by the user, the request goes to the local database and returns an "optimistic" response to the user that is as fast as any native application. That change is then verified at the main Mongo database through a socket-based Distributed Database Protocol (DDP) and propagated through all client instances of the web application. This gives Meteor apps all the speed of native applications with all the benefits of web-based platforms.

Meteor's other key feature is JavaScript across the entire stack, on both client and server--even Mongo uses JSON objects to store data instead of classic relational tables. The end result is that Meteor is fairly easy to pick up, and very fast to develop with once learned. Many tasks are code-once-run-everywhere. Because of this particular feature, Meteor lends itself very well to prototyping and the kind of rapid development required of hackathons. One of the Meteor's organizing principles is "make developers happy," and it shows.

That's not to say Meteor doesn't have its downsides. As much as Mongo and miniMongo is a strength, its noSQL structure makes many organizations that require the data assurance of ACID-compliant databases wary of using it in production, and data assurance is more difficult. Shops running on this stack will have a difficult time obtaining contracts that require absolute data integrity, such as banks.

Also, the import/export model adopted by Meteor following the deployment of ES2016 is in severe need of work. Though it makes security better, and working with very large applications much easier, it also makes it easy to forget which files have been imported where, especially with the circular importing between JavaScript and HTML files. There are some workarounds, like various collections of imports statements in files, but surely there must be a more elegant way of achieving the same outcome. Then, Meteor will not only be able to sustain development of huge applications, but it will also become painless.

Additionally, a small complaint: it is _incredibly_ slow to compile and start up.

Lastly, for a new developer, Meteor is full of "magic," in the sense there is a lot hidden behind the scenes. As with all frameworks, it has the potential to obscure and obstruct learning and lock developers into certain, recognizable patterns. Of course, as a new developer, Meteor may have depths that I simply haven't learned yet and it may be flexible and customizable enough to build unique, mass-market applications--this is what Wordpress accomplished, after all, despite being more limited in obvious ways.

Meteor remains in active development and continues to evolve very rapidly. The development group is aware of many of the downsides mentioned here, and are actively working to address them (there is even an SQL version in the works called Apollo), so it won't be long before this essay is outdated and Meteor is even more streamlined and powerful.

Despite the downsides (which are honestly nitpicking), the tech behind Meteor is the future, and it allows even small shops to deploy applications that behave like those made by large tech companies that have the resources to create responsive applications like it from scratch, and I've been very lucky to learn how to use it so early in the game, and expect it will be around a long time to come.
