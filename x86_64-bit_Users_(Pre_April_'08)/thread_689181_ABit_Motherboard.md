---
title: "ABit Motherboard"
date: 2008-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by xander_xu on 2008-02-06
Hi guys, I have recently installed Ubuntu on my system. The system cannot recognise several onboard devices. Could anyone help me to find the dirve for them please...

ABIT I-N73HD 

Intel Core2  Duo E6750
64-bits

Drivers needed

Chipset - NVIDIA GeForce7100/nForce 630i single chip 
Sound - On board 7.1 CH HD Audio (Realtek)
Graphic - nView™ - NVIDIA® nView™ multi-display


Thank you

---

### Post by Jouke74 on 2008-02-06
Did you try to install the "restricted drivers" :lolflag: ??

---

### Post by John.Michael.Kane on 2008-02-06
> **xander_xu said:**
> Hi guys, I have recently installed Ubuntu on my system. The system cannot recognise several onboard devices. Could anyone help me to find the dirve for them please...

ABIT I-N73HD 

Intel Core2  Duo E6750
64-bits

Drivers needed

Chipset - NVIDIA GeForce7100/nForce 630i single chip 
Sound - On board 7.1 CH HD Audio (Realtek)
Graphic - nView™ - NVIDIA® nView™ multi-display


Thank you
Under normal circumstances you should not have to install any sound or chip set drivers. Please post the output of the below command, 
```
lshw -short
```

As for running a multi-display configuration you can look in to setting up twin view.
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by claudiobello on 2008-03-13
hi guys,

I have a similar problem,
I installed windows XP on a new pc with the Abit Motherboard, 320 gb HDD, 2Gb ram, ATI Radeon 2400 with 512MB ram. 
When I try to install Ubuntu (6.04 or 7 version) I receive a Kernel panic message and I don't know what can I do.
I'm not expert with Ubuntu. 
Please help me
Thank you so much!

Claudio

---

### Post by daninca on 2008-03-15
I am having similar problems tryng to install 8.04 Alpha 4.  I have a Abit AN-M2HD with a AMD processor and a NVIDIA based motherboard.  The video is from a GeForce 7300LE, not the built-in 7100.

It claims it can't find the network interface (nvidia).  There are a couple message on F4 about a hot pluggable network interface being detected, but I didn't seen anything that looked related in lsmod.

If I continue, it manages to partition the SATA disk (750GB), but then times out trying to mount  the root partition.  I tried both with and without LVM.

I'm using the Alt installer (text based).  Both i386 and AMD64 installs act the same way.  I have installed Mythdora on this system before.

-Dan

---

