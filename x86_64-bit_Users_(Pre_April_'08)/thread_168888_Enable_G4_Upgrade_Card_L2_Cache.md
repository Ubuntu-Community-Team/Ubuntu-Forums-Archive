---
title: "Enable G4 Upgrade Card L2 Cache"
date: 2006-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Yimmy on 2006-05-01
Does anybody know how to enable the l2 cache on a G3/G4 upgrade card in Ubuntu?  BootX only has options for G3, so I don't have that option available since mine is a G4.

---

### Post by davygravy on 2006-05-01
I did this years back on a NewerTech ZIFCarrier, a DayStar G4 ZIF and YDL on a 7600.  I can't remember exactly how I did it, but I remember peeking at the setting via  something like /proc/cpu  or somewhere like that ...

How ever I did it ... apparently there may be yet another way still.  You already have OS 9, right?  (you use BootX, so you probably do).  Use any of the old CPU/Cache profilers from PowerLogix, XLR8, NewerTEch, etc to peak at your L2 cache setting.  You may be able to write down your cache setting (it is a hexadecimal string) and pass it via the boot arguement... see this link...
[Activating an L2 Cache on G4 Crescendo]("http://lists.debian.org/debian-powerpc/2002/12/msg00440.html") .  The author made a typo in his first part of the thread, and he *did* mean to say L2 instead of L3 - he corrects himself.

[COLOR="Red"][COLOR="red"]**[SIZE="4"]Caution[/SIZE]**[/COLOR][/COLOR] - see this [link]("http://www.cpu.lu/~mlan/linux/dev/g3upgrade.html#l2cr") for some warnings, in the section _Enabling the Level 2 Cache under Linux_...  I never had any problems, but from the looks of it, one has to be careful w/ the cache and your machine...



Good luck.

---

### Post by Yimmy on 2006-05-01
I found a similar link to what you posted here saying the same thing ... to use an argument in BootX.  I'll try it and report back with what I find.  Thanks for the post!

---

### Post by Yimmy on 2006-05-02
Thanks for the info davygravy.  My L2 cache is running and Ubuntu is super fast now.  I freaked out the first time I rebooted because the machine froze while booting up, but it must have been a fluke because it started right in the next time. Now it's printer and network setup time.  Gotta try to find or build a printer driver for my lexmark z730.  I'm a little worried that's going to be difficult. :confused:

---

### Post by cyrillekazis on 2007-10-31
hello

 I am trying to enable the l2 cache on a bw mac with G4 proc upgrade card;

 I have the cache hex code.

where is the kernel command line? is it at the prompt at yaboot? (boot_)

if yes what do I have to enter exactly? in this liine?

thak you

cyrille

---

