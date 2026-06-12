---
title: "No Game sounds in 64bit"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxted on 2006-01-15
Searched threads for a solution.  No luck.  I am getting sound at logon and logoff, however no sounds for games (planet-penguin, bzflag, or any others).  CD player sound works.


Any ideas?

Thanks,

---

### Post by BoyOfDestiny on 2006-01-16
[QUOTE=linuxted]Searched threads for a solution.  No luck.  I am getting sound at logon and logoff, however no sounds for games (planet-penguin, bzflag, or any others).  CD player sound works.


Any ideas?

Thanks,[/QUOTE]

Open a terminal and type

sudo killall esd

If that solves it, go ahead and in Preferences-> Sound and uncheck the box "enable sound server"
and in Preferences -> Multimedia Selector choose alsa instead of ESD.

Also, I've found it helpful to install libsdl-debian all (something like that, search in synaptic) and alsa-oss...

Best of luck!

---

### Post by DRF on 2006-01-16
With the SDL based games, of which planet penguin is one, a fix I found that what works well on my computer is opening up synaptic and installing the package:
libsdl1.2debian-all (I think this is the correct package it should be quite obvious).
This should want to uninstall libsdl1.2debian-oss which is ok, and now the SDL games will hopefully work properly.

Hope this fix works for a few of your games, if not just ask here.

Daniel

---

### Post by linuxted on 2006-01-16
[QUOTE=BoyOfDestiny]Open a terminal and type

sudo killall esd

If that solves it, go ahead and in Preferences-> Sound and uncheck the box "enable sound server"
and in Preferences -> Multimedia Selector choose alsa instead of ESD.

Also, I've found it helpful to install libsdl-debian all (something like that, search in synaptic) and alsa-oss...

Best of luck![/QUOTE]

This worked great, thanks!!!!

---

### Post by poiuytr on 2006-01-21
Hmmm, I am having the same problem.  I can play and mp3 just fine.  But if I play a game like planet penguin racer, there is no sound.

I have tried all of the above - I have killed ESD; I have installed libsdl1.2debian-all (which was something which ot my mp3 sounds working), and I have alsa.oss installed, too.

Any other ideas?  Do I need lib-whatever-alsa intalled, if I already have libsdl1.2debian-all installed?

Other ideas?  Thanks.

---

### Post by colsinc on 2006-05-04
I was also having trouble with sound in bzflags and pp racer.  I could get it working, but only with everything else closed, otherwise they didn't seem to see any soundcard, installing libsdl1.2debian-all made it work perfectly with all my other programs running.  :) thanks

---

