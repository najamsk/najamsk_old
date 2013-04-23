---
layout: post
title: C# Interfaces
date: 2009-06-22 03:37
comments: true
categories:
- c#
---
These parts are taken from msdn and some might be taken from other websites.

An interface can inherit from one or more base interfaces.

When a base type list contains a base class and interfaces, the base class must come first in the list.

A class that implements an interface can explicitly implement members of that interface. An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.

Ref: <a href="http://msdn.microsoft.com/en-us/library/87d83y5b(VS.80).aspx">http://msdn.microsoft.com/en-us/library/87d83y5b(VS.80).aspx</a>

Interfaces can consist of methods, properties, events, indexers, or any combination of those four member types. An interface cannot contain fields. Interfaces members are automatically public.

if a base class implements an interface, the derived class inherits that implementation.

Classes and structs can inherit from interfaces in a manner similar to how classes can inherit a base class or struct, with two exceptions:
<ul>
	<li>A class or struct can inherit more than one interface.</li>
	<li>When a class or struct inherits an interface, it inherits only the method names and signatures, because the interface itself contains no implementations</li>
</ul>
To implement an interface member, the corresponding member on the class must be public, non-static, and have the same name and signature as the interface member. Properties and indexers on a class can define extra accessors for a property or indexer defined on an interface. For example, an interface may declare a property with a <a id="ctl00_MTContentSelector1_mainContentContainer_ctl06" onclick="javascript:Track('ctl00_MTContentSelector1_mainContentContainer_ctl00|ctl00_MTContentSelector1_mainContentContainer_ctl06',this);" href="http://msdn.microsoft.com/en-us/library/ms228503.aspx">get</a> accessor, but the class implementing the interface can declare the same property with both a <span><span>get</span></span> and <a id="ctl00_MTContentSelector1_mainContentContainer_ctl07" onclick="javascript:Track('ctl00_MTContentSelector1_mainContentContainer_ctl00|ctl00_MTContentSelector1_mainContentContainer_ctl07',this);" href="http://msdn.microsoft.com/en-us/library/ms228368.aspx">set</a> accessor. However, if the property or indexer uses explicit implementation, the accessors must match.

Interfaces can inherit other interfaces. It is possible for a class to inherit an interface multiple times, through base classes or interfaces it inherits. In this case, the class can only implement the interface one time, if it is declared as part of the new class. If the inherited interface is not declared as part of the new class, its implementation is provided by the base class that declared it. It is possible for a base class to implement interface members using virtual members; in that case, the class inheriting the interface can change the interface behavior by overriding the virtual members. For more information about virtual members

Overview:

An interface has the following properties:
<ul>
	<li>An interface is like an abstract base class: any non-abstract type inheriting the interface must implement all its members.</li>
	<li>An interface cannot be instantiated directly.</li>
	<li>Interfaces can contain events, indexers, methods and properties.</li>
	<li>Interfaces contain no implementation of methods.</li>
	<li>Classes and structs can inherit from more than one interface.</li>
	<li>An interface can itself inherit from multiple interfaces.</li>
</ul>
Ref: <a href="http://msdn.microsoft.com/en-us/library/ms173156.aspx">http://msdn.microsoft.com/en-us/library/ms173156.aspx</a>
