---
layout: post
title: Facebook Application Development using Asp.net
date: 2010-09-23 01:31
comments: true
categories:
- asp.net
---
Hi,

I have been busy with facebook application development using IFrame and since I have asp.net background so instead of php I wanted to do this in asp.net their are few wrappers or sdk available for this like. After googling I have picked <a href="http://facebooktoolkit.codeplex.com/">Facebook developer toolkit v3.01</a>. After downloading the binaries I have created a asp.net web application project with 4.0 framework and simply added the reference of facebook.dll and facebook.web.dll.

In default.aspx code behind file we add the using statements for facebook dlls and inherit our page from facebook.web.CanvasIFrameBasePage and override the PreInit method for default page. Look at the snapshot of my default.aspx.cs for more understanding.

[caption id="" align="alignnone" width="504" caption="Code behind"]<a href="http://lh5.ggpht.com/_N_nhMTznTSY/TJrnvUilvCI/AAAAAAAAACE/tHVcjSKB9BY/s800/5.jpg"><img class="  " title="Defualt.aspx.cs" src="http://lh5.ggpht.com/_N_nhMTznTSY/TJrnvUilvCI/AAAAAAAAACE/tHVcjSKB9BY/s800/5.jpg" alt="Default page code behind " width="504" height="308" /></a>[/caption]

The hardest part was to configure my app with facebook and I also wanted to continue development using my development PC so that I don't have to upload my code as code changes. So lets first dive into facebook app configurations.

[caption id="" align="alignnone" width="504" caption="App Settings"]<a href="http://lh4.ggpht.com/_N_nhMTznTSY/TJrnqw-CC4I/AAAAAAAAABs/hPltmO-C6Io/s720/2.jpg"><img class=" " title="Facebook Application Settings" src="http://lh4.ggpht.com/_N_nhMTznTSY/TJrnqw-CC4I/AAAAAAAAABs/hPltmO-C6Io/s720/2.jpg" alt="FB APP Settings" width="504" height="347" /></a>[/caption]

From above snapshot you can see my application will run at at http://apps.facebook.com/fbnajam and the domain I am providing as Canvas URL is http://fbnajam.com. The www.fbnajam.com domain is not registered to anyone :) I will map this domain to my local IP address (127.0.0.1) by editting hosts file.

[caption id="" align="alignnone" width="717" caption="hosts file"]<a href="http://lh5.ggpht.com/_N_nhMTznTSY/TJrntfNdypI/AAAAAAAAAB8/H51GzD07FxM/s1024/3.jpg"><img class=" " title="Hosts file" src="http://lh5.ggpht.com/_N_nhMTznTSY/TJrntfNdypI/AAAAAAAAAB8/H51GzD07FxM/s1024/3.jpg" alt="domain mapping" width="717" height="338" /></a>[/caption]

Note in hosts file you can't put port with ip address for example 127.0.0./:1259 will not work so in your hosts file you will only enter the mapping between your virtual domain and 127.0.0.1 after making the entry make sure you reboot your PC to commit your changes.

Final part is to edit your web.config file and put app settings section which will contain your faceboko app api key, facebook app secret key and facebook app callbak URL in my case that was fbnajam.com for more understanding please look at following snapshot.

[caption id="" align="alignnone" width="560" caption="Web.config"]<a href="http://lh4.ggpht.com/_N_nhMTznTSY/TJrnuXSsh2I/AAAAAAAAACA/mJg7weL-tbI/s800/4.jpg"><img class=" " title="Web.Config" src="http://lh4.ggpht.com/_N_nhMTznTSY/TJrnuXSsh2I/AAAAAAAAACA/mJg7weL-tbI/s800/4.jpg" alt="web config" width="560" height="337" /></a>[/caption]

Now if you press F5 to run your application it will open facebook page showing your app and you will see your your name.

[caption id="" align="alignnone" width="694" caption="App Result"]<a href="http://lh6.ggpht.com/_N_nhMTznTSY/TJrnrgWdiNI/AAAAAAAAAB0/QbLOxyowUww/6.jpg"><img class=" " title="Facebook App Running" src="http://lh6.ggpht.com/_N_nhMTznTSY/TJrnrgWdiNI/AAAAAAAAAB0/QbLOxyowUww/6.jpg" alt="app result" width="694" height="195" /></a>[/caption]

After creating my first Facebook IFrame application I still want to use xFBML if supported need to test this application in my office. After doing some more experiments will update this post.
