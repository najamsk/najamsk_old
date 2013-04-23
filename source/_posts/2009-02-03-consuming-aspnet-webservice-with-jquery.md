---
layout: post
title: Consuming asp.net webservice with jquery
date: 2009-02-03 05:22
comments: true
categories:
- asp.net
---
hi guys,

Well I like to share one more experiment with you that is how to call a webservice from your javascript(jquery). For that again you need to have an asp.net ajax enable website.

Lets first examine what are the requiments for webservice if we need to call it from javascript well after having asp.net ajax enable website first is you should mark your serverice as [ScriptService] what it does it will make all the methods/functions of your webservice to be accessable from javascript code and it also serialise your webservice response using JASON .

By default asp.net web services use soap for communication scriptservice marker make your webservice to use JASON.

Now lets defien the method in our webservice which we want to be accessable by our javascript code.
[code lang="csharp"]
[WebMethod]
public int AddingNumbers(int a, int b)
{
return a + b;
}
[/code]
That's it now lets move to client side code.
[code lang="javascript"]
$(function(){
$.ajax({

type: "POST",
url: "WebServices/MyWS.asmx/AddingNumbers",
data: "{'a':'1','b':'2'}",
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
In above javasrcipt code we are making an ajax post request we set  contentType to "application/json; charset=utf-8" and  dataType to "json" and passing a=1,b=2 as are data input parameters note that varriables name are same as verriables declared in webservice's function <strong>AddingNumbers </strong>input parameters.

Please read articles from following links to know more and have a strong background.

http://encosia.com/2008/03/27/using-jquery-to-consume-aspnet-json-web-services/

http://encosia.com/2008/06/05/3-mistakes-to-avoid-when-using-jquery-with-aspnet-ajax/

http://www.keithrousseau.com/blog/2008/05/using-jquery-json-with-aspnet/
