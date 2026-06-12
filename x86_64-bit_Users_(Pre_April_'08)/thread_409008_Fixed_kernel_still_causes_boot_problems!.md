---
title: "Fixed kernel still causes boot problems!"
date: 2007-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by nbound on 2007-04-14
Different error this time though for me:

```
[33.666273] sr 4:0:0:0: Attached scsi generic sg0 type 5
Done.
             Check root= bootarg cat /proc/cmdline
              or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/57cbd205-0bb7-4cf9-b58f-7dcb398c7efc does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: cant access tty; job control turned off
(initramfs)
```

HELP! :'(

---

### Post by xreef on 2007-04-14
I am seeing the exact same problem on Feisty Fawn, kernel version 2.6.20-14. (After the update of 11/4/2007 (but i'm not really sure of the date)).
With the same uuid I can boot with the old kernel (I upgrade from edgy) 2.6.17-10-generic (2.6.17-11-generic don't go).

My Grub
reef@portatireef:~$ cat /boot/grub/menu.lst
default 0

timeout 10

title Ubuntu, kernel 2.6.20-14-lowlatency
root (hd0,3)
kernel /boot/vmlinuz-2.6.20-14-lowlatency root=UUID=dd2fff11-bfc0-4235-8557-ad9679166a1f ro quiet splash
initrd /boot/initrd.img-2.6.20-14-lowlatency
quiet
savedefault

title Ubuntu, kernel 2.6.20-14-lowlatency (recovery mode)
root (hd0,3)
kernel /boot/vmlinuz-2.6.20-14-lowlatency root=UUID=dd2fff11-bfc0-4235-8557-ad9679166a1f ro single
initrd /boot/initrd.img-2.6.20-14-lowlatency

title Ubuntu, kernel 2.6.20-14-generic
root (hd0,3)
kernel /boot/vmlinuz-2.6.20-14-generic root=UUID=dd2fff11-bfc0-4235-8557-ad9679166a1f ro quiet splash
initrd /boot/initrd.img-2.6.20-14-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-14-generic (recovery mode)
root (hd0,3)
kernel /boot/vmlinuz-2.6.20-14-generic root=UUID=dd2fff11-bfc0-4235-8557-ad9679166a1f ro single
initrd /boot/initrd.img-2.6.20-14-generic

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,3)
kernel /boot/vmlinuz-2.6.17-10-generic root=UUID=dd2fff11-bfc0-4235-8557-ad9679166a1f ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,3)
kernel /boot/vmlinuz-2.6.17-10-generic root=UUID=dd2fff11-bfc0-4235-8557-ad9679166a1f ro single
initrd /boot/initrd.img-2.6.17-10-generic

title Ubuntu, memtest86+
root (hd0,3)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

My lspci
reef@portatireef:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 755 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
00:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

bye :confused:

---

### Post by nbound on 2007-04-14
try upgrading yours to the 15 version see if it helps?

---

### Post by xreef on 2007-04-14
Yes 2.6.20-15 is ok.. tanks...

---

### Post by nbound on 2007-04-14
so anyone with the error on 15?

---

### Post by gavintlgold on 2007-04-14
I don't seem to be able to boot with 15. I have had that error in the past, and it seems like the timing is the same, but I haven't checked if it really is the same error.... probably though.

I am only able to boot feisty through a build of the kernel that I made a while ago.... but the restricted drivers manager doesn't work with that.

Can you help me? I looked in the forums for fixes, but they were all old kernel versions.

I think I have all default settings on for grub.

---

### Post by nbound on 2007-04-14
ive filed a bug at LP, they asked me to try and disable some ata thing for the kernel, but it didnt work still got the same error though rather then stop at [33] i got up to [468].

if you would like to try it pass "libata.ignore_hpa=0" on the kernel command line. If you get it to go perfectly, maybe you should file an LP bug

---

### Post by gavintlgold on 2007-04-15
I got an update today, and all the problems were fixed. (no hacks, etc)

I didn't get dumped into the busybox though before, so maybe it's not the same problem.

---

### Post by nbound on 2007-04-15
Yeah i got that update as well, fixed everything, just had to remake my nvidia module...

---

