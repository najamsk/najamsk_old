---
layout: post
title: "playing with octopress blogging"
date: 2013-04-22 20:12
comments: true
categories: 
- ruby 
- github 
- octopress
- blogging
---

I think blogging using octopress and github pages mentioned in yayquery episode where [rebbeca murphy](http://google.com) let us know about her blog is now powered by these tools and she moved it from wordpress.

At that time i did'nt do anythig with the info but today I thought lets do this crazy shit and wolla here I am.

I have read following octopress documentation for configuration and blogging:

* [configuring octopress](http://octopress.org/docs/configuring/)
* [blogging with octopress](http://octopress.org/docs/blogging/)
* To migrate your wordpress posts to markdown files i have used [wpxml2jekyll](https://github.com/theaob/wpXml2Jekyll)

	rake setup_github_pages
this will ask for your github repo path.

Next you need to do following two commands to genrate site from octopress and upload it to github repo.

	rake generate
	rake deploy

I will have few things in mind to discover about octopress 
* q: how to customize the styles/layout?
* q: how to make twitter work in sidebar?
* q: how to make rake preview to work against current copy in master branch?
* q: how to make it work against blog.najamsikander.com
* q: how to get my comments against each post from discuss?

I will keep updating this post while discovering work arounds. I guess i will be ditching wordpress soon after finding all the answers.