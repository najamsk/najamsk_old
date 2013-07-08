---
layout: post
title: "empower your outlook with powershell"
date: 2013-07-07 19:49
comments: true
categories: 
---


I needed to genrate an email log that contains every email from our clients these normally stored in their seprate folder. One way was to copy and paste email headers and body into a word document. Second was to use powershell and got all the emails using some script.

After playing a little with powershell and google few of its basic I have completed my task with powershell.

{% gist 5944505 %}

Above code is used to select a folder under your outlook inbox in my case its jun 2013 which comes under EmailLog which is under my inbox. I have saved the result of this function into a variable. That would be passed into second function for html creation. 

{% gist 5944515 %}

This funciton will take email objects and wrap html mark around thema before saving them into a html file.



