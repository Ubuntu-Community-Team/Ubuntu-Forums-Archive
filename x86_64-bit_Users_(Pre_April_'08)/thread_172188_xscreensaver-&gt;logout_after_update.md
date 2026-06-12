---
title: "xscreensaver-&gt;logout after update"
date: 2006-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by suxen on 2006-05-08
Hi, 
after the last update this morning (Xorg and kernel), every time the screensaver starts, I get logged out and all applications are killed. I moved .xscreensaver to .old_xscreensaver and tried to run the configuration tool, but the same thing happened (log out after the configuration window opened).
What can I do?


BTW, this is my .old_xscreensaver:

# XScreenSaver Preferences File
# Written by xscreensaver-demo 4.21 for carsten on Mon May  8 11:36:37 2006.
# [http://www.jwz.org/xscreensaver/](http://www.jwz.org/xscreensaver/)

timeout:	0:10:00
cycle:		0:10:00
lock:		False
lockTimeout:	0:00:00
passwdTimeout:	0:00:30
visualID:	default
installColormap:    True
verbose:	False
timestamp:	True
splash:		True
splashDuration:	0:00:05
quad:		False
demoCommand:	xscreensaver-demo
prefsCommand:	xscreensaver-demo -prefs
newLoginCommand:    gdmflexiserver -sl
newLoginCommand:    gdmflexiserver -sl
nice:		10
memoryLimit:	0
fade:		True
unfade:		True
fadeSeconds:	0:00:02
fadeTicks:	20
captureStderr:	False
ignoreUninstalledPrograms:False
font:		*-medium-r-*-140-*-m-*
dpmsEnabled:	True
dpmsStandby:	0:30:00
dpmsSuspend:	0:45:00
dpmsOff:	1:00:00
grabDesktopImages:  False
grabVideoFrames:    False
chooseRandomImages: False
imageDirectory:	

mode:		random
selected:	-1

...

---

### Post by musicinmybrain on 2006-05-08
I had this problem too. It is due to the updates, but reinstalling your video drivers should fix it (apparently this is often necessary after a kernel / x update).

My guess is you've probably used NVIDIA's installer to compile the latest drivers for your system. Since they're closely tied to the kernel, you'll need to recompile them with method 2 in [this HOWTO](http://www.ubuntuforums.org/showthread.php?t=75074). If you haven't used NVIDIA's installer before, I suspect you won't have the problem, but if you do, then I guess you could try reinstalling in Synaptic, then do the above if that doesn't work. If you use ATI, then reinstall however you ATI people do it. :-)

---

### Post by leberblock on 2006-05-09
i had this problem, too!

@musicinmybrain
thanks for your advice, it works! :)

---

### Post by suxen on 2006-05-09
from leberblock: 
> thanks for your advice, it works! 

Dito.

---

### Post by archis on 2006-05-12
Thanks musicinmybrain, sorted! A good excuse to [install the latest driver]("http://www.nvidia.com/object/unix.html") as well..

---

