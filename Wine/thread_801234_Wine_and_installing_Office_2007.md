---
title: "Wine and installing Office 2007"
date: 2008-05-20
forum: Wine
---

### Post by ggsherma on 2008-05-20
Hi there again!

As it would seem wine is not agreeing with me very much so I am having a lot of problems with it.

I am trying to isntall office 2007. I am following [these instructions.](http://www.quicktweaks.com/2008/04/09/install-ms-office-2007-in-linux/)

I have done all of the instructions given to me and have gotten to the point of actually installing Office 2k7, however, it stops 'installing' mid way through and just hangs there. I tested the CD out and it I have successfully installed it on 3 other machines. 

[Here is a screenshot of where it is hanging](http://s21.photobucket.com/albums/b278/DarkenWolfen/?action=view&current=FreezeOffce2k7.jpg)

I have tried to close it out before and re-install it, but then it tells me (once I start to try and install it again) that the process as encountered an error and the application cannot be installed. I also could not remove office 2k7 from the wineremoveal process; hence why I had to get rid of wine completely all together then reinstall it.

Thanks for any help I can get

Geoff

---

### Post by Kinst on 2008-05-20
Well you could try removing wine and compiling wine 0.9.58 from source, that was the old version that worked best way back. I hope this isn't a regression...

---

### Post by ggsherma on 2008-05-20
So I have read. The later versions of wine were better. 

Could you point me to the file I need to install (the older version of wine). 

I do not want to install the wrong thing :)

---

### Post by Kinst on 2008-05-20
Yeah sure.

[http://sourceforge.net/project/downloading.php?group_id=6241&use_mirror=internap&filename=wine-0.9.58.tar.bz2&12473595]("http://sourceforge.net/project/downloading.php?group_id=6241&use_mirror=internap&filename=wine-0.9.58.tar.bz2&12473595")

Then you just follow the readme.

---

### Post by ggsherma on 2008-05-20
In the process of installing it now.

I had to install flex and bison first apparently, so I did that.

It then asked me if I wanted to install it in the root too so I said yes. It seems to be going on for a long time. I hope it does eventually finish installing. o.o

---

### Post by Kinst on 2008-05-20
lol that's normal. Now you know why we use package managers (apt/synaptic).

---

### Post by amoresunaramera on 2008-11-09
sorry for reopening this thread, but i'm experiencing the same challenge.  i looked at the screenshot you posted and my installation stops at about the same point.  i've tried to follow a number of how-tos to no avail.  i'd like to know if using the older version of wine did actually help...?

> **ggsherma said:**
> In the process of installing it now.

I had to install flex and bison first apparently, so I did that.

It then asked me if I wanted to install it in the root too so I said yes. It seems to be going on for a long time. I hope it does eventually finish installing. o.o

---

