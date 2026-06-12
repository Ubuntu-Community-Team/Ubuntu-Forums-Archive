---
title: "Corrupt SATA DVD reads"
date: 2007-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by joshua7311 on 2007-07-18
I have three servers with identical hardware.  They have Tyan Thunder K8WE S2895 motherboards with 64 bit Dual Core AMD Opterons, and Sony DVD RW AW-G170S SATA drives.

When I did the initial install of Xubuntu 7.04 I didn’t have the Sony DVD drive yet, so I used an old IDE cdrom that I slaved in just to do the install.

Now that I have the Sony DVD drives installed I cannot get them to work properly under Xubuntu.  I put in a DVD and it automounts just fine, but some the directories show up as files, and the real files are corrupted.

We have a Slax live DVD that boots and works great in the Sony DVD drive.

The Xubuntu live cd will not boot in the Sony DVD drive.  It quits with this error message:

/bin/sh: can’t access tty; job control turned off
(initramfs)

There is some error messages in dmesg related to the drive, they are pretty extensive and I am not sure what is pertinent so I attached the whole output.  I also attached the output of lspci –vvnn.

uname -a
Linux RDA-1 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux


Can anyone help?

Joshua

---

### Post by Selage on 2007-10-30
I see that they were not able to fix the issues with the Tyan s2985.

I'm have several problems due to the Nvidea chipsets 2050 and 2200.
My Sata Hard drives are mounted as Old IDE, what is really frustating and my Nvidea GTX 7800 is not reconized corrertly, some memory lack.


Message to the programmers, Can we ( Tyan s2985, with Nvidea Chipset 2200 and 2050, users) also benifet from the wonderfull Linux version "Ubuntu 7.10"

I cant program, and dont even know how to start an investigation.
I hope some can, and are willing to pass the knowledge.


Thanks Kiss

---

