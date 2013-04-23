---
layout: post
title: Observer pattern with .net
date: 2009-07-08 05:11
comments: true
categories:
- c#
- .net
- design patterns
---
Hi folks,

Well I am investigating design patterns by reading an <a title="Read This" href="http://msdn.microsoft.com/en-us/magazine/cc188707.aspx" target="_blank">article</a> so after reading a bit I thought it would be nice if I write some code and test it.

{% codeblock lang:c# %}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace ConsoleApplication1
{
class Program
{
/// &lt;summary&gt;
/// Product Class
/// &lt;/summary&gt;
public class Product
{
public delegate void NameChangeEventHandler(int a);
public event NameChangeEventHandler NameChanged;
private string _name;
public string Name
{
get
{
return _name;
}
set
{
_name = value;
if (NameChanged != null)
{
NameChanged(5);
}
}
}

public Product(string name)
{
Name = name;
}
public void PrintName()
{
Console.WriteLine("ProductName={0}", Name);
}
}

/// &lt;summary&gt;
/// Test Class
/// &lt;/summary&gt;
public class Test
{
public Test(Product P)
{
P.NameChanged += new Product.NameChangeEventHandler(ChangeDetected);
}
public void ChangeDetected(int a)
{
Console.WriteLine("change found,argument passed is {0}",a);
}

}

static void Main(string[] args)
{
Product p = new Product("najam awan");
p.PrintName();
Test t = new Test(p);
p.Name = "najaf awan";
p.PrintName();
Console.ReadKey();

}
}
}

{% endcodeblock %}
