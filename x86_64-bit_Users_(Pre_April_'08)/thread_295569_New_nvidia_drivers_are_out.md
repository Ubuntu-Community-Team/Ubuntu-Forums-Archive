---
title: "New nvidia drivers are out"
date: 2006-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by kleeman on 2006-11-08
See here:

[http://www.nvnews.net/vbulletin/showthread.php?t=79719](http://www.nvnews.net/vbulletin/showthread.php?t=79719)

These are not betas. I will give them a spin tonight.

---

### Post by kuja on 2006-11-08
I attempted to give them a spin last night, but I must have done something wrong. I removed my current + the restricted modules after killing X, install xorg-dev, and it seemed to set up okay, but when I went to restart X it told me it couldn't load the nvidia drivers... Bad luck must like me or something.

---

### Post by javajunky on 2006-11-08
Fwiw, I've just upgraded from 9625 (Beta) to 9629, and my glxgears fps has gone from 600ish on average to 1200ish on average [this is on top of beryl + emerald], now if I could only get my laptop to run without 'noapic' on the kernel boot on edgy, I'd be happy with my lovely 64bit OS.

---

### Post by kleeman on 2006-11-09
Tried them out and they look good on my 7950 GX2 rig. Under beryl and glxgears I get 7700fps while metacity is showing 14000fps. sauerbraten FPS works with x86_64 and is showing 170fps at fullscreen. beryl works fine and seems snappier than with the 9625 beta driver. No stability issues so far despite the 64bit OS and multiple gpus and cpus.

---

### Post by zaddik01 on 2006-11-19
Hi there,

I have followed NVidia instructions on installing the -9629 drivers and it locks up my machine. I have even waited overnight to see if it would come up, but I always have to power down!

My system is an ECS K8T890 mb with a dualcore amd 3800, GeForce FX5500 video card, and 2GB ram. The only Xorg stuff installed:

xserver-xorg
xserver-xorg-core
xserver-xorg-dev
xserver-xorg-input-evdev
xserver-xorg-input-kbd
xserver-xorg-input-mouse
xserver-xorg-video-fbdev
xserver-xorg-video-nv

I don't know what to do. Also, I have tried doing the nvidia-glx package with the same results?? I am including the relevant bits of the log to see if it helps anyone. 

Thanks!

---

### Post by kleeman on 2006-11-19
Is that xorg.conf you included the one that caused the lockup? You realize that to use the nvidia driver you need to use "nvidia" not "nv" in xorg.conf....

---

### Post by Azakus on 2006-11-19
I'll give it a spin after I make the obligatory backup of my system (Nvidia drivers seem to hate me when I install new ones). I'll also see if I can get Beryl to run without XGL, which causes some interesting problems for me, like no "." on the numpad.

---

### Post by zaddik01 on 2006-11-20
> **kleeman said:**
> Is that xorg.conf you included the one that caused the lockup? You realize that to use the nvidia driver you need to use "nvidia" not "nv" in xorg.conf....

No, that is the one that works :( substitute nvidia and that is the one that bombs, religiously.

---

### Post by kleeman on 2006-11-20
Head on over to the nvidia linux forum and lodge a bugreport:

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

There is a sticky there about how to proceed. You may also find threads with problems similar to yours.

---

