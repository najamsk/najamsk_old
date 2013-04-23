---
layout: post
title: How to enable full multimedia capabilities on Suse 10.2 using the xine engine
date: 2007-03-12 10:36
comments: true
categories:
- linux
---
NOTE: The package manager in Suse 10.2 appears to be working a lot better than the one in 10.1, so this time we will be using YAST and not SMART to install the required packages.

The first step in resolving the multimedia issue is to setup additional YAST <a href="http://www.linuxquestions.org/questions/showthread.php?t=509097#" target="_top"><u><font size="2"></font><font face="Verdana, Arial, Helvetica, sans-serif"></font><font color="#0000ff">software</font></u></a> sources. The software repositories used in this howto, are <a href="http://packman.links2linux.org/" target="_blank">Packman</a> and <a href="http://linux01.gwdg.de/%7Epbleser/" target="_blank">Guru</a>. If possible, please use a mirror instead of the main download site to prevent overloading one download location. The mirrors for Packman are listed <a href="ftp://packman.links2linux.de/pub/packman/MIRRORS" target="_blank">here</a> and the ones for Guru are on the section titled "Mirrors" on this <a href="http://linux01.gwdg.de/%7Epbleser/" target="_blank">page</a>.

<strong><u>Adding the Packman Repository</u></strong>
<ol>
	<li>
<p style="margin-bottom:0;">Start YAST -&gt; Software -&gt; 	Installation Source and click on "add"</p>
</li>
	<li>
<p style="margin-bottom:0;">Select HTTP or FTP as the protocol 	and click on "next"</p>
</li>
	<li>
<p style="margin-bottom:0;"><a name="KonaLink1"></a>In the box 	that is labeled "<a href="http://www.linuxquestions.org/questions/showthread.php?t=509097#" target="_top"><u><font size="2"></font><font face="Verdana, Arial, Helvetica, sans-serif"></font><font color="#0000ff">Server</font></u></a> 	Name" enter the address of the ftp or http server of your 	mirror e.g. mirror.geht-schon.de or ftp.uni-erlangen.de. Please do 	not enter the preceding http:// or ftp://.</p>

<p style="margin-bottom:0;">Working Example:
<strong>Server Name: 	mirror.geht-schon.de</strong></p></li>
	<li>
<p style="margin-bottom:0;">In the box labeled "Directory 	on Server", enter the path to the packman directory for Suse 	10.2 e.g. /packman.links2linux.de/suse/10.2 or 	/pub/mirrors/packman/suse/10.2
Working Example:
<strong>Directory 	on Server: /packman.links2linux.de/suse/10.2</strong></p></li>
	<li>Once thats done, click on the finish button and depending on 	your net connection YAST may take a few seconds or a few minutes to 	setup the repo.</li>
</ol>
NOTE: If you are asked about a "KEY" please choose the option to import the key.

<strong><u>Adding the Guru Repository</u></strong>

*The process is similar to adding the packman repo, the only difference being the mirros, so I won't delve into that. Follow the instructions above and just substitute server names and directory paths.

Working Example

<strong>Server Name: </strong><a href="ftp://ftp.gwdg.de/"><strong>ftp.gwdg.de</strong></a>
<strong>Directory on Server: /pub/linux/misc/suser-guru/rpm/10.2/RPMS</strong>


<strong><u>Installing the required packages</u></strong>

Once the mirrors have been setup do the following,
<ol>
	<li>
<p style="margin-bottom:0;">YAST -&gt; Software -&gt; Software 	Management</p>
</li>
	<li>
<p style="margin-bottom:0;">Search for xine and when the 	search results show up:</p>

<ul>
	<li>
<p style="margin-bottom:0;">Select libxine1 for installation</p>
</li>
</ul>
</li>
	<li>
<p style="margin-bottom:0;">Select xine-lib for deinstallation</p>
</li>
	<li>
<p style="margin-bottom:0;">If you want amarok to use the xine 	engine, select "amarok-xine" for installation if it is not 	already installed</p>
</li>
	<li>
<p style="margin-bottom:0;">If you use totem and prefer to use 	xine instead of gstreamer as the backend, select libxine1-gnome-vfs 	for installation</p>
</li>
	<li>Search for w32codec and select it for installation</li>
</ol>
<p style="margin-bottom:0;">Once thats done, click accept and YAST should install the packages for you and hopefully you can play mp3, mp4, wmv etc.

NOTE: We did not use any packages from the Guru repository, but it has some apps e.g. Kmplayer, amarok-xmms, and others as well as not multimedia packages that you may find useful.

<strong><u>Playing encrypted DVD discs</u></strong>

Xine cannot play encrypted dvd discs without some help. If you want to do this, then go to <a href="http://download.videolan.org/pub/libdvdcss/1.2.9/rpm/" target="_blank">videolan</a> and download the libdvdcss rpm. Install the rpm by doing
</p><p style="margin-left:0.24in;margin-right:0.24in;margin-bottom:0.02in;"> Code:</p>

<pre style="border:1px solid #000000;margin-left:0.24in;margin-right:0.24in;text-align:left;padding:0.04in;">#rpm -Uvh libdvdcss2-1.2.9-1.i386.rpm</pre>
<p style="margin-left:0.24in;margin-right:0.24in;">
NOTE: Using libdvdcss maybe illegal in your country, so please check with the authorities before downloading and using it. We will not be held responsible or accountable if you use this software where you are not supposed to.

<strong><u>A note on package management</u></strong>

If you have problems with your package manager, it maybe a good idea to drop back to the old Suse package manager instead of the Zenworks related tools. To do this do
<ol>
	<li>
<p style="margin-bottom:0;">YAST -&gt; Software -&gt; Software 	Management</p>
</li>
	<li>
<p style="margin-bottom:0;">On the "Filter" box, 	select "Patterns"</p>
</li>
	<li>
<p style="margin-bottom:0;">Navigate to the "Enterprise 	Software Management" pattern and deselect it and all the 	packages listed on the right</p>
</li>
	<li>Click accept and once YAST has completed the changes, close 	it and reboot.</li>
</ol>
When the system starts, you will notice that you have different tools for updating the system although YAST will work as usual but using the old backend.

NOTE: As usual, any comments, addition and correction are welcome.

Have fun.  <img src="http://linuxquestions.cachefly.net/images/questions/images/smilies/wink.gif" align="bottom" height="15" width="15" /></p>
