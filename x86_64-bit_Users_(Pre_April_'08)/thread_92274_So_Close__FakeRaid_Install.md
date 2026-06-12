---
title: "So Close :: FakeRaid Install"
date: 2005-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghostpsalm on 2005-11-19
Alright, I have been trying for four days straight to get Ubuntu installed on my computer.  It is an Athlon64, with a Via Fake RAID.  I am hoping to make this RAID0 my boot drive.  I have followed many howto's (listed below).  After many debootstraps, and many installs, I combined these howtos, I:

-Installed Ubuntu onto a PATA hard-drive.
-Copied it to my RAID via Ubuntu LiveCD, and (downloaded 'dmraid' utility.).  
-Re-Built Kernel, enabling statically support for RAID, as in KernelHowTo
-Configured the initramfs; as in FakeRaidHowTo

PROBLEM:  When I run GRUB to configure the MBR, etc, and hopefully get the whole thing to boot into the RAID filesystem - Grub cannot find the drives.  Outside of Grub dmraid outputs the following:

```
root@ubuntu:/# dmraid -ay -v
RAID set "via_cfdehjfb" already active
INFO: Activating stripe RAID set "via_cfdehjfb"
ERROR: opening "/dev/mapper/via_cfdehjfb"
```
and
```
root@ubuntu:/# dmraid -r
/dev/sda: via, "via_cfdehjfb", stripe, ok, 72303839 sectors, data@ 0
/dev/sdb: via, "via_cfdehjfb", stripe, ok, 72303839 sectors, data@ 0
```

Any hints as to why the RAID is working in theory, but not displaying in /dev/mapper/?  

Links:
[FakeRaidHowto]("https://wiki.ubuntu.com/FakeRaidHowto")
[KernelByHandHowto]("http://https://wiki.ubuntu.com/KernelByHandHowto")
[IstallViaGentoo]("http://www.ubuntuforums.org/showthread.php?t=86219")

---

### Post by psusi on 2005-11-19
What does dmsetup status show?

What about ls -al /dev/mapper?

It looks like dmraid is saying it found the drives, but something failed and it says it could not open the raid to probe for and create the partition devices on it.

---

### Post by ghostpsalm on 2005-11-19
```
root@ubuntu:/# dmsetup status
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
via_cfdehjfb4: 0 4305420 linear
via_cfdehjfb3: 0 123298875 linear
via_cfdehjfb2: 0 16787925 linear
via_cfdehjfb1: 0 208782 linear
casper-cow: 0 2097152 linear
via_cfdehjfb: 0 144607678 striped
casper-snapshot: 0 4192384 snapshot 85864/2097152
```

```
root@ubuntu:/# ls -al /dev/mapper
total 38
drwxr-xr-x   2 root root     72 2005-11-20 09:16 .
drwxr-xr-x  13 root root  39136 2005-11-20 09:16 ..
crw-------   1 root root 10, 63 2005-11-20 09:16 control
```


OKe, I ran 'uname -a', but found out a little later that it will display the kernel information of the LiveCD, not my chroot'ed environment.  So, dmsetup says I should try to install the device-mapper driver into the kernel though it isn't working.  I have /sys, and /proc mounted when I am in the chroot.

---

### Post by ghostpsalm on 2005-11-20
Oke, currently I have only seemingly one problem.

I have mounted /proc, and /sys before I enter into the chroot.  This then anables the dmsetup utility to function normally.  But now when I run dmraid, it says:

```
root@ubuntu:/# dmraid -ay -v
RAID set "via_cfdehjfb" already active
INFO: Activating stripe RAID set "via_cfdehjfb"
ERROR: opening "/dev/mapper/via_cfdehjfb"
```

Can anyone help?

---

### Post by psusi on 2005-11-21
Try asking dmraid to be more verbose, and if that doesn't work, try straceing it to see exactly what is failing.  By the way, why are you trying to run dmraid from inside a chroot?  And what have you chrooted into?  You should not use a chroot until after you get the drive recognized, format a partition to install to, mount it, debootstrap it, and THEN chroot into it to install the rest of the system.  

[QUOTE=ghostpsalm]Oke, currently I have only seemingly one problem.

I have mounted /proc, and /sys before I enter into the chroot.  This then anables the dmsetup utility to function normally.  But now when I run dmraid, it says:

```
root@ubuntu:/# dmraid -ay -v
RAID set "via_cfdehjfb" already active
INFO: Activating stripe RAID set "via_cfdehjfb"
ERROR: opening "/dev/mapper/via_cfdehjfb"
```

Can anyone help?[/QUOTE]

---

