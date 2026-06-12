---
title: "Wow using nvidia beta 310.14 thread optimized drivers"
date: 2012-10-16
forum: Wine
---

### Post by Tweak42 on 2012-10-16
Good news for nvidia users, I just tried out the latest beta nvidia drivers 310.14 that have threaded optimization and they do make very measureable impact on performance if you enable that feature.

This is using drivers from the bleeding edge xorg-edgers PPA so use at your own risk.  Eventually they should hit the X-updates PPA.

Info taken from the botton of:
[ftp://download.nvidia.com/XFree86/Linux-x86/310.14/README/openglenvvariables.html](ftp://download.nvidia.com/XFree86/Linux-x86/310.14/README/openglenvvariables.html)
Launch command I used:
```
LD_PRELOAD="libpthread.so.0 libGL.so.1" __GL_THREADED_OPTIMIZATIONS=1 wine wow.exe -opengl
```



Using System Monitor, Wow.exe now uses about 134% cpu instead of 100% without optimizations enabled.  Also history of cpu core usage is flat instead of alternating up and down.

I don't have anyway to compare it with the old rGL patch since it stopped working for me when MOP launched.

I don't have guildwars 2 but if someone who does wants to test this out and inform GW2 users this maybe what they've been waiting for.

---

### Post by phibxr on 2012-10-20
Confirmed! This actually made me pull my Geforce 9600GT out of an old computer in my closet, since the new NVIDIA-drivers actually makes it perform better than my brick sized brand new Radeon-card.

---

### Post by Bsohm on 2012-11-06
Alright I installed World of Warcraft through crossover and am trying to get this working on my nvidia card also and i cant get it to run at all
[PHP]

LD_PRELOAD="libpthread.so.0 libGL.so.1" __GL_THREADED_OPTIMIZATIONS=1 wine /home/brandon/.cxoffice/World of Warcraft/drive_c/Program Files/World of Warcraft --cx-app wow.exe -opengl[/PHP]


If someone can help me out i would appreciate it.

---

### Post by Dlambert on 2012-11-07
And here I was just excited about 304.64. Can't wait till this becomes stable. Will download asap.

But how is 134% possible?

---

### Post by Tweak42 on 2012-11-08
> **Bsohm said:**
> Alright I installed World of Warcraft through crossover and am trying to get this working on my nvidia card also and i cant get it to run at all
[PHP]

LD_PRELOAD="libpthread.so.0 libGL.so.1" __GL_THREADED_OPTIMIZATIONS=1 wine /home/brandon/.cxoffice/World of Warcraft/drive_c/Program Files/World of Warcraft --cx-app wow.exe -opengl[/PHP]


If someone can help me out i would appreciate it.

You need to change the line for wine to the cxoffice binary which is located in the /opt/cxoffice/bin directory (I just use regular wine in system so I don't need to include the path).  I think this will work, you should copy paste and run this in terminal to see what the error is.
NOTE: I'm not sure how the beta nvidia drivers with react with cxoffice since it's based on a older more mature version of wine.
```

LD_PRELOAD="libpthread.so.0 libGL.so.1" __GL_THREADED_OPTIMIZATIONS=1 /opt/cxoffice/bin/wine /home/brandon/.cxoffice/World of Warcraft/drive_c/Program Files/World of Warcraft --cx-app "C:/Program Files/World of Warcraft/Wow.exe" -opengl
```

---

### Post by Tweak42 on 2012-11-08
> **Dlambert said:**
> And here I was just excited about 304.64. Can't wait till this becomes stable. Will download asap.

But how is 134% possible?

I believe it has something to do with offloading graphics rendering thread to a seperate physical processors core so instead of the a process just maxing out on just one core, the load is shared and thus adds to the %.   

If you want to read all the messy details here's the wine bug where it's been discussed in detail.
[http://bugs.winehq.org/show_bug.cgi?id=11674](http://bugs.winehq.org/show_bug.cgi?id=11674)

---

### Post by Bsohm on 2012-11-09
Alright when i run that it gives me error:

Unable to find the 'default' bottle:
bottle 'default' not found in '/home/brandon/.cxoffice'
bottle 'default' not found in '/opt/cxoffice/support'

---

### Post by Tweak42 on 2012-11-13
> **Bsohm said:**
> Alright when i run that it gives me error:

Unable to find the 'default' bottle:
bottle 'default' not found in '/home/brandon/.cxoffice'
bottle 'default' not found in '/opt/cxoffice/support'

Sounds like there's a command line switch missing there that designates the which cx bottle to launch in, or you don't have any default bottle designated.  You may want to contact Codeweavers support for more specifics.

---

### Post by fogNL on 2013-06-03
> **Bsohm said:**
> Alright when i run that it gives me error:

Unable to find the 'default' bottle:
bottle 'default' not found in '/home/brandon/.cxoffice'
bottle 'default' not found in '/opt/cxoffice/support'

This works for me:

~/bin/gw2.sh
```

#!/bin/bash
LD_PRELOAD="libpthread.so.0 libGL.so.1" __GL_THREADED_OPTIMIZATIONS=1 "/opt/cxoffice/bin/wine" --bottle "Guild Wars 2" --check --wait-children --start "C:/users/Public/Desktop/Guild Wars 2.lnk" "$@"
```

Then chmod +x the script, and away you go.

(Note, if your GW2 bottle is named anything else, change the --bottle part.)

---

