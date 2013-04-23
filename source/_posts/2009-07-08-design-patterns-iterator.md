---
layout: post
title: Design Patterns -- Iterator
date: 2009-07-08 06:16
comments: true
categories:
- c#
- design patterns
- .net
---
Hi Guys,

I am reading more on design patterns from this  <a title="Read This" href="http://msdn.microsoft.com/en-us/magazine/cc188707.aspx" target="_blank">article</a> after little theory session here is working code. Key point was all of the collection classes in the System.Collections namespace, as well as arrays, implement IEnumerable and can therefore be iterated over.

{% codeblock lang:c#%}
	using System;
	using System.Collections.Generic;
	using System.Linq;
	using System.Text;

	namespace ConsoleApplication1
	{
	class IteratorPattern
	{

	static void Main(string[] args)
	{

	int[] values = new int[] { 1, 2, 3, 4, 5 };
	IEnumerator&lt;int&gt; e = ((IEnumerable&lt;int&gt;)values).GetEnumerator();
	while (e.MoveNext())
	{
	Console.Write(e.Current.ToString() + " ");
	}

	Console.ReadKey();
	}
	}

	}
{% endcodeblock %}
