---
title: "[WINE 64BIT] problem with first run"
date: 2007-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sockerdrickan on 2007-09-30
robin@PC:~$ winecfg
wine: creating configuration directory '/home/robin/.wine'...
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : legacy
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/robin/.wine'.
robin@PC:~$ wineserver: could not save registry branch to /home/robin/.wine-amPFlL/system.reg : No such file or directory
wineserver: could not save registry branch to /home/robin/.wine-amPFlL/user.reg : No such file or directory


:lolflag:

What's wrong?

---

### Post by Kilz on 2007-09-30
looks like wine cant make its .wine folder. What versions of wine and Ubuntu are you running?

---

### Post by Sockerdrickan on 2007-09-30
7.10 current and the wine that comes in the repos

---

### Post by Kilz on 2007-09-30
> **Tux0r said:**
> 7.10 current and the wine that comes in the repos

Did you report this bug?

---

### Post by Sockerdrickan on 2007-09-30
No, could this have something to do with me first installing 7.04 deb (0.9.46) and getting the same error?

---

### Post by Kilz on 2007-09-30
Nope, because the newer install will overwrite the old. You could completely remove the package and try again. But I think this isnt in the wine packages but the system. I would report it.

---

### Post by sisslack on 2007-10-02
I'm having the same problem.  Although I did shorten my error message by running wineprefixconfig, which did create my .wine directory in my home folder.  But when I run winecfg, it still crashes with this error message:

Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : legacy
Segmentation fault

So it looks like the problem isn't creating the .wine directory but somewhere in fontconfig.  I'll play around with this a little more tonight and post if I find a solution.

Note:
I had wine working in 64-bit before but I recently reinstalled and this time I installed the proprietary video driver before I installed wine.

---

### Post by Sockerdrickan on 2007-10-02
That's the exact problem I have.

---

### Post by Cirvaazny on 2007-10-02
I had the same problem you had described in your first post Tux0r.  I kept getting that Segmentation fault error.  I just now got it fixed.  I don't know if it will fix your problem, but what worked for me was first, uninstalling wine and my nVidia drivers using envy (remove/clean).  Then reinstalling wine w/o the drivers installed and getting it configured first (using default drivers).  Then I used envy install the custom drivers for my nVidia card.  I can finally configure and use wine now.  It seems there might be some kind of problem with wine and some of the video drivers (at least for me).  :confused:

---

### Post by Sockerdrickan on 2007-10-03
It works now yes, yesterday I re installed my drivers manually and then it worked lol :D :guitar:

---

### Post by sisslack on 2007-10-03
Well I'm glad to see you guys figured it out!  I was doing some extensive troubleshooting last night myself and I believe I can shed some more light on this.

It looks like its a compatibility issue between WINE and the NVIDIA 32bit OpenGL libraries. At one point I recompiled my drivers without the 32bit OpenGL libraries and I was able to run winecfg and notepad without that "Segmentation fault (core dumped)" error.  Of course I can't play the game I want to play without those libraries. :(

So it looks like we all came to the same conclusion.  And if I were to venture a guess I would say we are all running similar graphics cards...  GeForce 8800 GTS in my case, and I see Tux0r is using the same.

I'll try your fixes when I get a chance, unfortunately I'll be away for a few days.  For a moment there I was thinking about dual booting...  32 and 64 bit Ubuntu that is, not XP! :-D

---

### Post by Sockerdrickan on 2007-10-03
64bit is cool now when I have it configured right!

Please, read my how2 for nVidia install:

GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start

:guitar:

---

### Post by sisslack on 2007-10-09
I'm up and running now too! :)  I followed very similar steps to the ones above, that I found in the Nvidia forum, but I had even done that the 1st time around.  

What seemed to fix the problem was uninstalling the driver or reinstalling without the 32-bit OpenGL libraries, running winecfg, then reinstalling the full driver with the 32-bit libs.  When you install be sure to follow those steps that Tux0r outlined above.

According to the folks in the WINE community it's probably a library/driver issue and that uninstalling (or reinstalling without the 32-bit libs) actually removed some other broken libs as well.

---

