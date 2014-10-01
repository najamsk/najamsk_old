---
layout: post
title: "Sending Emails With Powershell"
date: 2014-10-01 10:09
comments: true
categories: 
- powershell
- Email
---

I am managing different servers and each of them have different responsibilities.

I am learning powershell and trying to build lego blocks that will eventually become recipes for automating tasks on different servers. One important block is email report for that if you don't have smtp configured on server you can use following powershell script with gmail SMTP information. 


I will open source on [github](https://github.com/najamsk/powershellRepo) many of the small powershell scripts that you can make use of to build somethign cool. 



{% codeblock %}
$EmailFrom = "from@mail.com"
$EmailTo = "to@mail.com" 
$Subject = "emailing powershell report" 
$Body = "this should work on remove server as well. test email" 
$SMTPServer = "smtp.gmail.com" 
$SMTPClient = New-Object Net.Mail.SmtpClient($SmtpServer, 587) 
$SMTPClient.EnableSsl = $true 
$SMTPClient.Credentials = New-Object System.Net.NetworkCredential("gmailUser", "gmailPasswor"); 
$SMTPClient.Send($EmailFrom, $EmailTo, $Subject, $Body)
{% endcodeblock %}

Hope this will help someone, feel free to improve this script and than share it with me you can file bugs on github. 

Thanks for your time. 

-Najam