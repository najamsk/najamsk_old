---
layout: post
title: "Archive Folders With Powershell"
date: 2014-10-01 12:09
comments: true
categories: 
- powershell
---

When your web application is running on web server and you don't have automatic backup service available form your hosting service provider taking manual backups is really a frustrating job. 

I have [Pscx](https://pscx.codeplex.com/) module installed on my PC and they have a nice little command Write-Zip available so I decided to write a custom powershell function that can create archive in zip formats for me. You can use windows task scheduler to invoke any powershell script so you can take advantage of this to have automatic daily or monthly backups. 

{% codeblock %}
#$target is the folder you want to zip
#$destinaion is the path where you want to create zip file
#$outFile is the fileName of the generated zip file
function CreateZip($target, $destination, $outFile)
{

#todays date
$date = Get-Date -Format yyyy_dd_MM

#if output file is not mentioned try to get a file name based on target
if ($outFile -eq $null -or $outFile -eq '')
{
    #$target = "E:\projects\AspNet\MVC\newFolder"
    $a = Split-Path $target -Parent
    $outFile = $target.Replace("$a\", "") + "_$date"  + ".zip"    
}

#if desitnation is not mentioned create zip file in target folder
if($destination -eq $null -or $destination -eq '')
{   
    $destinationPath = $target + $outFile;
}
else
{
    $destinationPath = $destination + $outFile
}

Write-Zip $target -IncludeEmptyDirectories -OutputPath $destinationPath
return $destinationPath
}

#this command will zip folder at E:\projects\AspNet\MVC\newFolder as myproject.zip at E:\Projects\AspNet\ 
$bakfile = CreateZip E:\projects\AspNet\MVC\newFolder E:\Projects\AspNet\ myproject.zip

{% endcodeblock %}

I have shared this script on [github](https://github.com/najamsk/powershellRepo) adjust it accroding to your needs and share your resutls. 

Please feel free to suggest improvements and if you have any questions use comments area.

Thanks for your time. 

-Najam