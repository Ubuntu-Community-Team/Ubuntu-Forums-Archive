---
title: "Problem with Breezy kernel on 'Old World' Power Mac"
date: 2006-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by stocksy on 2006-03-29
Hi,

I'm trying to get Ubuntu breezy running on my Power Mac 9500/180MP, but I have had only limited success.

First of all, I tried installing from the Breezy CD.  The first half of the installation went fine:  I booted from the CD using BootX, partitioned the hard disk and installed the base system as usual.  Before I rebooted, I mounted the HFS+ partition and copied the kernel and initrd from the boot directory over to the Mac OS folder ready for rebooting.

When I tried to boot from the linux partition (supplying bootx with the location of the new kernel and ramdisk), Ubuntu would not boot.  It says:

---begin screen output---
<snip>
Begin: Initializing /dev ...
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system ...
Begin: Running /scripts/local-top ...
Done.
ALERT! /dev/sda8 does not exist. Dropping to a shell!


BusyBox <blahblah>

/bin/sh: can't access tty; job control turned off
# 
---end screen output---

and with that, it dumps me in a busybox shell.  I am 100% confident that /dev/sda8 is my root partition - I checked *several* times :) 

I was able to install successfully from the Hoary CD and this worked fine.  I have been able to dist-upgrade to breezy, but I still can't boot using the Breezy kernel (2.6.12-10-powerpc or 2.6.12-10-powerpc-smp).

For a sanity check, here are the bootx settings I'm using:

kernel: System Folder:Linux Kernels:vmlinux
ramdisk: System Folder:Linux Kernels:ramdisk.initrd.img
ramdisk size: 8192
options: root=/dev/sda8

I have tried various combinations of 'Force SCSI' etc, all to no avail.

At the moment, it is running the breezy distro with the hoary kernel.  It works, but I'd like to have a breezy kernel - bonus points for smp so I can get the other processor working!

James.

---

### Post by jdp on 2006-03-29
There are two SCSI busses on the 9500, internal Fast SCSI andd the int/ext slow SCSI.  Are you sure it's not sdb8?  I know you posted you checked it several times, but just another double check to point out...

I've had my 8500 booted up from 5.10, IIRC.

---

### Post by stocksy on 2006-03-30
[QUOTE=jdp]There are two SCSI busses on the 9500, internal Fast SCSI andd the int/ext slow SCSI.  Are you sure it's not sdb8?[/QUOTE]

With the hoary kernel it is sda8, but I will try the breezy kernel with sdb8 when I get home.

---

### Post by stocksy on 2006-03-30
OK,

I tried /dev/sdb8, still no luck :(

For what it's worth, I have an 8500 too.  I took the drive out of the 9500 and tried booting it in the 8500, but I got the same problem with that as well.  I even went as far as to try building my own kernel ([https://wiki.ubuntu.com/KernelBuildPPCHowTo)](https://wiki.ubuntu.com/KernelBuildPPCHowTo)), which did compile, but did not boot :P

Perhaps nobody is interested in running Ubuntu on such old computers - it's a pity if so.

---

### Post by ottojschlosser on 2006-03-30
[QUOTE=stocksy]
Perhaps nobody is interested in running Ubuntu on such old computers - it's a pity if so.[/QUOTE]

I tried to install Breezy on a 7300, but it hung early in the install. I haven't pursued it, since I have Breezy running on this fine old B & W G3. :)

---

