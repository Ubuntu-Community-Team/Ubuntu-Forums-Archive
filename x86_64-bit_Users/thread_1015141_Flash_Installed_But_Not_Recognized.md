---
title: "Flash Installed But Not Recognized"
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by CarlosinFL on 2008-12-18
I have installed Adobe Flash and when I go to youtube.com, it tells me that I need additional plugins and offers me Adobe Flash again. However when I goto install the Flash plugin, it tells me it's already installed. I rebooted and restarted Firefox. I am not sure why if it is installed, it wont render or display flash via my Firefox browser.
Using 8.10.

---

### Post by philinux on 2008-12-18
Put this in the firefox address bar then press enter.

```
about:plugins
```

Does it show flash installed

---

### Post by trksh22 on 2008-12-18
I am having the same problem. I can see flash ads but flash movies won't play. Specifically I am trying to get sproutonline.com working for my son :) I just upgraded to Ibex today, and this is the only problem that I have noticed.

This is what showed up for me when I did about:plugins

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

---

### Post by ktrnka on 2008-12-18
Did you install the 64bit alpha flashplugin? If so, make sure you installed it to /usr/lib/firefox-3.0.5/ or whatever version you have and then close completely out of firefox then relaunch it and try youtube again. I have found the 64bit alpha to be more reliable and stable than the 32bit.


Reference [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

---

### Post by Yellow Pasque on 2008-12-18
> If so, make sure you installed it to /usr/lib/firefox-3.0.5/ or whatever version you have
The proper place to put it would be /usr/lib/firefox-addons/plugins

---

### Post by SeePU on 2008-12-18
Did you follow these instructions when you installed it?:

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html")

---

