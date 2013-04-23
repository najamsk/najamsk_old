---
layout: post
title: How to get pagename of itself
date: 2007-11-06 06:04
comments: true
categories:
- c#
---
 If you want to display the filename or page name of the current displaying page just use these two lines and it will show only the filename like default.aspx, najam.aspx or indexas.aspx no matter it these pages are located deep into your site structure.

string pagename = System.IO.Path.GetFileName(Request.ServerVariables["SCRIPT_NAME"]); Response.Write(pagename);

Enjoy coding

Najam Sikander Awan
