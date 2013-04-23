---
layout: post
title: Custom Event for Classes
date: 2009-07-06 04:28
comments: true
categories:
- c#
- .net
---
I was reading how to write events for your custom classes so after reading a little I thought give it a shot and created this sample code. Below code is using Product class with event and delegate for event handling and other class named Test is using this class and manipulate product class data. If you change the Name of the product event will fire.

[code lang="csharp"]

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

public void ChangeDetected(int a)
{
Console.WriteLine("change found,argument passed is {0}",a);
}
public void TestProduct()
{
Product p = new Product("najam awan");
p.PrintName();
p.NameChanged += ChangeDetected;
p.Name = "najaf";
p.PrintName();
Console.ReadKey();
}

}

static void Main(string[] args)
{
Test t = new Test();
t.TestProduct();
}
}
}

[/code]
