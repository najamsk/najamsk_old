---
layout: post
title: Realtek HD sound card working
date: 2007-02-20 09:54
comments: true
categories:
- linux
- tips
---
Hi guyz

My sound card working now after installing latest <a href="http://www.alsa-project.org/"><font color="#578fb2">Alsa</font></a> driver, Lib and Utils.

Compile alsa-driver like this:

{% codeblock %}
./configure --with-cards=hda-intel
make
make install
{% endcodeblock %}

and alsa-lib and alsa-util in this order like this:

{% codeblock %}
./configure
make
make install
{% endcodeblock %}

Reboot and there you go!

Regards
Najam Sikander Awan
