---
layout: post
title: "Continuous Integration &amp; Deployment For .Net Projects TL;DR"
date: 2014-12-31 20:05
comments: true
categories: 
---

I have been involved with development of small and large web applications using asp.net technologies currently using MVC to get the job done. I might have been using latest technologies and tooling but my workflow was from ancient times. Recently I got so much obsessed with automation I thought it's good time to improve my end to end workflow. 

I have been busy with testing tools and products in automation space and following tech gurus to understand how they are avoiding the deployment hell. I came across following and with few days of work I decided to go all in. 

- PowerShell 
 - Managing Remote Server Desired State
 - Notifications (Twitter Bot)
- Slack
- GitLab
- TeamCity
- Octopus Deployment
 
### If you are thinking wow it's alot to get automated workflow for your development sprints then you can master powershell to do it all. I have seen few talks that only used powershell only to achieve everything you will see in this post.

First of all I wanted my team to start using git for version control and since internet bandwidth is expensive we needed local git server to mange repositories. I went for GitLab we are running it on ubuntu 12.04LTS server its very stable and we loved it. My team loved it specially devs who have been banging their heads with SVN. Since early adopters of our team were happy we thought this is the only automation we need. Don't judge us remember there was a time we were using zip files to have back and code sharing.

### Problem : Who Broke The Code?
First pain we felt was about commit that might introduce the compile time errors and other team members don't know if its ok to pull the code? Our first response was before pushing code make sure you compile it. If you love your team member so much pull your own code after push and make sure its still compiling. 

This activity was a burden and my team members call this pain "Push-Pa" that means Push and Pull loop they are having while sharing code/features with each other. While doing Push-Pa we tried to integrate Teamcity with our local gitlab server.

Now our teamcity server is monitoring Dev branch on gitlab server for latest code and once code is pushed teamcity download the code and compile is using visual studio .sln file. If you have notification/reporting setup properly you can have email notifications about teamcity compile result.

Next in line was to deploy code automatically to our staging server (MS-DC-05) for that octoplus is installed and linked with Teamcity. So once teamcity is done with code compilation and making deployment package as a Nuget Package, Octopus server pull the code and start pushing code to staging server (MS-DC-05). 

I was happy from my web administration console I observed the progress from code commit to deployment on staging but my team was missing that fun specially the chosen one "QA Guy".

Our QA guy was keep pinging devs if code with fixes has been pushed to staging server so he can start testing even devs need to know if someone have fixes or latest release for deployment. First step to solve this problem I have asked my team to start using "Slack" it's an amazing tool for team chat. Second step was to integrate octopus deploy with slack so our dev chat room can show notifications if some latest build is deployed and available for testing.  I have configured octopus to run some custom powershell script which run after deployment and these script test website for errors. Result of this testing is also shared into our dev chat room.



## Source Control: GitLab

## Installing TeamCity

## Installing Octopus Deploy

## Configurations

## Results 





Install teamcity 
========================

Sql Server as database
	download sqljdbc package from http://confluence.jetbrains.com/display/TCD9/Setting+up+an+External+Database#SettingupanExternalDatabase-MicrosoftSQLServer
	at time we had two options 4.0 and 4.1. if you download and unzip 4.1
	inside it you will find 4.0.jar copy it to lib folder of teamcity
	installation.
	
	Choose sql server our database server is (ms-dc-02\sql2008). for host
	i put ms-dc-02 and for instance sql2008, use sql authentication and
	supply username and password. make sure empty database is created before you
	proceed with teamcity wizard. if connected with db it will show you terms and
	conditions. 

	Next teamcity will prompt you for admin user and password.


Creating Build: Gitlab
	create project (jumpstartpakistan)
	create  build configuration
	version control settings: make settings like screenshot
	Build steps:
		building using solution file:

		octopack plugin install:
		copy Octopus.TeamCity.zip into teamcity plugins folder located
		at C:\ProgramData\JetBrains\TeamCity\plugins you can also
		upload plugin from teamcity admin web panel. After installation restart
		teamcity server service from windows services. 

		modify build step with vs sln file as per screenshot


Install octopack
	Create new project
	install tenticle on some pc (make sure proxy is off, than on server
add that machiene by hostname)
	Add nuget feed of teamcity with teamcity credentials. test by
searching packages. Make sure your teamcity has nuget feed available.
screenshot
	Create environment (development)
	then you need to defien process for this project. process has steps. 
	create your first step for deployment. Process -> add step.
