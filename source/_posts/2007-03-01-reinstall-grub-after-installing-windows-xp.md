---
layout: post
title: reinstall grub after installing windows xp
date: 2007-03-01 11:15
comments: true
categories:
- windows
---
hi guyz

Today i formated my c drive in which vista was installed and i replaced it with windows xp after installing win xp into my c drive my boot loader is disappeared as expected.

Fixing  grub  (boot loader) is simple insert your suse 10.2 dvd or frist cd into drive and boot from it choose "Rescue System" after loading some stuff system will take you into command prompt
<ol>
	<li>first I list all of my partitions by using fdisk -l
<pre style="border:1px inset;overflow:auto;width:98%;height:210px;margin:0;padding:3px;">  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2167    17406396    7  Fat32
/dev/sda2            5822       12161    50926050    f  W95 Ext'd (LBA)
/dev/sda3            2168        5821    29350755    c  W95 FAT32 (LBA)
/dev/sda5            5822        6076     2048256    b  W95 FAT32
/dev/sda6            6077        6270     1558273+  82  Linux swap
/dev/sda7            6271        7837    12586896   83  Linux
/dev/sda8            7838       12161    34732498+  83  Linux</pre>
</li>
	<li>Then enter grub</li>
	<li>root (hd0,6)</li>
	<li>setup (hd0)</li>
	<li>quit</li>
	<li>reboot :)</li>
</ol>
