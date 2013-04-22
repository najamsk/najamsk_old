---
layout: post
title: "playing with octopress blogging"
date: 2013-04-22 20:12
comments: true
categories: 
- ruby 
- github 
- octopress
---

I think blogging using octopress and github pages mentioned in yayquery episode where [rebbeca murphy](http://google.com) let us know about her blog is now powered by these tools and she moved it from wordpress.

At that time i did'nt do anythig with the info but today I thought lets do this crazy shit and wolla here I am.

I have read following octopress documentation for configuration and blogging:

* [configuring octopress](http://octopress.org/docs/configuring/)
* [blogging with octopress](http://octopress.org/docs/blogging/)

	rake setup_github_pages
this will ask for your github repo path

Next you need to do following two commands to genrate site from octopress and upload it to github repo.

	rake generate
	rake deploy
