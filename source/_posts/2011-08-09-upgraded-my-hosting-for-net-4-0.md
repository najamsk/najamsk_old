---
layout: post
title: Upgraded my hosting for .net 4.0
date: 2011-08-09 10:13
comments: true
categories:
- .net
---
I have been watching Mix11 videos about asp.net mvc3 and felt pretty excited to mingle with these latest bits but I didn't wanted to limit myself to local environment I wanted to know what efforts are required if I am developing with latest stuff one limitation I had that my host always take ages to update server so I had support for .net3.5. I email them about this thing and in reply they told me either wait 6 months or pay $8. Since I was dying to test out EF code first I paid them and within one day my hosting is all updated and now I am running my incomplete demo online :).

Deployment was a little bit scarier as my hosting doesn't come with any publishing/deployment server but if you have vs2010 sp1 then you are in safe hands all you have to do is to click on add deployable dependencies then build your solution and upload using your favorite ftp client.

This far I like MVC3.0 , Nuget and MVC Scaffolding but I am still learning how to scaffold many to many relations or at least leverage scaffolding and then tune it to have many to many relations.
