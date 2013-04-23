---
layout: post
title: Random rows selection from a database table
date: 2009-01-29 03:36
comments: true
categories:
- database
- tips
- sql
---
hi everyone,

today I discovered a nice tip from a <a href="http://haacked.com/archive/2004/06/21/658.aspx" target="_blank">blog</a> I never knew selecting random rows were that easy with sqlserver 2000 and above. I have a country table that has four countries and from 4 I am selecting random 2.

<em>SELECT TOP 2 * FROM country ORDER By NEWID()
select * from country</em>

<strong>First Result</strong>

3           SaudiArabia
4           France

<strong>Second Result</strong>

1           UAE
4           France

<strong>Third Result</strong>

1           UAE
3           SaudiArabia

<strong>All Countries</strong>

1           UAE
2           Pakistan
3           SaudiArabia
4           France

Amazing right??
