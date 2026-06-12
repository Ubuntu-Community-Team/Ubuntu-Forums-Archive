---
title: "CD/DVD Rom closes constantly, WINE won't open it"
date: 2012-05-17
forum: Wine
---

### Post by AbeFM on 2012-05-17
It appears after a reboot, the behavior has gone away, I'll consider the mater closed unless I need to reboot constantly to fix it. It's happened several times but perhaps it's not an issue
----------------------------------

I've been running pretty much the same software in V10.04. After upgrading to 12.04, a program I was using in wine (DVDfab8QT) won't open the CD rom drive after it's done.

Additionally, when I manually open the door (with the regular button on the drive) it closes again randomly between 30 seconds and so soon that the door hasn't fully opened yet.

Does not appear to be a physical issue, are there any pointers? Most things are stock, except I've been running
sudo noflushd -n 8 /dev/md127p1
on my RAID, which isn't supposed to work but seems to work fine.

---

### Post by AbeFM on 2012-05-21
No this definitely keeps coming back - I was hoping it would behave, but anytime I run wine, I get this behavior.

Any suggestions? No hardware changes, but now I get it all the time.

---

### Post by maxar6 on 2012-05-21
I would try to re-install wine. If you really need to use that windows program then fine. But i am pretty sure there is just as much software for Linux that will do the same job for free.

---

### Post by AbeFM on 2012-05-21
It was a clean install of Wine, the whole install is clean, that's basically all I have on there aside from Handbrake. Is there a reason to prefer one wine version over another?

The software is DVDfab, which seems to be the go-to program for backing up your (oftentimes DRM'ed to death) personal DVD collection. If you know something that's better, I'd love to hear it. I've always been a fan of DVD-decryptor, but it doesn't see the optical drive at all.

Basically, each generation of Linux I try, I get less contact with the hardware.

---

### Post by jmore9 on 2012-05-21
Try k9copy it is in the repos.  Also whenever i tried to use windows software on linux the ones that had hardware I/O were always giving me problems.  Also if you broese thruogh the multi media and video sections of snyaptic you will find all sorts of interesting software.

---

### Post by AbeFM on 2012-05-21
I'll check it out. By and large, I've tried everything in the standard repos, over the past 6 years. I'd MUCH rather have a gui, if I can get it. Will let you know if it works. Either way, it's odd wine won't see the cdrom drive properly anymore.

--------------------
Neat looking program, missing a few simple bells and whistles, but nothing insurmountable (not letting you override the name of the folder it puts it in, etc).... But there is one MAJOR issue: It's not dealing with protection, so all I get out the other end is unusable garbage. Is the program one of those you have to set up to remove all the protections (I'll compress it myself, I just need to rip it to disc)?

---

### Post by AbeFM on 2012-05-25
Ok, just like this time a year ago and two years ago and a year before that... the best software for the specific task is in windows... And that software worked just fine under 11.04

So all I'm asking for here is a way to make 12.04 to work as well as the previous version.

Can anyone offer some specific advice on how to get wine to interact with the DVD drive properly?

---

### Post by AbeFM on 2012-06-05
Anyone have any suggestions on this? I'm tired of scratching DVD's because I can't get them out of the tray before it closes on the disc... And I don't think it does the tray motors any favors either.

---

### Post by lisati on 2012-06-05
*Thread moved to **Wine**.*

---

### Post by AbeFM on 2012-06-14
Now that thread is in correct spot (THANKS for moving it!) has anyone seen this? Happened on upgrade.

---

### Post by AbeFM on 2012-07-29
> **lisati said:**
> *Thread moved to **Wine**.*

I'm not convinced this is a WINE issue - it seems to happen most often, but it's happened before I've run WINE once since a reboot.

---

