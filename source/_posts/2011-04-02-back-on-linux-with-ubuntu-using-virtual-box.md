---
layout: post
title: Back on linux with ubuntu using Virtual Box
date: 2011-04-02 05:26
comments: true
categories:
- linux
---
Well for some experiments that involved git and curl I was coming across the windows problem I was trying to make my way using cygwin but after few stuck I always get stuck. Everyone's recommended solution  was using linux OS so I have download virtual box created a virtual machine and then installed ubuntu iso 10.10 32 bit. Now as I am trying to get some softwares like chrome and vim I got few errors in package manager saying something like waiting for jockey to end. Google comes to rescue in terminal I run following commands:

<pre>
ps -e | grep jockey
sudo kill process_id
</pre>

Second big problem was I wanted full screen when using ubuntu solution that I found in some forum is following:

The nut of what you will be doing:

1. Install Ubuntu on VB.
2. After install and restart, go to the 'Devices' menu for VirtualBox.
3. Select 'Install Guest Additions'.
4. Open Terminal in Ubuntu.

Type:
cd /media/cdrom0 (this puts you to the cdrom directory where you just mounted guest additions)
Press enter then type:
dir (this shows you what's inside this directory.)
Press enter then type:
sudo sh ./VBoxLinuxAdditions-x86.run (this is what you would type if you have an x86 machine, typical. If you have an AMD use that one, and so forth.)

5. Wait for update to complete.
6. Once complete, shut down Ubuntu.
7. Restart VirtualBox
8. Boot up Ubuntu.
9. Once booted, press cmd+F for fullscreen or cmd+L for seamless.


Best,

Najam Sikander Awan

