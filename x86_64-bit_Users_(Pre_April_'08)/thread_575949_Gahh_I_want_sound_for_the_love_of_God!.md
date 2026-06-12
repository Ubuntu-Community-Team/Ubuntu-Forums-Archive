---
title: "Gahh I want sound for the love of God!"
date: 2007-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sgt_Jerky on 2007-10-14
Alright so I installed Feisty Fawn last weekend and have been struggling since to squeeze any sound out of my system.  I'm running on an AMD Athlon 64 X2, with an XFi SoundBlaster XtremeGamer card.  Now I'm absolutely SICK of trashing through the internet trying to find a way to force the XFi Beta driver to work on my system.  I've tried at least 20 different methods, all resulting in failure.  At this point I'd be perfectly happy with using my onboard soundcard, which I believe to be an intel ICH card using the Realtek drivers.  Again I have searched forever trying to find how to get even these drivers to work.  And yes, I have tried doing the stupid stuff like making sure nothing is muted, etc etc.  here is the output from aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: ICH [Intel ICH], device 0: Intel ICH [Intel ICH]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH [Intel ICH], device 2: Intel ICH - IEC958 [Intel ICH - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
*************************************

If a ubuntu guru could PLEASE assist the world's largest newb with this I would be forever in your debt.  I'm sick of windows and other than my sound issue I'm very excited about linux.

---

### Post by Kilz on 2007-10-14
[This thread may prove helpful.]("http://ubuntuforums.org/showthread.php?t=571656")

---

### Post by Sgt_Jerky on 2007-10-14
I've already tried that whole page up and down.  I can get to the point where I'm supposed to do the "make" and "make install" but I get a ton of errors (I don't know them off-hand I'd have to redo the process to get them).  I think I remember one of them being "libXxf86dga.so.1 is not a symbolic link".  If that makes any sense to anyone. :(

---

### Post by Kilz on 2007-10-14
I would suggest posting your errors in the topic dealing with it as the writer may be able to help you. But without exact errors it may be hard. You can copy and paste right off the terminal, that may be easier than typing it out.

---

### Post by Sgt_Jerky on 2007-10-14
Alright well here's the deal.  I can get up to the part where I do the "make" command (yes I have tried doing it both as just "make" and as "sudo make" with the same failure each time).  here is my Makefile.conf  just in case I botched up that entry.

**Makefile.conf**************
CFLAGS			= -Wall -fomit-frame-pointer -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -fno-stack-protector\
**************************

After doing the sudo make install I get this:

install /home/kevin/XFiDrv_Linux_US-1.04/ctsound to /etc/init.d...
FATAL: Error inserting ctalsa (/lib/modules/2.6.20-16-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Does any of that help?

---

### Post by ekricyote on 2007-10-29
I would suggest trying 'sudo make clean' before trying to redo any calls to make.

If this was an upgrade install from feisty, you might be stuck as I was; eventually I decided it was less trouble and moved my home folder out to another partition and started with a fresh install of Ubuntu. It solved a lot of my other issues and even seemed to improve graphical performance (I had been using Beryl, if only for the Emerald themes...makes me wish some of them were ported to whatever compiz uses.)

Also, be sure that start working with your driver in your home directory. If the installer is as bad as they say it is, it might even assume you're installing it from a folder in your home directory.

Seriously, the thread mentioned in previous posts is your best hope at this point. Best of wishes.

---

