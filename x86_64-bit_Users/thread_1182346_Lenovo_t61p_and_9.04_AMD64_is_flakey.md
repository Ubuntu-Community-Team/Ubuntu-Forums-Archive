---
title: "Lenovo t61p and 9.04 AMD64 is flakey"
date: 2009-06-08
forum: x86 64-bit Users
---

### Post by computerfixitguy on 2009-06-08
I have tried 3 new hard disks now and I keep getting random lockups.  I get dpkg error using update manager.  Its just consistant general wierdness.

This system is a Centrino Pro with 2.4Ghz processor.  I can put my old 200GB drive in with 8.10 and its fine.  I tried upgrading to a 320 and all this started.  I have tried 3 different makers of drives (like it should ever make a difference) with no avail.

[  134.703753] jockey-backend[3690]: segfault at 7f21685d381c ip 00007f14e7dee294 sp 00007f14e4df2950 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[7f14e7db4000+bc000]

That happened when I tried to activate the nVidia driver.  Its just wierd.  Anyone else having problems with 9.04 AMD64?

Derek

---

### Post by John Jason Jordan on 2009-06-08
1. What happens when you try a different distro, e.g., Fedora or OpenSuse? I am thinking that it would either convict or acquit Ubuntu of the problems.

2. I have a T61 (not a p) with nVidia graphics and I have had no problem since I started with Hardy (currently Jaunty), all x86_64. However, I'm just using the 160 GB drive that came with it.

3. There is a Linux Thinkpad e-list which might be a good place to ask questions like this. You can sign up here:

[http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad]("http://mailman.linux-thinkpad.org/mailman/listinfo/linux-thinkpad")

Sorry I don't have any specific answers for your problem.

---

### Post by computerfixitguy on 2009-06-10
After trying two different 320's and now the origional 100G in my t61p its still flakey.  I have reinstalled 9.04 AMD64 five or six time and I get wierd stuff.  Like windows close kn gnome for no reason. 

Launching pidgin (fresh install) for the first time get this on my current install:  

Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 458: e....

I get random fsck errors.  Its never consistant.  More like a vulture overhead.  8.10 works flawlessly.

All I have running is 9.04 AMD64, I did a update.  At this momement Synaptic doesn't even run.  It just opens and closes.  Thats new.

My t61p has the Quadro 570, but I am not using the drivers. I tried a new ISO to install from and no difference.  It continues to be bizzare.

After a few years with Ubuntu, this is very not like them.  Something slipped through the cracks on the 9.04 release.

Derek

---

### Post by hhyang6333 on 2009-08-18
I encountered the same problem with my thinkpad t61p. I tried more than 10 times of installation and gave up.
I switched to Kbuntu 9.04 and it works for 1 week until now.

Hope someone can figure out what the problem is.

---

### Post by stilus on 2009-08-19
I have two users, one with a HP compaq, no real problems with AMD64 install. The other with a X61s, exactly the same make, model and config as I have. ubuntu 9.04 AMD64 has been a drama: segfaults, hard (kernel)locks, apt-get getting into a stress (newline errors). Including the blinking caps-lock and wirless lights. Completely erratic. I'm running debian lenny 5.02 without as much as a single hitch (although admittedly with a lot more configuration after the install). Too disappointed to start filing bugreports (been watching this [annoying bug]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/42121") for about a year and a half now).

Currently, debian 5.0(2) is running stable as a rock on both X61s systems, AMD64 install. Sorry to say ubuntu 9.04 has, on this system with AMD64 architecture and code, failed. I wish I could be more specific as to what caused the instability.

---

### Post by r m h on 2009-08-30
Hmmm, My ThinkPad T61p with 9.04 64-bit is rock solid.

I wonder if it's a difference with the variations of the T61ps?

I run a T61p (6459-CTO, T7700 2.4GHz, 4GB RAM, 256MB NVidia FX570M @ 1920x1200) that had been running 8.10, and now 9.04 with no stability issues.

$ uname -a
Linux icefog 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

---

### Post by GUmeR on 2009-09-03
Same here:
T61p (6460-6XG, T7500 2.2GHz, 8GB RAM, NVidia FX570M @ 1920x1200).

Random I/O error while installing or when updating (tried three HD's).

I'm trying with different file systems now, will let you know.

---

### Post by sivant on 2009-09-19
t61p  6459 cto

the only ubuntu that has proven completely stable was 8.04, 8.10 was ok, with networking issues, 9.04  crashes, locks/hangs (at least 3 different types, some obvious higher level program hangs/x org problems, and seg faults, it seems there is some kind of memory leak, databasing will cause massive slowdown and finally hang)  and poor networking (silent drops, where it thinks it is connected, and can not recoonect)

It seems that using a bluetooth mouse makes any of this hihghly more likely, andd turning off all radios makes it highly unlikely (most just the occasional random program drop then)

so for those t61p users with rock hard stability, mind trying bluetooth and telling me if you have the same performance?

going to try debian atmm, a month of 9.04 has really made me sad for ubuntu, but if there are fixes, I would love to use it again (my opinion is that ubuntu has the most reliable package manager out there, and that is important to me, but stability is #1)  alternately I may drop to 8.04.2, as it was the last one that performed well, but no hot swap, and  a lot of HAL stuff could get messy,

---

