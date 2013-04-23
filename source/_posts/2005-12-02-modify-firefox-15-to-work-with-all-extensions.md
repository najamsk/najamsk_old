---
layout: post
title: Modify Firefox 1.5 to work with all extensions
date: 2005-12-02 13:12
comments: true
categories:
- firefox
---
<p>For all of those who just downloaded Firefox 1.5 and canât get your extensions to work. This is a simple modification of Firefoxâs configuration to trick the extensions to work. No need to manually edit the extensions to get them to work. Currently all the extensions I use work except the bookmark sync extension that I so dearly want to.</p>
<p>1. At the location bar, enter: about:config. This will show you a list of Firefox internal preferences.<br />
2. Right-click on the list, select New &gt; String<br />
Enter âapp.extensions.versionâ? (without quotes) for the preference name.<br />
3. Then, enter â1.0â? (without quotes) as the value for app.extensions.version.<br />
4. Restart Firefox 1.5, then enable those disabled Firefox extensions.<br />
5. Restart Firefox 1.5 again to active the extensions. Done.
</p>
