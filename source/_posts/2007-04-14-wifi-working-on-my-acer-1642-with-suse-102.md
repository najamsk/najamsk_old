---
layout: post
title: Wifi working on my acer 1642 with suse 10.2
date: 2007-04-14 17:41
comments: true
categories:
- inventory
---
<p>Hi,</p><p>phew after lots of search finally my acer 1642 ( <a href="http://najam.wordpress.com/2007/02/13/my-acer-aspire-1642znwlci/">view specifications</a> ) laptop with suse 10.2 communication with Access Point. :D</p><p>Intel
PRO/Wireless 2200BG is my wireless card and its detected by suse 10.2
but as i turn my wifi on led is not lightening up and nothing works&nbsp; as
i searched&nbsp; i found that suse 10.2 includes driver for my wireless lan
card but firmware is missing so all i have to do is install proper
firmware for my card.</p><p>Some forums mentioned that for suse10.2 and Intel PRO/Wireless 2200BG card proper firmware is version 3 and all i have to do is <a href="http://ipw2200.sourceforge.net/firmware.php">download</a> it and extract it into /lib/firmware.  Reboot.</p><p>After reboot my led lighten up and i installed some packages like knetworkmanager from yast to manage my wireless connections.</p>Regards<br />Najam Sikander Awan<br /><br /><p class="poweredbyperformancing">Powered by <a href="http://scribefire.com/">ScribeFire</a>.</p>
