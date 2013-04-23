---
layout: post
title: CSS Diet Plan - first step to object oriented css
date: 2010-12-03 01:59
comments: true
categories:
- css
---
I was wondering how to count the rules of my style sheets after little googling i discovered two ways one is through vim and second is through a command line tool called grep.

If you are a vim user and your css file is loaded into vim in command mode enter following command
<pre>:%s/font-size//gn</pre>
output will be the number of type font-size is used in your css file.

for grep open your command line and enter
<pre>cat style.css | grep -c font-size</pre>
output will be the count of font-size occurrences in style.css.

you can use *.css as well for all the css files in current directory.

Other then these methods I am really interested to use a tool which will take a file and list all the rules along with their count in code.
