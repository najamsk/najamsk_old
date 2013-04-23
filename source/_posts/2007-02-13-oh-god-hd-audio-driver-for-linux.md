---
layout: post
title: oh God Hd audio driver for linux
date: 2007-02-13 22:33
comments: true
categories:
- linux
- tips
---
hi guyz;

Well after solving problem for my lan card through mac spoofing next problem that I want to solve now is making sound work on my acer laptop while running fedore core 6 live cd.

Now as i inspect my hardware i get to know that i have a realtek sound card that has hd audio codec Alc 883 now.

to check if your hardware is detected by linux or not you have to run following command in shell

/sbin/lspci

This will list hardware check your sound card vendor and note model for your card.

output of sbin/lspci for my laptop is listed below

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
Now as i googled i come to know that this problem is because alsa bug and older kernel many users with latest kernel like 2.6.17 and fedora 6 live hai kernel 2.6.18 so i think i don't need to play with kernel.

You can also find currently running modules for your sound card by running following into shell/sbin/lsmod

output of /sbin/lsmod is given below

Module                  Size  Used by
i915                   23361  3
drm                    72789  4 i915
ipv6                  267489  12
hidp                   24129  2
rfcomm                 46041  0
l2cap                  31681  10 hidp,rfcomm
bluetooth              58917  5 hidp,rfcomm,l2cap
cpufreq_ondemand       11085  1
dm_mirror              33041  0
video                  21061  0
sbs                    20225  0
i2c_ec                  9281  1 sbs
button                 10961  0
battery                14405  0
asus_acpi              20697  0
ac                      9541  0
parport_pc             31205  0
lp                     17033  0
parport                40841  2 parport_pc,lp
snd_hda_intel          22613  2
snd_hda_codec         154049  1 snd_hda_intel
joydev                 13697  0
snd_seq_dummy           8133  0
snd_seq_oss            37185  0
snd_seq_midi_event     11841  1 snd_seq_oss
snd_seq                57137  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device         12621  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            46561  0
snd_mixer_oss          20545  1 snd_pcm_oss
snd_pcm                80325  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ipw2200               112037  0
snd_timer              27077  2 snd_seq,snd_pcm
pcspkr                  7361  0
serio_raw              11205  0
snd                    57029  13 snd_hda_intel,snd_hda_codec,snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
8139too                31169  0
8139cp                 28609  0
i2c_i801               11853  0
soundcore              14113  1 snd
mii                     9665  2 8139too,8139cp
snd_page_alloc         14281  2 snd_hda_intel,snd_pcm
i2c_core               25537  2 i2c_ec,i2c_i801
ieee80211              34953  1 ipw2200
ieee80211_crypt        10433  1 ieee80211
ext3                  136009  1
jbd                    63337  1 ext3
squashfs               49093  1
dm_snapshot            21357  1
dm_mod                 61529  6 dm_mirror,dm_snapshot
loop                   20297  134
uhci_hcd               27725  0
ehci_hcd               35661  0
ide_cd                 42337  3
cdrom                  38625  1 ide_cd

Now 2nd thing is to check your alsa driver version now i don't how to check that :( currently stuck on that i don't know from where to download alsa driver for fedora 6 live and then how to make it work and i don't want to run fedora 6 live on my laptop i just want all the functionality while running it with cd.

Please help me out here.

Check <a href="http://najam.wordpress.com/2007/02/13/my-acer-aspire-1642znwlci/" title="My laptop configuration">my laptop specification</a> if you need to know them to solve this problem.

Regards

Najam Sikander Awan
