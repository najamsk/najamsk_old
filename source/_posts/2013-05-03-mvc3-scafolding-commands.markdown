---
layout: post
title: "MVC3 Scaffolding Commands"
date: 2013-05-03 21:06
comments: true
categories: 
- MVC
- asp.net
- c#
- tips
---

I had a freelance project that I have decided to do in MVC3 and to found following scaffolding commands very useful to get my Context, repository, controller, controller and views in PM console inside visual studio


{% codeblock lang:c# %}
Scaffold DbContext -Project CRS.Domain Service Concrete.CRSContext
Scaffold Repository -ModelType Attachment -DbContextType BigApp.Domain.Concrete.BigAppContext -force
Scaffold Controller -ModelType BigApp.Domain.Entities.Project -ControllerName Projects -DbContextType BigApp.Domain.Concrete.BigAppContext -Repository -NoChildItems -Force
Scaffold Controller -ModelType CRS.Domain.Entities.Service -ControllerName Services -DbContextType CRS.Domain.Concrete.CRSContext -Repository -NoChildItems -Force -Area admin
Scaffold Views -Controller Tags -ModelType BigApp.Domain.Entities.Tag
{% endcodeblock %}