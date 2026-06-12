---
title: "My Kernel seems to have been deleted"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by kiwited on 2008-05-02
During my efforts to get USB working on Hardy, I received advice to purge udev, which I did through synaptic using complete removal instruction. After rebooting I got an "error 15" message. I rebooted using a 7.04 live cd and, after digging around a bit, found that all files in the "Boot" folder were gone. If I am right, this is where the kernel lives. It has taken days to succeed in downloading a live cd 8.04, but I now have one.

My question is - How do I go about restoring the kernel? Can I do this without a complete re-installation?

Thanks in advance,

Theo

---

### Post by Yellow Pasque on 2008-05-02
Are you sure your /boot folder wasn't stored in a separate partition? Can you run this from the Live CD?:
```
fdisk -l
```

---

### Post by kiwited on 2008-05-02
My hard drive has the following partitions:
sda1 is my former Xandros install
sda2 is swap
sda3 is a fat32 partition for transferring windows data for virtualbox
sda4 is the ubuntu install

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73f204fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12749   102406311   83  Linux
/dev/sda2           12750       14024    10241437+  82  Linux swap / Solaris
/dev/sda3           14025       15299    10241437+   c  W95 FAT32 (LBA)
/dev/sda4   *       15300       38910   189655357+  83  Linux
ubuntu@ubuntu:~$ 


Theo

---

