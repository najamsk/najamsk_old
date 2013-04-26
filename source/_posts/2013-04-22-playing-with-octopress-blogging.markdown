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
I first came to know about octopress from yayquery episode in which rebbeca murphy mentioned she has moved her blog form wordpress to octopress and she is very happy with that. At that time I didn't paid any attention to this. 

But today I suddenly started to play with it and I liked few things I learn along the way and that kept me going till I have imported all of my posts from wordpress to github pages.


I have read following pages form octopress documentation for configuration and blogging:

* [configuring octopress](http://octopress.org/docs/configuring/)
* [blogging with octopress](http://octopress.org/docs/blogging/)
* To migrate your wordpress posts to markdown files i have used [wpxml2jekyll](https://github.com/theaob/wpXml2Jekyll)
* To integrate twitter into your octopress blog sidebar read [put twitter back into sidebar](http://blog.jmac.org/blog/2013/03/30/putting-twitter-back-into-octopress/)
To link your octopress setup with github you have to run following this will ask for your user/organization repository.

{% codeblock %}
	rake setup_github_pages
{% endcodeblock %}

Next you need to do following two commands to generate site from octopress and upload it to github repo.
	rake generate
	rake deploy

I will have few things in mind to discover about octopress

* q: how to customize the styles/layout?
* q: how to make twitter work in sidebar?
* q: how to make rake preview to work against current copy in master branch?
* q: how to make it work against blog.najamsikander.com
* q: how to get my comments against each post from discuss?

I will keep updating this post while discovering work around. I guess i will be ditching wordpress soon after finding all the answers.