---
layout: post
title: "Continuous Integration &amp; Deployment For .Net Projects TL;DR"
date: 2014-12-31 20:05
comments: true
categories: 
- DevOps
- Automation
- Development
- Setup
---

I have been involved with development of small and large web applications for quite sometime now. While using latest tools and technology for development I always felt my workflow is from ancient times. Recently I got much obsessed with automation, I thought to improve my development workflow. In my mind I knew I need to do something about build process, tests the build, deployment of latest build and notify team members that new code/build is available. 

I started looking around, playing with tools from different vendors and finally shortlisted few tools to start with. Following tools made the list.

- PowerShell 
- Slack
- GitLab
- TeamCity
- Octopus Deployment
 
__If you are thinking wow it's alot to get started with automation then I will recommond learning Powershell if your using windows and .Net technologies. With Powershell only you can do most of things I am about to share with you.__

##Sprint Killings

We are using scrum for development with two week sprint cycle to get things out. Short sprints have their benefits but they also kills, if you are doing testing and deployment manually and this pain reaches to maximum intensity if you need to to push code to multiple servers (Dev, QA, Staging, Production). 

<img src="http://s3-ec.buzzfed.com/static/enhanced/webdr01/2013/2/20/17/anigif_enhanced-buzz-4131-1361399397-4.gif"/>

We have been using some tooling while writing code and communicating with each other and that was not modern and did hurt us after a while. Following list contains few common tools in use by our local industry:

* __TFS and SVN__ - for version control
* __Vychat & skype - for communication
* __Zero unit tests__ - (well few devs were submiting their forms to check output and called that unit testing. I am not joking.)
* __Zero integration tests__ (Again manual process followed by Devs and QA)
* __Deployment using filezilla__ (Yes this is the holy grail of deployment)

Few team members had major issues with SVN and TFS as souce control specially when they are not using windows. Since I have been using Git for sometime now and loved it. I recommonded git and knew we can't move ahead without installing local git server. After some research found GitLab that has free option available. We are running GitLab on ubuntu 12.04 box and untill now it's working smoothly.

Co-workers that got beatings from SVN fall in love with git and we all thought it's the only change we needed in our current workflow/tooling. Well that was a mistake.

<img src="http://s3-ec.buzzfed.com/static/enhanced/webdr02/2013/2/8/14/anigif_enhanced-buzz-11517-1360352639-1.gif" />


#### Problem 1: Who Moved The Code?

"Is it ok to pull latest code from remote branch?". Gitlab was providing us information about what changed in latest commit and by whom but couldn't signal us if the code is free from compile time errors. That created fear among devs and they came up with a solution called __"Push-Pa"__.

###### Manual Solution: Push-Pa

To solve above problem our team agreed to follow a process which dictates that before pushing your code to version control make sure you pull the code first merge it with your local changes. Compile the merged code, test it to check every feature is still working and than push it to remote branch. 

Compiling code is no rocket science but it was painful to do it manually against each commit. Team started to feel the burden but keeps doing it in fact they name this push-pull exercise as "Push-Pa".

###### Real Solution: Teamcity
I knew Teamcity for a while and used it against TFS source control for a big web forms based web application. At that time I was using it against TFS and to get notifications if latest commit compiles without errors. 

Since we are using GitLab now for latest projects first task at hand was how to integrate Teamcity with Gitlab server for monitoring latest commits in a specific branch. 

#### Problem 2: Deployment Nightmare
Our deployment process was from 80's or 90's if ftp exist back then. For deployment first step was to pull the latest code from source control. Then make changes for server environment (if you miss transforms, and environment checks) in config files and other code which is specific to server environment. Once that's done create a zip file and upload it to server via ftp. 

On server we need to unzip the latest code, and create backup of running website. Then overwrite files and test to see if deployment works. If its failing restore the backup, if it works pray to God and say thanks for the blessings.

<img src="http://25.media.tumblr.com/18f10fa837406181e2b43e1680187bb6/tumblr_mpg1oe3dK21qjmdwqo1_500.gif" />


###### Solution: Octopus Deploy
There are many solutions out there to handle deployments some bundled with integration feature. In few talks related to devops I came across Octopus Deploy. It felt nice, easy and powerful best part was they were targeting .net devs with slogan __"Automated deployment for .NEt"__.

Our team currently testing Octopus Deploy and it's linked with our Teamcity server. It takes the Teamcity compiled output/package and transform the code and settings for our deployment servers. Once code is modified for web servers its uploaded and deployed automatically. Backup against each deployment is managed by Octopus Deploy, you can roll back to preview release anytime you want. 

Configurations and integrating Octopus server with Teamcity and Gitlab was little hard but I got minimal setup working in fair amount of time. Now its much easier to deploy code and we can develop our project faster, push small changes/fixes frequently while keeping our sanity intact.

#### Problem 3: Are We There Yet?
Achieving continuous deployment was fun and I felt good about it, but one problem was still sticking around. Team asking each other if latest code has been deployed I could have setup emails notification on Teamcity and Octopus but knew different people value email differently. Some will wait for it and read it to get latest updates some will apply filter so these kind of emails skip their inbox. 

<img src="http://media.giphy.com/media/XUR9XH8olimic/giphy.gif" />

In my view having these updates inside team chat room was the best option but it's hard to integrate notifications with vychat or skype. This is why my first mission was to convert each member to slack and enforce everyone is using it. (still working on that front)

###### Solution: Slack
Slack offers integration points and rest API, using their API our Octopus server pushes updates about deployment like if deployment is successful or failed. After deployment notification another notification about same release updates team chat room for smoke tests(Powershell scripts) status.

###### Problem 4: Smoke Testing
Our current web application under development has many pages of different nature like public pages, secure pages, redirect pages and error pages.

One time we got complaint that one or two public pages are not working for users. Another time pages that suppose to be secure and ask for user credentials were open to everyone. Even though we have QA department and they take proper time to test still these issues could have crawled back. 

###### Solution: PowerShell
To avoid future complaints in this area I have developed a Powershell script that has list of pages (public, secure, 404, 500) and it make requests to those pages and according to response it pushes notifications to slack. That Powershell script is executed by Octopus on remote server after each deployment.

<img src="http://33.media.tumblr.com/tumblr_m2yyycfgnj1r2optzo1_500.gif"/>



## Source Control: GitLab

## Installing TeamCity

## Installing Octopus Deploy

## Configurations

## Results 


### Environment
We have made modifications to our local IT infrastructure we have some new servers that are running Gitlab, Teamcity and Octopus deploy. Gitlab is configured on Ubuntu 12.04 box for rest of the tools we are using windows platform.

Download Teamcity and Octopus Deploy setups files from following:

- [TeamCity Setup](https://www.jetbrains.com/teamcity/download/)
- [Octopus Deploy Sever](https://Octopusdeploy.com/downloads)
- [Octopus Deploy Tentacle](https://Octopusdeploy.com/downloads)
- [Ocotpus Deploy Teamcity Plugin](https://Octopusdeploy.com/downloads)



###Installing Teamcity
Installation is fairly simple and for database I wanted to use Microsoft SQL Server.Teamcity installation wizard guides you to [download SQL JDBC driver](http://confluence.jetbrains.com/display/TCD9/Setting+up+an+External+Database#SettingupanExternalDatabase-MicrosoftSQLServer). Unzip the file and look for a file _4.0.jar_ copy this file to lib folder of Teamcity installation directory. 

Now check your Teamcity installation wizard and test if drivers are loaded. If there are no errors you can now specify connection detail for your sql server database. 

After database setup Teamcity will prompt you for terms and conditions and then ask you to create admin account. 

####Creating Build: Gitlab
First thing is to create a new project, next choose create build configuration for your new project. Since source is on GitLab you need to check version control settings inside Teamcity. Make sure your settings are similar to mine.

<a href="https://lh6.googleusercontent.com/-gawLVzorkio/VK08JhJiFNI/AAAAAAAADkQ/6Wz8eiDJSn4/s2560/Edit-VCS-Root----TeamCity.jpg" title="version control settings">
<img src="https://lh5.googleusercontent.com/-HgycLiQB-VE/VK08HN9MQ3I/AAAAAAAADjk/RzN8533XJkI/s2560/Create-Build-Configuration-%E2%80%94-TeamCity.jpg"/>
</a>

<a href="https://lh6.googleusercontent.com/-gawLVzorkio/VK08JhJiFNI/AAAAAAAADkQ/6Wz8eiDJSn4/s2560/Edit-VCS-Root----TeamCity.jpg" title="version control settings">
<img src="https://lh6.googleusercontent.com/-gawLVzorkio/VK08JhJiFNI/AAAAAAAADkQ/6Wz8eiDJSn4/s2560/Edit-VCS-Root----TeamCity.jpg" title="version control settings" /></a>

You might tell from screenshot that our team city build will monitor dev branch of our project and as soon as new commit will arrive we will be notified to process it. 

Now we need to configure build steps right now I only have two build steps that downloads the code of latest commit and compiles it using the method I have choose. Second step will package the compiled code and pass it on to Octopus Deployment. You can see my build step configuration from following screenshot.

<a href="https://lh6.googleusercontent.com/--M2by-kAbPA/VK08NzqncBI/AAAAAAAADlA/vO2a0vnO9kE/s2560/jsp-Dev-Configuration----TeamCity_build_step.jpg"><img src="https://lh6.googleusercontent.com/--M2by-kAbPA/VK08NzqncBI/AAAAAAAADlA/vO2a0vnO9kE/s2560/jsp-Dev-Configuration----TeamCity_build_step.jpg" /></a>

<a href="https://lh3.googleusercontent.com/-UE-hPQxWaFM/VK08NeMJOqI/AAAAAAAADk8/OwzNLBeQ9fk/s2560/jsp-Dev-Configuration----TeamCityOctopus.jpg">
<img src="https://lh3.googleusercontent.com/-UE-hPQxWaFM/VK08NeMJOqI/AAAAAAAADk8/OwzNLBeQ9fk/s2560/jsp-Dev-Configuration----TeamCityOctopus.jpg" />
</a>

If you don't see OctoPack section yet with your Teamcity installation you need to install OctoPack plugin. Installation is dead simple copy Octopus.TeamCity.zip into Teamcity plugins folder (C:\ProgramData\JetBrains\TeamCity\plugins) then restart Teamciy windows service and refresh your browser you will have OctoPack section like screenshot.
<a href="https://lh5.googleusercontent.com/-Kk6UsR-yd-8/VK08Ij1p8iI/AAAAAAAADj4/9TOuhJi_2S0/s2560/Diagnostics---Browse-Data-Directory-%E2%80%94-TeamCity.jpg">
<img src="https://lh5.googleusercontent.com/-Kk6UsR-yd-8/VK08Ij1p8iI/AAAAAAAADj4/9TOuhJi_2S0/s2560/Diagnostics---Browse-Data-Directory-%E2%80%94-TeamCity.jpg" />
</a>

<a href="https://lh6.googleusercontent.com/-8051eiR2hqQ/VK08LJR0S0I/AAAAAAAADkk/wIEO5eM3Rx8/s2560/Plugins-List-%E2%80%94-TeamCity.jpg">
<img src="https://lh6.googleusercontent.com/-8051eiR2hqQ/VK08LJR0S0I/AAAAAAAADkk/wIEO5eM3Rx8/s2560/Plugins-List-%E2%80%94-TeamCity.jpg" />
</a>

### Installing OctoPack
Installation is dead simple once you have installed the Octopus Deploy server. You can run a tentacle setup on any deployment server (Staging, Testing, Production).

Let's configure our project inside Octopus Deploy now. Create a new project and name it.

Create a new environment and make sure add your tentacle or deployment server to that environment. I have one environment called development but later on I will add more like staging and production. 
<a href="https://lh6.googleusercontent.com/-7BkVrcQkcc4/VK08HwRAiKI/AAAAAAAADj0/DNP6ANsOWvk/s2560/Development-settings---Octopus-Deploy.jpg">
<img src="https://lh6.googleusercontent.com/-7BkVrcQkcc4/VK08HwRAiKI/AAAAAAAADj0/DNP6ANsOWvk/s2560/Development-settings---Octopus-Deploy.jpg" />
</a>

To integrate Octopus Deploy with Teamcity we need to create an API key. API keys are tied to Octopus Deploy user so you can create key by visiting users than pick a user and you will see a link to create new key. 

<a href="https://lh4.googleusercontent.com/-Vsfpjoi1idE/VMiO7qVZVMI/AAAAAAAADmw/RU30d6zCt44/s2560/octopuskey.png">
<img src="https://lh4.googleusercontent.com/-Vsfpjoi1idE/VMiO7qVZVMI/AAAAAAAADmw/RU30d6zCt44/s2560/octopuskey.png" />
</a>

We need to tell Octopus how to download Teamcity output for that you need to visit back Teamcity and configure a nuget feed. Goto teamcity administration area on left sidebar under integrations heading you will see a link called nuget click on it for configuration.

<a href="https://lh4.googleusercontent.com/-1rAGhlGhSg4/VMiO6_nhiOI/AAAAAAAADnE/oSGpIxXpsxQ/s2560/NuGetfeed.png">
<img src="https://lh4.googleusercontent.com/-1rAGhlGhSg4/VMiO6_nhiOI/AAAAAAAADnE/oSGpIxXpsxQ/s2560/NuGetfeed.png" />
</a>

Now you need to add that feed inside Octopus Deploy you can do that from inside Octopus Deploy dashboard. Simply click on library link from top navigation bar then you will see a link "External Feeds" on left sidebar. External feeds link will allow us to add teamcity feed and test it. For testing click on the test link and on new page you will see a search field and a search button. Click on search button and you will get results from teamcity. 

<a href="https://lh3.googleusercontent.com/-ZrS1eC9f-b4/VMiO69Nu5xI/AAAAAAAADm8/tuUaJ8TTbCU/s2560/octopusFeedArea.png">
<img src="https://lh3.googleusercontent.com/-ZrS1eC9f-b4/VMiO69Nu5xI/AAAAAAAADm8/tuUaJ8TTbCU/s2560/octopusFeedArea.png" />
</a>

While are pieces of puzzle are in their place we can now define the deployment process for our project. Octopus Deploy breaks process into steps that you need to define and configured. 

<a href="https://lh4.googleusercontent.com/-QgCOHh426Qo/VK08KQ8becI/AAAAAAAADkU/JRsK-3fkc6w/s2560/JumpstartPakistan-deployment-process---Octopus-Deploy.jpg">
<img src="https://lh4.googleusercontent.com/-QgCOHh426Qo/VK08KQ8becI/AAAAAAAADkU/JRsK-3fkc6w/s2560/JumpstartPakistan-deployment-process---Octopus-Deploy.jpg" />
</a>

<a href="https://lh3.googleusercontent.com/-izLzdy0drnQ/VK08HOYFABI/AAAAAAAADjs/4hTmdXlhWy4/s2560/Deploy---Octopus-Deploy_step_deploy.jpg">
<img src="https://lh3.googleusercontent.com/-izLzdy0drnQ/VK08HOYFABI/AAAAAAAADjs/4hTmdXlhWy4/s2560/Deploy---Octopus-Deploy_step_deploy.jpg" />
</a>

We start with our first step called deploy and like it's name it deploys the latest build from Teamcity to any environment we have pick. 

#### Slack Notifications
By this time you should be able to have a pipeline connecting your gitlab server to your deployment server using Teamcity and Octopus Deploy. It's time to inform team that new build has been deployed. To configure slack with Octopus deploy you need to visit Octopus Deploy dashboard again and click on library. On left sidebar click on "Step templates" link and than on top menu you will see another link "import step template". Octopus deploy has a community library and from there I have imported [Slack Integration script](https://library.octopusdeploy.com/#!/step-template/actiontemplate-slack-notify-deployment). 

Now you can add a new step into your process defined earlier. Follow screenshots to match my configuration. 

<a href="https://lh5.googleusercontent.com/-6jnog1nSD_o/VMiO746dWxI/AAAAAAAADm0/_5BZIBGETq4/s2560/slackImport.png">
<img src="https://lh5.googleusercontent.com/-6jnog1nSD_o/VMiO746dWxI/AAAAAAAADm0/_5BZIBGETq4/s2560/slackImport.png" />
</a>

<a href="https://lh3.googleusercontent.com/-hVW5n-d_bqI/VMiO79o1qDI/AAAAAAAADnI/jqse1muUppk/s2560/slackDetails.png">
<img src="https://lh3.googleusercontent.com/-hVW5n-d_bqI/VMiO79o1qDI/AAAAAAAADnI/jqse1muUppk/s2560/slackDetails.png" />
</a>

#### Smoke Testing Deployment
Remember the problem I have mentioned earlier in this post about some pages slip through QA and I solved that by writing Powershell script. Well running that test script manually was not good enough. I configured my process to run Powershell script for testing pages and announce the result of test in slack. Follow the screenshots for my configurations. 

<a href="https://lh4.googleusercontent.com/-VNbGYhdpY1g/VMiRVkcUg6I/AAAAAAAADnY/_Ya_JCidGjM/s2560/octopussmoke.png">
<img src="https://lh4.googleusercontent.com/-VNbGYhdpY1g/VMiRVkcUg6I/AAAAAAAADnY/_Ya_JCidGjM/s2560/octopussmoke.png" />
</a>

### Test Run
I have recorded a screencast for whole thing in action so you have better understanding of what we achieved.

### What's Next

<img src="http://media.giphy.com/media/c3LrSypJkaj0A/giphy.gif" />

- I need to add more environments into Octopus Deploy specially production so from testing server I can promote a build on live server without ftp and have support for rolling back.
- Need to have more Powershell script to clean files of builds older than a month to save disk space.
- Need to integrate twitter to post tweets about server status and post readings on slack. Monitoring bandwidth, hard disk space and some other events comes handy.


<img src="http://media.giphy.com/media/c3LrSypJkaj0A/giphy.gif" />


