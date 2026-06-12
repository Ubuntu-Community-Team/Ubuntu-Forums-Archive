---
title: "Opera 64 bit and 32 bit plugins"
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by papaver on 2006-06-10
Hi.. 

Is it possible to use Opera on amd64 with 32 bit plugins ?   I have both flash and realplayer installed and they don't seem to work at all.  I'm pretty sure the plugins are installed properly because I can get them both working on a firefox32 bit install I have as well .. but im not much of a fan of firefox and want to stick with opera..  In my opera install all I get is a blank screen when i try to look at google video or [www.homestarrunner.com](www.homestarrunner.com).  There used to be a plugin's missing icon before I installed the plugins.  

Here is ls on the opera plugins dir :

flashplayer.xpt
libflashplayer.so
libnpp.so
libnullplugin.so
mplayerplug-in-gmp.so
mplayerplug-in-gmp.xpt
mplayerplug-in-qt.so
mplayerplug-in-qt.xpt
mplayerplug-in-rm.so
mplayerplug-in-rm.xpt
mplayerplug-in.so
mplayerplug-in-wmp.so
mplayerplug-in-wmp.xpt
mplayerplug-in.xpt
nphelix.so
nphelix.xpt
operamotifwrapper-1
operamotifwrapper-2
operamotifwrapper-3
operaplugincleaner

I have the following in the plugins dirs in opera :

/usr/lib/opera/plugins/
/usr/lib/mozilla/plugins/
/usr/lib/firefox/plugins/
/usr/lib/realplayer/
/usr/lib/mozilla-firefox/plugins/

---

### Post by papaver on 2006-06-11
nm.. I got it working. I had the 64 bit versions of lesstif2, swtiching to 32 bit fixed it.

---

### Post by kuja on 2006-06-11
Isn't Opera 32-bit itself? I've had no problems getting 32-bit plugins working in it... in fact, it's what I turn to when I need support for 32-bit things, namely flash.

---

