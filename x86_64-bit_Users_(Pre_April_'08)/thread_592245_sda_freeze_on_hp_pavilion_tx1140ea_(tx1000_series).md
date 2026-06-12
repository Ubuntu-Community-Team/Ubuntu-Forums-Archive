---
title: "sda freeze on hp pavilion tx1140ea (tx1000 series)"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by nolith on 2007-10-26
Hi,
last week I bought an HP pavilion tx1140ea.
I've installed Gutsy(64bit), gentoo(64bit) and Win Vista(32bit)

I noticed that using linux causes sda controller (or device) to Freeze in gutsy and to timeout in gentoo.
I'm traying to obtain the same problem on vista, but I can't.

This freeze affect the system some times, but yesterday, for istance, has freezed 5 times!

Now I'll try to install Gutsy 32bit, cose I'm not sure if it was a hardware problem or a software one.

Has someone experience with this laptops?


tnx

---

### Post by VincenzoAMD64 on 2007-10-26
Hello,
I have a HP TX1000,
Feisty works very well,
Gutsy -> sound problem, usb disk problem

I have two kernels:
2.6.20-16 sound Ok, usb disk problem
2.6.22-14 sound KO, usb disk problem

So, using the same binaries and configuration, but changing the kernel at boot time the sound problem is not present. This means that is related to kernel and alsa module.

With both kernels, when I connected my usb disk no disk was found and mounted. Looking for a solution a discover that:
booting using the irqpoll option and adding to fstab:
/dev/sdb1 /mnt/usbdiskb auto rw,user,umask=000 0 0
/dev/sdc1 /mnt/usbdiskc auto rw,user,umask=000 0 0
the disk are mounted.

Anyone have same problems?
Thank you Vincenzo

---

### Post by VincenzoAMD64 on 2007-10-26
Sorry,

the solution is already at
Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories > Hardware & Laptops > Helpfull Hints for a tx1000 (tx1120) 

Thank you
Vincenzo

---

