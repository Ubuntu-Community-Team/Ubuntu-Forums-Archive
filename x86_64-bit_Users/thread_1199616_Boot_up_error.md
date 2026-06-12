---
title: "Boot up error"
date: 2009-06-29
forum: x86 64-bit Users
---

### Post by 0pul3nce on 2009-06-29
Hello

I'm getting boot up errors, quite often and i'm not sure if it's because of the sata HD or the 64 os.

When booting up i have to press esc and then go to recovery to get anything working, when i leave the computer to just run i get the message below (maybe because it's booting from the wrong kernel...i've got like 5 options ...i want to use 9.04 2.6.28-13-generic)

"Boot from (hd0,0) ect3 da66bb11-fda3-4b2b-b33d-910f89aed644
Starting up ...
Loading please wait...
Gave up waiting for root device. Common problems
-Boot arg (cat/proc/cmdline)
   -Check rootdelay=(did system wait long enough?)
   -Check root=(did system wait for right device?)
-Missing modules (cat/proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/da66bb11-fda3-4b2b-b33d-910f89aed644 does not exist. Dropping shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2ubuntu7) built-in shell (ash)
Enter help for a list of built-in commands."

So from the above message i believe it's a Harddisk problem
I've been to the following website

[http://ubuntuforums.org/showthread.php?t=311158&highlight=gave+waiting+root+device](http://ubuntuforums.org/showthread.php?t=311158&highlight=gave+waiting+root+device)


Q. After GRUB boots my kernel, all I see is this:
Quote:
Begin: Waiting for root _file system.._.(slightly different to my problem)
A. This may because you installed Ubuntu on a SATA hard drive. To fix this error, you must recompile the kernel with SATA options enabled.

How do i do that?? If that is the answer for me...

Thanks in advance

---

### Post by bedtime_with_the_bear on 2009-06-29
I don't think it's a SATA issue, as I have installed and used Ubuntu on SATA since 8.10 with no additional steps necessary. I'm running kernel 2.6.28-13 right now and it does not require any additional steps.

With that in mind - it is entirely possible there is an issue with the disk itself, or your configuration.

Can you do the following please:


[LIST]
[*]Boot to a Jaunty livecd
[*]Open a command line
[*]Post the output of sudo fdisk -l
[*]Post the output of sudo blkid
[/LIST]
From this we'll be able to identify the physical disks Ubuntu can see, and then mount your root disk and take a look at the boot configuration.

---

### Post by webit on 2009-07-01
I got very similar issue (had no network in home because of heavy-rain so I have no fdisk and blkid outputs) but this is what I discover:
* normal boot (sending me to BusyBox) after long time I was signed as root. I did `fdisk -l` and that didn't show my root-partition's disc (ata); showed only second disc (sata)
* live cd boot - `fdisk -l` output shows both discs, and I can even mount them

Can anyone help? 
Should I boot into liveCD mount orginal root to / and try to install other kernel version (I have only one set up in grub)?

---

### Post by master_kernel on 2009-07-01
Which kernel are you trying to boot from?

---

### Post by bedtime_with_the_bear on 2009-07-01
What kernel version do you have on your normal install? (uname -a)

If you boot to the livecd, mount your root filesystem on, say, /mnt, you can then run blkid and fdisk as /mnt/sbin/blkid and /mnt/sbin/fdisk.

Once mounted, I'd also suggest attaching copies of boot/grub/menu.lst boot/grub/device.map, and etc/fstab.

---

### Post by webit on 2009-07-02
Fixed by adding one of latest kernels to grub. I don't know why I have no listed latest kernels while booting. The problem was with SATA controller I think. Disconnecting that disk (turned power cable off) allowed me to boot correctly (glad home and root partitions was on ata disk). Than I was able to install new kernel in grub (edited menu.lst).

Thnaks for your replies.

---

