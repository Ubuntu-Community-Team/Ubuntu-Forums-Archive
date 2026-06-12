---
title: "flash persisting after firefox crash"
date: 2008-08-28
forum: x86 64-bit Users
---

### Post by tamman2000 on 2008-08-28
I have been getting a strange behavior out of flash on my AMD64 kubuntu 8.04 box with firefox 2.

Sometimes when I am doing a whole bunch of things at once ff will freeze (say if I try to close a notification box and change tabs in rapid succession).  So I kill the firefox process...  Sometimes I get these flash windows that stick around.  They are on all desktops, they have now window decorations...  they are always on top of all other windows.

The only way I found to get rid of them is to restart kde.  That is extremely annoying.  Does anyone else see these things?  Is there something I can do to make them stop happening?  Is there a way to get rid of them without having to restart kde?

Thanks.

P.S.  I am attaching a screenshot in case my description is inadequate.

---

### Post by lovinglinux on 2008-08-28
I have problems with Firefox 3 on 32-bit, specially when  switching tabs while something is loading, but I don't get any persistent flash windows. I do get a crazy Firefox window like encrypted cable TV channel stripes.

Anyways, I don't know if it will work, but you could try install compiz fusion-icon and use the "Reload window manager" function. It solves similar persistent window anomalies on my system.

---

### Post by rpnet on 2008-08-28
I've experienced the same thing on 64 bit, 8.04, kubuntu with compiz.  I usually solve it by finding the flash player:

ps aux | grep flash

xxxxx   14376  8.0  0.8  77704 18168 ?        Sl   20:49   0:30 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-nonfree/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/7583-5

and killing that process.


Cheers!

---

### Post by tuxxy on 2008-08-29
Open system monitor and locate the processes to kill them, I think this is a KDE issue, best add it to the list :lolflag:

---

### Post by thestgman on 2009-04-14
It is not a KDE issue, I an using GNOME and I have this bug too. The "kill" solution works within GNOME too.

---

