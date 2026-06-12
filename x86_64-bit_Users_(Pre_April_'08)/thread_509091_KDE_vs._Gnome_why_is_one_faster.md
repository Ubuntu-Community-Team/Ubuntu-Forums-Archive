---
title: "KDE vs. Gnome why is one faster??"
date: 2007-07-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by sparks0548 on 2007-07-25
I've been running Ubuntu 64-bit 7.04 on my HP DV210.  AMD-64 proc, Nvidia 6150 graphics card, 120GB HDD.  1GB RAM.  The video adapter runs 128MB on the card, but then will share memory with the system RAM.  What I can't figure out, is when I try to install the Kubuntu packages 7.04 64-bit, the desktop is dog slow.  I install the same video drivers, and everything.  Configured exactly the same.  Some of my mouse clicks when I went to run adept, would just fail.  Application wouldn't even load.  When I go back to Ubuntu 7.04 64-bit, everything runs great.  Even Compiz Fusion.  Besides I can't get the 3D cube to work, but no big deal I'm gonna stick another 1GB stick of RAM.

So enough of mindless babbling, has anyone else experienced this?  I've read all of the KDE Myths on the web, but some odd ball reason.....my laptop is in love with GNOME and only responds fiercely on that desktop.

Weird

---

### Post by kuja on 2007-07-25
> **sparks0548 said:**
> Some of my mouse clicks when I went to run adept, would just fail.  Application wouldn't even load.  This one in particular is caused by some sort of problem with kdesu. As for the rest, try tuning down some of the effects (an easy way to do so is provided by kpersonalizer). You can have as many preloaded konquerors as you want (very handy, for me anyway). Some of the windecs seem to slow things down, especially crystal (and especially if you have some of its nicer options turned on) There are a variety of other things you can look at too. :KS

---

### Post by dabl on 2007-07-25
Did you install the metapackage *kubuntu-desktop*, or just selected KDE apps?  The whole X server is different in Kubuntu - you really need to boot into the KDE environment to have the KDE apps perform as designed. :)

---

### Post by shafin on 2007-07-25
> Besides I can't get the 3D cube to work,

Try changing the backend to flat file configuration backend at backend and profiles in compizconfig settings manager

---

### Post by sparks0548 on 2007-07-27
I installed Kubuntu from the Live CD, not just the desktop.  The apps just ran pretty damn slow on the 64-bit platform.  Weird really weird.  I went back to Ubuntu and stuck with the GNOME desktop.  I did get the 3D cube to work after using the instructions on Compiz's website and the changes made to the NVIDIA-XCONFIG file.  I pulled those in and set the Horizontal, Vertical and number of desktops to the correct values.  It runs great on my laptop.  I think when I get home I'll try to install in Kubuntu on my clone tower and pickup a new video card for it.

Thanks alot for the information.  I'll stay with GNOME for now....thanks.

---

