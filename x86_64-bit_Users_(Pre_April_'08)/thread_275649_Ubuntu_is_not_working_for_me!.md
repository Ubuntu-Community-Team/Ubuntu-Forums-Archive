---
title: "Ubuntu is not working for me!"
date: 2006-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jadix on 2006-10-11
I have an AMD 64 3200+ processor, and an ATI Radeon x850 video card.

I have a brand new blank 160 GB SATA hard drive.

When I boot from the amd-64 cd that Ubuntu mailed me, it goes to a menu where I choose to install. this option causes it to list a bunch of processes it does before going to a blank screen. The screen remains blank until i restart.

So then I tried downloading the alternate 64bit edition of Ubuntu, burning to a cd, and trying again. this got me much further along, but still failed. The installation completed, but when I restarted and tried to boot into Ubuntu off the hard drive i get a blank screen. if i choose text only mode it works, but i have nothing in my root directory.
](*,) 
help!

---

### Post by Ptero-4 on 2006-10-11
By nothing in the root directory what you mean?
Also have you tried this:
```
ls ~
```
or this:
```
ls /
```
Hope you find a solution for your issue.

---

### Post by Jadix on 2006-10-11
Correction: everything is in root. im just retarded.  but i'm still having problems.

I can only boot into recovery mode.  If i try to boot normally i get a black screen right after the ubuntu splash screen.  is there something i can do in recovery mode to fix this?

---

### Post by kuja on 2006-10-11
Maybe it's a graphics card related issue? In that case, you should probably install the proprietary ATI drivers, and configure X to use them. I think the user Kilz has some info on it in his signature, click around, it shouldn't be hard to find one of Kilz's posts.

---

### Post by Jadix on 2006-10-11
Solved this by booting into recovery mode and typing:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(username)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
reboot

---

