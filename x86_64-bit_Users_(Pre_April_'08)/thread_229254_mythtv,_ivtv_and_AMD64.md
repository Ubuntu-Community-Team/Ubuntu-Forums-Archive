---
title: "mythtv, ivtv and AMD64"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravalox on 2006-08-04
Okay, I'm trying to build a mythtv rig from an athlon64 system I have.  This is very difficult to do with Ubuntu it seems, I've done this previously with gentoo and never had so many hoops to jump through.  My big problem right now is that ivtv won't build a working kernel module for me; when I modprobe for ivtv I get: FATAL: Error inserting ivtv (/lib/modules/2.6.15-23-amd64-k8/ivtv/ivtv.ko): Unknown symbol in module, or unknown parameter (see dmesg)


I have tried ivtv version , 4.1, 4.4, and 4.6.  All have similar effect; I've followed these instructions: 

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)
 and then these:
[http://ubuntuforums.org/showthread.php?t=186747&highlight=installing+mythtv](http://ubuntuforums.org/showthread.php?t=186747&highlight=installing+mythtv)

What can I do with an uncooperative kernel module?

---

### Post by x64Jimbo on 2006-08-04
was your gentoo version 64 bit as well? I'd be inclined to try it with 32 bit first. PVRs don't need a lot of raw crunching power.

---

### Post by ravalox on 2006-08-04
I don't have much choice, the other motherboard died and it was the best available option.

---

### Post by x64Jimbo on 2006-08-06
You can install 32 bit operating systems on 64 bit processor systems. AMD64 is designed to be able to run all 32 bit programs, including the operating system.

---

### Post by LinuxConvertJune2006 on 2006-08-06
> **x64Jimbo said:**
> was your gentoo version 64 bit as well? I'd be inclined to try it with 32 bit first. PVRs don't need a lot of raw crunching power.

Assuming you have a capture card that decodes/encosdes video (like the 150/250/350's), otherwise if using a simple caspture card than your CPU is critical (it does all encoding/decoding), and 64bit helps alot.

---

### Post by RAOF on 2006-08-06
> **ravalox said:**
> Okay, I'm trying to build a mythtv rig from an athlon64 system I have.  This is very difficult to do with Ubuntu it seems, I've done this previously with gentoo and never had so many hoops to jump through.  My big problem right now is that ivtv won't build a working kernel module for me; when I modprobe for ivtv I get: FATAL: Error inserting ivtv (/lib/modules/2.6.15-23-amd64-k8/ivtv/ivtv.ko): Unknown symbol in module, or unknown parameter (see dmesg)


I have tried ivtv version , 4.1, 4.4, and 4.6.  All have similar effect; I've followed these instructions: 

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)
 and then these:
[http://ubuntuforums.org/showthread.php?t=186747&highlight=installing+mythtv](http://ubuntuforums.org/showthread.php?t=186747&highlight=installing+mythtv)

What can I do with an uncooperative kernel module?
Have you checked the dmesg log?  That would contain the specific problem, which would help us fix it :)

The problem **might** be a missing v4l2-core module, or something.  But the actual relevant dmesg log would be most useful :)

Oh, and x86-64 is **very** useful for a MythTV box.  Encoding/decoding is something that really benefits (about 30%).

---

### Post by x64Jimbo on 2006-08-07
> **LinuxConvertJune2006 said:**
> Assuming you have a capture card that decodes/encosdes video (like the 150/250/350's), otherwise if using a simple caspture card than your CPU is critical (it does all encoding/decoding), and 64bit helps alot.
**Touché**

---

### Post by rosbif on 2006-08-09
Ok, well the good news is that it can be done in 64-bit-land - I'm currently running ivtv-0.4.6 on an AMD64.
The bad news is that it takes a while to get it right.....
If you're going to stay at 2.6.15, then I'd recommend getting the current kernel version (-26 I think, I'm away from my machine at the mo').  The Hyams guide regarding ivtv is definitely the one to follow, with the following two important points:
1. the firmware needs to live in /usr/firmware in current Dapper configurations (took me ages to get this right)
2. examine VERY carefully, the output from the "make install" - you WILL find conflicts and you MUST hide the offending libs and re-run the make install (this took me ages to find, since the output shoots off the screen pretty quickly)

As a previous poster said, some dmesg output might help us diagnose your probs.
Good luck!

---

### Post by ravalox on 2006-08-13
The answer is to have the -26 kernal.  After upgrading the kernel everything went fine.

---

