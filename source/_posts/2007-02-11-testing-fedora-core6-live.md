---
layout: post
title: Fedora Core6 live-configuring internet by spoofing mac address
date: 2007-02-11 13:29
comments: true
categories:
- linux 
- tips
- networks
---
hi

Guyz i am writing this post while using fedora core 6 live cd and it took 2 hours to make internet working on this live distro.

I have acer 1642ZNWLCi with 1.7 ghz, 512 mb, and 60 gb HDD.  I have a cabel connection and my cabel operator is keepig record of my mac address and only one mac address is allowed so to run internet on all my pc i have to spoof mac addresss. If you like to spoof your mac address for fedora core 6 live follow these steps.

1. get su by typing su in shell and hit enter.

2. run /sbin/ifconfig and check your ethernet details check its on enth0 or eth1 interface for my case its eth1.

3. then run /sbin/ifconfig eth1 down hw ether 00:xx:xx:xx:xx:xx

4. then run /sbin/ifconfig eth1 up

5. finally run /sbin/ifconfig  to check if your mac address changed or not. for my case its changed.

now its all set up fire your browser like firefox or firefox ;) and visit any site you want like http://www.najam.wordpress.com/

Best of luck now

Regards

Najam Sikander Awan
