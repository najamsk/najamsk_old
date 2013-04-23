---
layout: post
title: Vychat alternative for my suse 10.2 laptop
date: 2007-03-12 10:43
comments: true
categories:
- linux
---
<p style="margin-bottom:0;" align="left"><font size="3">After switching to suse what I badly missed is vychat a very popular LAN chat client </font></p>
<p style="margin-bottom:0;" align="left"><font size="3">that support many useful functions such as file transfer and real time chat capabilities. All of my network users use windows and they communicate and file transfer with each other using vychat so after setting up suse I googled and end up with many vychat clones for unix and linux. Below is the list of some clones</font></p>

<p style="margin-bottom:0;" align="left">
<ol>
	<li>
<p style="margin-bottom:0;" align="left"><font size="3">Trix</font></p>
</li>
	<li>
<p style="margin-bottom:0;" align="left"><font size="3">Vqcc-gtk</font></p>
</li>
	<li>
<p style="margin-bottom:0;" align="left"><font size="3">Vyqchat</font></p>
</li>
</ol>
</p><p style="margin-bottom:0;" align="left">
</p><p style="margin-bottom:0;" align="left"><font size="3">I have successfully installed trix and vqcc-gtk but the only problem with them is that they were not showing any users. So I decided to take help from linux irc help channels and from there a kind guy named yasir told me that i have to either disable firewall or add vychat ports to my susefirewall. </font></p>

<p style="margin-bottom:0;" align="left">
</p><p style="margin-bottom:0;" align="left"><font size="3">After disabling firewall i get all of my users in trix and vqcc-gtk. You can turn on and off firewall on suse by typing following commands in shell as root.</font></p>

<p style="margin-bottom:0;" align="left">
</p><p align="left"><font size="3"><strong>Turning firewall off</strong>
rcSuSEfirewall2 stop</font>

</p><p align="left"><font size="3">
<strong>turning firewall on </strong>
rcSuSEfirewall2 start</font>
</p><p align="left">&nbsp;</p>

<form>
<p class="enclosure-inner enclosure-photo">
</p><p class="enclosure-list">
</p><p class="enclosure-item photo-asset last">
</p><p class="enclosure-image">                          <a href="http://najam.vox.com/library/photo/6a00c2251d69c9549d00cd97177f0c4cd5.html"><img src="http://a4.vox.com/6a00c2251d69c9549d00cd97177f0c4cd5-200pi" alt="TriX" /></a>
</p><p class="enclosure-image-actions"><a href="void 0;" class="command-edit-asset" title="Edit"><img src="http://aka-static.vox.com/.shared:v23.8:vox:en_us/images/icons/enclosure-edit.gif" alt="Edit" /></a><a href="void 0;" class="command-edit-enclosure-format" title="Format"><img src="http://aka-static.vox.com/.shared:v23.8:vox:en_us/images/icons/enclosure-format.gif" alt="Format" /></a><a href="void 0;" class="command-delete-enclosure" title="Remove"><img src="http://aka-static.vox.com/.shared:v23.8:vox:en_us/images/icons/enclosure-remove.gif" alt="Remove" /></a></p>


<p class="enclosure-meta">
</p><p class="enclosure-asset-name"><a href="http://najam.vox.com/library/photo/6a00c2251d69c9549d00cd97177f0c4cd5.html" title="TriX">TriX</a></p>


</form><!-- end enclosure -->

<p style="margin-bottom:0;" align="left"></p>
