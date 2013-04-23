---
layout: post
title: Get Running Jquery Version
date: 2010-12-06 02:12
comments: true
categories:
- jQuery
- javascript
- tips
- development
---
Few weeks back I came across a page that has multiple jquery versions referenced in it and I had no idea which jquery version is actually running. So after little bit of googling I find following solution.
<div>
<pre>//Returns "1.3.1"
$().jquery;

//Returns "1.3.1"
jQuery.fn.jquery;</pre>
</div>
