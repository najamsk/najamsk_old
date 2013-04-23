---
layout: post
title: BLL - Business layer with Linq
date: 2009-06-08 07:04
comments: true
categories:
- linq
- c#
- .net
---
Hello guys,

This is my first Bll class that is using linq and returning objects to presentation layer. Main data component class is ItemsDT which contain another skeleton class "ItemGridView" for custom view of items data table. "ItemGridView" contains basically have the fields that i want to show in my presentation layer. Note that items datatable has many column which can be reterived by calling AllItems() method.

If you just want to list all the methods into your table that is also included into your linq to sql file then you can set your method return type to list collection of the type that specified in dbml file (linq to sql). For example if you add items table into your linq to sql you will have a new type or class called Item. From your linq code you can return all the rows into the table as objects. Now these objects you can have as list collection of type Items so your method can return List&lt;Items&gt; and this return list will bind to any databound control like grid view with ease.

Problem arises if someone say only show selective columns then if you try to select few colums you will see visual studio provding you hint that objects return from the linq query will be of annonymous type. So to tackle this you have two options either spicy your return varriable of  object type or write a skelton class that have all those columns you want to have from your datable. Below is the code with skelton class approch its easy to guess skelton class will define a type and visual studio will not alert anymore by saying your objects are of annonymous type.

{% codeblock lang:c# %}

public class ItemsDT
{
[System.ComponentModel.DataObjectMethod(System.ComponentModel.DataObjectMethodType.Select)]
public static List&lt;Items&gt; AllItems()
{
DBDataContext db = new DBDataContext();
return (from t in db.Items select t).ToList&lt;Items&gt;();
}

public class ItemGridView
{
public int itemID { get; set; }
public string itemName { get; set; }
public string itemgroupName { get; set; }
}
[System.ComponentModel.DataObjectMethod(System.ComponentModel.DataObjectMethodType.Select)]
public static List&lt;ItemGridView&gt; ListSubGroups_Admin()
{

return (from t in AllItems() select new ItemGridView {
itemID = t.sgID,
itemName = t.sgName,
itemgroupName = t.Group.gName
}).ToList&lt;ItemGridView&gt;();
}

{% endcodeblock %}
