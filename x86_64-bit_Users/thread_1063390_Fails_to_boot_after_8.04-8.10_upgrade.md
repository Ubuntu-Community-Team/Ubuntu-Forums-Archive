---
title: "Fails to boot after 8.04-8.10 upgrade"
date: 2009-02-07
forum: x86 64-bit Users
---

### Post by bluedalek on 2009-02-07
Hey All

Finally pitched Vista and installed Ubuntu 8.04.  Was a pain to get working in the first place due to SATA & nVidia drivers.

Here is my system specs:

XFX 8200 Mainboard
AMD x2 5000+
3.0 GB 667MHz Ram
XFX 8500 nVidia 512MB
500 GB Hitachi SATA2 HD

System was working fine until I upgraded to 8.10 from 8.04.  Now, when attempting to boot I get the following:
[B]
Loading, please wait...

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev

Alert! /dev/disc/by-uuid/c0672152-4d46-412d-9489-b863ccf1073b does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)[/B]

I have been using Linux off and on for the past couple years, but am totally stumped as to what's going on.

---

### Post by Yellow Pasque on 2009-02-07
When you boot your computer, press 'Esc' until you get to the GRUB menu. When you're at the GRUB menu edit the kernel boot line to read:
```
root=/dev/sda1
```

---

### Post by bluedalek on 2009-04-25
Hi

I know this was a while in responding, but that did not fix the issue.

I tried specifying sda, sdb, sdc & sdd

I also tried pointing it to /dev/disk/by-path/pci-000:00:06.0-scsi-0:0:0:0

I get the same error message, regardless of what I have it pointed to.

Here is my GRUB boot info:

[B]Ubuntu 8.10, kernel 2.6.27-14-generic
Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
Ubuntu 8.10,kernel 2.6.24.23-generic
Ubuntu 8.10,kernel 2.6.24.23-generic (recovery mode)
Ubuntu 8.10, memtest86+[/B]

When editing the first entry, I have this:

[B]root (hd0,0)
kernel /boot/vmlinuz-2.6.27-14-generic root=UUID=uuid/c0672152-4d46-412d-9489-b863ccf1073b ro quiet splash
initrd /boot/initrd.img-2.6.27-14-generic
quiet[/B]

Any help would be more than welcome!

Derek

---

### Post by old_geekster on 2009-04-25
Bluedalek, why don't you just try Jaunty Jackalope, 9.04?  I just installed it on a computer similar to yours and it was the easiest install I have ever made.  I have been using Ubuntu for several years.  So, I have done many installs of different distros.  It even recoqnized my XFX ATI 4870 XXX and setup the Catalyst software/drivers.  ATI drivers have always been a challenge for Ubuntu.  Not this time, however.

---

### Post by bluedalek on 2009-04-25
Actually got it fixed...  

edited the Grub entry from:

**kernel /boot/vmlinuz-2.6.27-14-generic root=UUID=uuid/c0672152-4d46-412d-9489-b863ccf1073b ro quiet splash**

to:

**kernel /boot/vmlinuz-2.6.27-14-generic root=UUID=uuid/c0672152-4d46-412d-9489-b863ccf1073b *pci=nomsi xforce=vesa* splash**

from what I found is that it's an issue with the SATA on the motherboard I am using.

Any thoughts?

---

