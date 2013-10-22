---
layout: post
title: "MongoDB Setup On Windows 8"
date: 2013-10-22 13:15
comments: true
categories:
- MongoDB
- NoSQL
- Windows
- Tips
- Development
- Database
---

I am very much into learning new tools and burning hours of my life trying to figure them out. To track whats new on development horizon and technology I tend to keep my eyes on sessions, conferences, blogs and screen-casts. 

In past few days I wanted to explore no-sql options two in particular RavenDB and MongoDB. I have successfully completed the environment setup for raven but didn't use it in any project until now. On the other hand I have built a new website for my current employer using MVC4 and MongoDB. I have learned a a lot and in this blog post I will share few commands to setup mongoDB and deploy it on remote server.

You can download MongoDb zip file from http://www.mongodb.org/downloads. I picked 64bit version of it.

## Installing MongoDb as windows service

To install MongoDB using your command prompt navigate to the bin folder in my case it was on following path:

{% codeblock %}
	D:\mongodb\bin>
{% endcodeblock %}

Then run following command to install it

{% codeblock %}
	D:\mongodb\bin>mongod --dbpath=D:\mongodb --logpath=D:\mongodb\log.txt --install
{% endcodeblock %}

Then you can goto windows services and look for MongoDB service and simply start it. If you face any error during installation make sure you launch command prompt as administrator and log.txt file used in above command do exists in your hard drive.

If for some reason you want to un-install the MongoDB service run following command in command prompt after stopping service from system services.

{% codeblock %}
	D:\mongodb\bin>mongod --remove
{% endcodeblock %}

##GUI to manage MongoDB

You can interact with MongoDb database and collections using command prompt it will make you master of the little quires against small frequent tasks. In my case I wanted some simple GUI to perform simple tasks and I came across [RoboMongo](http://robomongo.org/).


Installation is simple once this tool is installed and you have your MongoDb service up and running. click on the create button showing in following screen.

![Robo Mongo Connection Screen](https://lh4.googleusercontent.com/-W5SYuoYBfqE/UmZNepJZPkI/AAAAAAAACcQ/LVaMJiW2k50/w668-h410-no/roboCreate.jpg)

Proceed with defaults in address I have localhost and using port 27017. After connection is created you can click on the connect button and it will show you following screen listing with your databases and collections.


![Robo Mongo Showing Databases and Collections](https://lh6.googleusercontent.com/fJjuZWRgwzWSRNwF0HzVw4bJ8JryEKLuAwWWIaKlfEY=w1183-h737-no)


##Deployment

After completing v1.0 I have been asked to deploy our new web site on remote server. Asp.net deployment was not a big deal but to deploy local MongoDb database onto remote I had to read about two commands *mongodump* and *mongorestore*

First to create a backup file of my local mongoDB database I run following command 

{% codeblock %}
	mongodump --db DBName
{% endcodeblock %}

Above command will generate called DBName under MongoDB_Installation_Folder/bin/dump inside generated folder you will find *.bson* files for all the collections your database contains. I have uploaded this folder on remote server.


Now to restore MongoDB on remote server I used mongorestore command syntax is simple you need to supply foldername/dbname to restore

{% codeblock %}
	mongorestore dump/DBName
{% endcodeblock %}

Once restore is completed successfully you can check your database on remote using RoboMongo.

I hope this will help someone starting with MongoDB thank you for reading my blog.