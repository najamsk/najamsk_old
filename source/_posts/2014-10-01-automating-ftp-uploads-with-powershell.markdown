---
layout: post
title: "Automating Ftp Uploads With Powershell"
date: 2014-10-01 12:45
comments: true
categories: 
- powershell
---

When your web application is running on web server and you don't have automatic backup service available form your hosting service provider taking manual backups is really a frustrating job. 

I have [Pscx](https://pscx.codeplex.com/) module installed on my PC and they have a nice little command Write-Zip available so I decided to write a custom powershell function that can create archive in zip formats for me. You can use windows task scheduler to invoke any powershell script so you can take advantage of this to have automatic daily or monthly backups. 

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