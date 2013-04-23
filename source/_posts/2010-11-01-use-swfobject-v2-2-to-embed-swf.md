---
layout: post
title: use SWFObject v2.2 to embed swf
date: 2010-11-01 09:46
comments: true
categories:
- development
- javascript
---
{% codeblock lang:js %}
function flashswf(file, target, Width, Height, ID) {
var flashvars = {}
var params = {
//allowfullscreen:"true",
allowscriptaccess: "always",
wmode: "transparent",
menu: "false"
}
var attributes = {
id: ID,
name: ID
}
swfobject.embedSWF(file, target, Width, Height, "9.0.115", false, flashvars, params, attributes);
}

flashswf("/swf/total moistureiser.swf", "flashW", "704", "286", "homeFlash");

{% endcodeblock %}
