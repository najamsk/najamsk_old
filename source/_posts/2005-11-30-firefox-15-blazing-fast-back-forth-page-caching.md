---
layout: post
title: Firefox 1.5 - blazing fast back &amp; forth page caching
date: 2005-11-30 23:43
comments: true
categories:
- tips
---
<p>1. Download and install the latest Firefox<br />
* Linux<br />
* MacOS X<br />
* Windows<br />
2. Run Firefox and type 'about:config' in the location bar.<br />
3. Right-click on the main content area.<br />
1. Select New<br />
2. Select Integer<br />
4. Enter the preference name 'browser.sessionhistory.max_viewers' and click OK.<br />
5. Enter '5' and click OK.<br />
6. Shutdown and restart Firefox.<br />
7. Take the feature for a test drive!<br />
1. View a large web page with lots of elements, like planet.mozilla.org or mozillaZine feedHouse.<br />
2. Next, go to another page, like Slashdot.<br />
3. Click Firefox's Back button. If the preference is properly enabled, the previous page should appear instantly.<br />
4. Click the Forward button to see it work again with Slashdot.
</p>
