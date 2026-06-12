---
title: "Grub installation"
date: 2006-08-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by amione on 2006-08-03
I have an Athlon64 system with three harddrives. The main drive I boot off of is SATA and has Windows XP 64 Pro installed. I just installed Kubuntu on my third drive which is a slave IDE drive, however when I power on my system it automatically boots into windows. So, I hit F11 which brings me to the boot menu and selected the drive I installed Kubuntu on. It starts to try and boot and then tells me that no operating system was found. I know this is false because I booted into Knoppix and confirmed that the linux directory structure is indeed present on my drive. I checked the boot folder and the grub files and for some reason they did not  get configured properly or something. Every other time I have installed Linux the bootloader has configured itself automatically so I didn't need to mess with it (LILO and Grub). Should the Grub file be on my SATA drive or something? Please help, I'm basically a noob. Thanks for your help in advance.

---

### Post by mlind on 2006-08-03
Kubuntu installer probably prompted you for drive where to install grub?

If GRUB is installed on one of the hdd's, but not the one that's currently first on boot order, it's easiest to just change the boot order from BIOS, so that the drive that has GRUB is first.
If you find out that GRUB is not installed in any of these drives MBR, you must boot in Kubuntu using livecd or other recovery method and execute
```

grub-install /dev/xxx

```

Where /dev/xxx is the drive (not a partition) that's first on boot order.

---

### Post by VirtuAlex on 2006-08-04
I think we should file a bug-report.
See [http://ubuntuforums.org/showthread.php?t=227133]("http://ubuntuforums.org/showthread.php?t=227133")

---

