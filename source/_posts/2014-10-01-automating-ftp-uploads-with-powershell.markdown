---
layout: post
title: "Automating Ftp Uploads With Powershell"
date: 2014-10-01 12:45
comments: true
categories: 
- powershell
---


In my last post I have shared hwo you can [archive a folder via powershell](http://blog.najamsikander.com/blog/2014/10/01/archive-folders-with-powershell/) and [Pscx](https://pscx.codeplex.com/). In my normal backup process I am used to upload zip files using ftp client like filezilla but now I am trying powershell to perform this task. 

Please feel free to test following code and let me know your thoughts and improvements.


{% codeblock %}

#upload file using ftp
function FtpUpload($file, $ftphost, $ftpuser, $ftppass){   
   $Dir = Split-Path $file -Parent 
   $filename = $file.Replace("$Dir\", "")

   #ftp server 
   $webclient = New-Object System.Net.WebClient 
   $webclient.Credentials = New-Object System.Net.NetworkCredential($ftpuser,$ftppass) 
    
    #list every sql server trace file 
    foreach($item in (dir $Dir $filename)){ 
        "Uploading $item..." 
        $filepath = $ftphost+$item.Name
        $filepath
        $uri = New-Object System.Uri($filepath)         
        $webclient.UploadFile($uri, $item.FullName) 
    } 
}

FtpUpload E:\projects\AspNet\MVC\newFoldernewFolder_2014_29_09.zip ftpHost ftpUser ftpPassword

{% endcodeblock %}

I have shared this script on [github](https://github.com/najamsk/powershellRepo) adjust it accroding to your needs and share your resutls. 

Please feel free to suggest improvements and if you have any questions use comments area.

Thanks for your time. 

-Najam