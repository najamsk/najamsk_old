---
layout: post
title: "Continuous Integration &amp; Deployment For .Net Projects TL;DR"
date: 2014-12-31 20:05
comments: true
categories: 
---

I have been involved with development of small and large web applications. I might have been using latest technologies and tooling but my workflow felt from ancient times. Recently I got so much obsessed with automation I thought it's good time to improve my development workflow. In my mind I knew i need to do somthing about build process, tests the build, deployment of latest build and notify team members that new build is available. 

I started looking around at that time devops coin was not tossed or wasn't that popular. I have testing tooling available from different vendors and tools I like were recorded with experiments into my evernote. I have explored following tools from some time

- PowerShell 
- Slack
- GitLab
- TeamCity
- Octopus Deployment
 
__If you are thinking wow it's alot to get started with automation then I will recommond learning powershell if your using windows and .Net technologies. With powershell only you can do most of things I am about to share with you.__

##Problems

<img src="http://s3-ec.buzzfed.com/static/enhanced/webdr01/2013/2/20/17/anigif_enhanced-buzz-4131-1361399397-4.gif"/>

We are using scrum for development with two week sprint cycle to get things out early and have some level of feedback while this all sounds promising short sprint cycle was killing us due to mannual code integration, testing and deployment to multiple servers. Specially when we were using following tooling to get job done.

* TFS and SVN for version control
* Vychat and skype of communication
* No unit testing
* No integration testing
* Deployoment using filezilla

Few team members had major issues with SVN and TFS as souce control specially on non-windows platforms. Since I have been using Git for sometime now and loved it. I recommonded git and knew we can't move ahead without installing local git server. After some research found GitLab that has free option available. We are running GitLab on ubuntu 12.04 box and untill now it's working smoothly.

Co-workers who were beaten by SVN were in love with git and thought it's the only change we needed that matters and we can live without burning too much time in exploring what else is out there. Well that was a mistake.

<img src="http://s3-ec.buzzfed.com/static/enhanced/webdr02/2013/2/8/14/anigif_enhanced-buzz-11517-1360352639-1.gif" />


#### Who Broke The Code?

When you are working in team for a single project with tight deadlines you continously asking question to yourself or team members "Is it ok to pull latest code from remote branch?". Gitlab was providing us information about what changed in latest commit and by whome but couldn't singal us about the integratity of the code it has.

###### Manual Solution: Push-Pa

To solve above our team agreed to a follow a process which dictates that before pushing your code to version control make sure you pull the code from target branch merge it with your changes. Compile the merge code test it to check every feature is still working and than push it back to remote branch. 

Since we lacked unit and integration tests for our code real testing was hard to achieve and compiling code is no rocket science but it was painful to do it manually. Team started to feel the burden but keep doing it infact they name this push pull excersize as "Push-Pa".

###### Real Solution: Teamcity
I knew teamcity for a while and used it against TFS source control for a big web forms based web applicatoin. First task at hand was how to integrate teamcity with gitlab server for monitoring latest commits in a specific branch. 

#### Deployment Nightmare
Our deployment process was from 80's or 90's if ftp exist back then. When we needed to deploy code first step was to pull the latest code from source control. Then make change for server envoirnment (if you miss transforms, and envoirnment checks) in config files and other code which is specific to server envoirnment. One thats done create a zip file and upload it to server via ftp. 

On server we need to unzip the latest code, and create backup of running website. than overwrite files and test to see if deployment works. If its failing restore the backup if it works pray to God and say thank you for the blessings.

<img src="http://25.media.tumblr.com/18f10fa837406181e2b43e1680187bb6/tumblr_mpg1oe3dK21qjmdwqo1_500.gif" />


###### Solution: Octopus Deploy
There are many solutions out there to handle deployments some also offer integration feature for which we are using teamcity. In few talks related to devops I came across octopus deploy. It felt nice, easy and powerfull best part was they were targeting .net devs. 

Our team currently testing octopus deploy and its linked with our teamcity server. It takes the teamcity compiled output and transform the code and settings for our deployment servers. Once code is modified for web servers its uploaded and deployed automatically. Backups of each deployment are managed by octopusdeploy you can roll back to preview release anytime you want. 

Configurations and integrating octopus server with teamcity and gitlab was little hard but it was worth it. Now its much easire to deploy code and we can develop our project faster, push small changes/fixes frequently while keeping our sanity intact.

#### Are We There Yet?
Achieving continous deployment was fun and I felt good about it, but one problem was still sticking around. Team asking each other if latest code has been deployed I can handle that with email notifications supported by teamcity and otcopus server. But I Know different people value email differently. Some will wait for it and read it to get latest updates some will apply filter so these kind of emails skip their inbox. 

<img src="http://media.giphy.com/media/XUR9XH8olimic/giphy.gif" />

In my view having these updates inside team chat room was the best option but its hard to integrate notfications with vychat or skype. This is why my first mission was to converty each member to slack and enforce everyone is using it. 

Slack offers integration points and rest api using their api our octopus server pushes updates about deployment like if deployment is successful or failed. After deployment notification you will see another notification about same release, which informs you if release passed the smoke tests(powershell scripts).

###### Smoke Testing
Webapplication we are developing have many pages of different nature like public pages, secure pages, rediret pages and error pages.

One time we got complaint that one or two public pages are not working for users. Another time pages that suppose to be secure and ask for user credentials were open to everyone. Even though we have QA department and they take proper time to test still these issues could have crawled back. To avoid future compalints in this area I have developed a powershell script that has list of pages (public, secure, 404, 500) and it make requests to those pages and according to response it pushes notifications to slack. That powershell script is executed by Octopus on remote server after each deployment.

<img src="http://33.media.tumblr.com/tumblr_m2yyycfgnj1r2optzo1_500.gif"/>


## Source Control: GitLab

## Installing TeamCity

## Installing Octopus Deploy

## Configurations

## Results 


### Envoirnment
For testing purpose I have installed both teamcity and octopus deploy on windows 8.1 machiene. We are using GitLab for our source control setup on Ubuntu 12.04 box.

Download teamcity and octpus deploy setups files from following:

- TeamCity Setup
- Octopus Deploy Sever
- Octopus Deploy Tenticle 
- Ocotpus Deploy Teamcity Plugin



###Installing teamcity
Installation is fairly simple and for database I wanted to use Microsoft SQL Server for that teamcity installation wizard guides you to [download SQL JDBC driver](http://confluence.jetbrains.com/display/TCD9/Setting+up+an+External+Database#SettingupanExternalDatabase-MicrosoftSQLServer). Unzip the file and look for a file _4.0.jar_ copy this file to lib foder of teamcity installation directory. 

Now check your teamcity installation wizard and test if drivers are loaded. If there are no errors you can now specifiy connection detail for your sql server database. 

After database setup teamcity will prompt you for terms and conditions and then ask you to create admin account. 

####Creating Build: Gitlab
First thing is to create a new project next choose create build configuration for your new project. Since source is on GitLab you need to check version control settings inside teamcity. Make sure your settings are similar to mine.

You might tell from screenshot that our team city build will monitor dev branch of our project and as soon as new commit will arrive we will be notified to process it. 

Now we need to configure build steps right now I only have two build steps that downloads the code of latest commit and compiles it using the method I have choose. Second step will package the compiled code and pass it on to octopus deployment. You can see my build step configuration from following screenshot.


If you don't see octopack section yet with your teamcity installation you need to install octopack plugin. Installation is dead simple copy Octopus.TeamCity.zip into teamcity plugins folder (C:\ProgramData\JetBrains\TeamCity\plugins) then restart Teamciy windows service and refresh your browser you will have octopack section like screenshot.

### Installing octopack
Installation is dead simple once you have installed the OctopusDeploy server. You can run a tenticle setup on any deployment server (Staging, Testing, Production).

Let's confgiure our project inside octopusDeploy now. Create a new project and name it.

Create a new envoirnment and make sure add your tenticle or deployemnet server to that envoirnment. I have one envoirnment called development but later on I will add more like staging and production. 

Octopusdeploy api key by going inside user.

We need to tell octopus how to download teamcity output for that you need to visit back teamcity and configure a nuget feed. 

Add nuget feed of teamcity with teamcity credentials. test by
searching packages. Make sure your teamcity has nuget feed available.

While are pecies of puzzle are in their place we can now define the deployment procoess for our project. Octopusdeploy breaks process into steps that you need to define and configured. 

We start with our first step called deploy and like it's name it deploys the latest build from teamcity to any envoirnment we have pick. 

#### Slack Notifications

#### Smoke Testing Deployment


<img src="http://media.giphy.com/media/c3LrSypJkaj0A/giphy.gif" />

<img src="http://www.simonstratford.com/wp-content/uploads/game-of-thrones-tyrion-lanister.gif" />

### Teamcity

<img src ="https://lh5.googleusercontent.com/-UE-hPQxWaFM/VK08NeMJOqI/AAAAAAAADk8/OwzNLBeQ9fk/w675-h563-no/jsp-Dev-Configuration----TeamCityOctopus.jpg" />

<img src ="https://lh4.googleusercontent.com/-DxsEE4vWejk/VK08KDHqhGI/AAAAAAAADkM/bokpxHfv0lI/w1044-h492-no/JumpstartPakistan----jsp-Dev----1--31-Dec-14-16-07----Build-Log-%E2%80%94-TeamCity.jpg" />

<img src="https://lh4.googleusercontent.com/-8051eiR2hqQ/VK08LJR0S0I/AAAAAAAADkk/wIEO5eM3Rx8/w1044-h492-no/Plugins-List-%E2%80%94-TeamCity.jpg" />

<img src="https://lh4.googleusercontent.com/-HgycLiQB-VE/VK08HN9MQ3I/AAAAAAAADjk/RzN8533XJkI/w1044-h492-no/Create-Build-Configuration-%E2%80%94-TeamCity.jpg" />

<img src="https://lh4.googleusercontent.com/-gawLVzorkio/VK08JhJiFNI/AAAAAAAADkQ/6Wz8eiDJSn4/w351-h563-no/Edit-VCS-Root----TeamCity.jpg" />

<img src="https://lh5.googleusercontent.com/-Kk6UsR-yd-8/VK08Ij1p8iI/AAAAAAAADj4/9TOuhJi_2S0/w1044-h492-no/Diagnostics---Browse-Data-Directory-%E2%80%94-TeamCity.jpg"/>

<img src="https://lh6.googleusercontent.com/-8ywvuLLHDpg/VK08MbRYi9I/AAAAAAAADk0/LT3lOGdbdfg/w934-h563-no/gitpush.jpg" />
<img src="https://lh5.googleusercontent.com/--M2by-kAbPA/VK08NzqncBI/AAAAAAAADlA/vO2a0vnO9kE/w686-h563-no/jsp-Dev-Configuration----TeamCity_build_step.jpg" />

<img src="https://lh6.googleusercontent.com/FD74QCTbIywNS-ZKDWKV-3MQz41_8zdgF9gvrhzIcek=w1044-h492-no" />

<img src ="https://lh5.googleusercontent.com/-QgCOHh426Qo/VK08KQ8becI/AAAAAAAADkU/JRsK-3fkc6w/w1044-h492-no/JumpstartPakistan-deployment-process---Octopus-Deploy.jpg" />

<img src ="https://lh5.googleusercontent.com/-xUsarFDboeI/VK08KmN0dvI/AAAAAAAADkc/314u0zZYqXA/w1044-h492-no/JumpstartPakistan-variables---Octopus-Deploy_varriables.jpg" />

<img src="https://lh5.googleusercontent.com/-2ncogbfvwlc/VK08LynNuPI/AAAAAAAADks/Mb0RAJnMsJI/w1044-h492-no/TeamCity-Packages---Octopus-Deployfeed.jpg" />

<img src="https://lh5.googleusercontent.com/-izLzdy0drnQ/VK08HOYFABI/AAAAAAAADjs/4hTmdXlhWy4/w347-h562-no/Deploy---Octopus-Deploy_step_deploy.jpg" />

<img src="https://lh4.googleusercontent.com/-7BkVrcQkcc4/VK08HwRAiKI/AAAAAAAADj0/DNP6ANsOWvk/w1044-h492-no/Development-settings---Octopus-Deploy.jpg" />


