---
layout: post
title: How to get directory name of the page currently displaying
date: 2007-11-06 06:40
comments: true
categories:
- c#
- .net
- asp.net
---
If you want to know only the directory name not the full path of the page that is currently displaying you can use this code

string sPath = System.Web.HttpContext.Current.Request.Url.AbsolutePath;
System.IO.FileInfo oInfo = new System.IO.FileInfo(sPath);
string sRet = oInfo.Directory.Name.ToString();
Response.Write("&lt;br&gt;&lt;br&gt;Directory name===" + sRet + "&lt;br&gt;&lt;br&gt;");

Happy Coding

Najam Sikander Awan
