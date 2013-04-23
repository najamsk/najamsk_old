---
layout: post
title: Speed Up Firfox
date: 2005-12-01 00:12
comments: true
categories:
- firefox
- tips
- browsers
---
<p><strong> Here's something for broadband people that will really speed Firefox up:<br />
</strong><br />
1.Type "about:config" into the address bar and hit return. Scroll down and look for the following entries:</p>
<p>network.http.pipelining<br />
network.http.proxy.pipelining<br />
network.http.pipelining.maxrequests</p>
<p>Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.</p>
<p>2. Alter the entries as follows:</p>
<p>Set "network.http.pipelining" to "true"</p>
<p>Set "network.http.proxy.pipelining" to "true"</p>
<p>Set "network.http.pipelining.maxrequests" to some number like 30. This means it will make 30 requests at once.</p>
<p>3. Lastly right-click anywhere and select New-&gt; Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it receives.</p>
<p>If you're using a broadband connection you'll load pages MUCH faster now!
</p>
