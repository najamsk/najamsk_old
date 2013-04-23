---
layout: post
title: Calling asp.net page methods with jquery
date: 2009-02-03 04:23
comments: true
categories:
- asp.net
- ajax
- jQuery
- development
---
Hi guyz,

Today I am sharing how to call asp.net web page code behind methods from client side javascript in my case it will be jquery.

Let us divide this into two parts the server side and client side on server side we have to write a function or page method.
[code lang="csharp"]
[WebMethod]
public static string AddStrings(string a, string b)
{
return string.Format("my friend answer is {0}", a + b);
}
[/code]
Note that we mark  our AddStrings function as WebMethod and its public and static this is the basic requirement for the funtion if you want to call it from javascript or jquery.

Function itlsef is pretty simple all it does takes two strings join them and return the result.  Thats all we need to write for server side.

[code lang="javascript"]
$(function(){
$.ajax({

type: "POST",
url: "Default.aspx/AddStrings",
data: "{a:'najam ',b:'sikander'}",
contentType: "application/json; charset=utf-8",
dataType: "json",
success: function(msg) {
// Do something interesting here.
alert(msg);
},
error: function()
{
alert("Request can't made using ajax");
}
});//ajax ends here
});// document ready ends here
[/code]
Client side has its own requirements first its better to use post request if you want any result back from server and then you should use json as communication medium and for that we need to set content type and data type as

contentType: "application/json; charset=utf-8",  dataType: "json" and we should supply the input  data with our request. Please note that if your server side function expecting two parameters named "a" and "b" you should name your javascript input parameters same as server side parameters thats why in data section we have same name of the varriables. Example data: "{a:'najam ',b:'sikander'}",

Last requirement is your web.config should have entries for asp.net ajax sections. If you are building from scrath you can shoose asp.net ajax website as template when starting new website.

Please read articles from following links to know more and have a strong background.

http://encosia.com/2008/03/27/using-jquery-to-consume-aspnet-json-web-services/

http://encosia.com/2008/06/05/3-mistakes-to-avoid-when-using-jquery-with-aspnet-ajax/

http://www.keithrousseau.com/blog/2008/05/using-jquery-json-with-aspnet/
