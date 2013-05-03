---
layout: post
title: "Testing jQuery code via YUI Test"
date: 2013-05-03 21:22
comments: true
categories: 
- javascript
- tips
- Testing
- YUI
---

The term TDD is not new to me I heard it quite often but never took time to go into details until last few days. I have been checking stuff from YUI team and liked their YUI test framework for now ,but in future i might switch to qUint (jquery testing framework) as I am big fan of jQuery and using it daily.

There are different version of YUI like 2.0,3.0 and standalone version of YUI test that has no dependency over YUI framework according to yui theater video. 

So for learning purpose I have written few lines of jQuery to set color of a paragraph on mouse hover. I wrote a test using YUI; in the test I simulate mouse hover event and then checking the paragraph css color properties using jquery :).

You can view the code at [http://snipplr.com/view/47746/testing-js-code/](http://snipplr.com/view/47746/testing-js-code/).