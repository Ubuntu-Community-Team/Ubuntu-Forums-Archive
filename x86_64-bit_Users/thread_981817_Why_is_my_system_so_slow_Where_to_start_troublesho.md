---
title: "Why is my system so slow? Where to start troubleshooting?"
date: 2008-11-14
forum: x86 64-bit Users
---

### Post by Mander on 2008-11-14
I've had Hardy installed (dual-boot) on an Acer Aspire 7520 for a while now (since April, I think), and it seems to be getting progressively slower.  The system has 1GB RAM, AMD64 Athlon processor, and Nvidia GeForce 7000m.  

I originally installed Ubuntu using Wubi, then moved it to its own partition. It was very much faster than Vista at first, but lately it seems to be freezing, crashing, and generally locking up as much as if not more than Vista on the same machine!  

Even if I use XFCE it often takes several seconds for windows to respond if I click on them or for simple programs like calculator to open.  Firefox (version 3) is often completely locked up, OpenOffice is dead slow (click and wait, sometimes for several minutes), and it often crashes or freezes up completely.  With Gnome or KDE the problem is even worse, but especially with Gnome.  

I'm sure that in my newbie-ness I have messed up some setting or other but I'm not experienced enough to know where to start with troubleshooting it.  

Thanks in advance for any pointers!

---

### Post by briandu on 2008-11-14
What version of Ubuntu are you using?

Start with:

open term and enter:   sudo apt-get update            then sudo apt-get autoremove       just as a bit of house keeping

also enter sudo df          and post that

---

### Post by Mander on 2008-11-14
sudo df gives:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             10399748   9283616    592016  95% /
varrun                  384932       292    384640   1% /var/run
varlock                 384932         0    384932   0% /var/lock
udev                    384932        80    384852   1% /dev
devshm                  384932         0    384932   0% /dev/shm
/dev/sda3             22288376  11581028  10707348  52% /media/DATA
/dev/sda2             34093052  23408124  10684928  69% /media/drv0

It's Hardy (8.04) with all the standard updates.  I installed the Nvidia driver using Envy.

---

### Post by spoc on 2008-11-14
I got a slow system because of tracker.
Try to remove it: ```
sudo apt-get remove tracker
```
This software often made my disk busy.

---

### Post by Kevbert on 2008-11-14
You could try looking at what programs are running in terminal with
```
top
```
Also try cleaning out with
```
sudo apt-get clean
sudo apt-get autoclean
```
and check for incomplete or damaged packages with
```
sudo dpkg --configure -a
sudo apt-get install -f
```
What's the size of your swap file when compared to RAM ? Maybe that needs to be enlarged.

---

### Post by Mander on 2009-01-11
Sorry I never did come back to this.

My swap file is 1GB, the same size as my memory.

I've tried all the commands you suggested, but I haven't noticed a major improvement.  Switching to KDE seems to have helped somewhat, but I have mostly just become used to it being slow!  I am thinking of reinstalling soon, perhaps that will fix it!

---

