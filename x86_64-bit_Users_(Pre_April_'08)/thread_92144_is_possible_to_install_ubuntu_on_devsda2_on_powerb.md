---
title: "is possible to install ubuntu on /dev/sda2 on powerbook"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by deen on 2005-11-18
my powerbook is lombard G333
openfirmware 3

is possible to install ubuntu on (USB Harddisk) /dev/sda2 (=> already created using mac-fdisk c )


even can't boot from usb harddisk (/dev/sda), maybe we can burn the kernel,yaboot,yaboot.com on CDROM and add option root=/dev/sda2 on yaboot.conf

is this possible ?


My Powerbook HardDisk IDE is broken.

---

### Post by er-ku on 2005-11-22
i'm not sure, but you may try that. But i doubt it'll be sda2, maybe sda3 (don't forgetthe bootstrap partition). You may want to just try the automatic partitioning of /dev/sda. Afterwards, you'll just probably have to play with openfirmware.

If you have a spare USB stick, just try it. Ubuntu install doesn't take too long (an hour or two, maybe), and you won't have to do much just so see if it boots "out of the box" after installing. And if you're patient enough, you may even find the ways to configure it to boot from the key anyways. ;)

---

### Post by er-ku on 2005-11-22
oh, and to boot from the flashdrive, you should read [this thread](http://ubuntuforums.org/showthread.php?t=89990) and check links in it.

---

