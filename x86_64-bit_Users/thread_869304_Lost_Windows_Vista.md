---
title: "Lost Windows Vista?"
date: 2008-07-24
forum: x86 64-bit Users
---

### Post by marvlowe on 2008-07-24
I installed 64bit Ubuntu 8.04 on my HP Pavilion dv6000 laptop. I thought I was setting it up with dual boot but it appears I blew it and Windows is now gone. The grub boot director does not show it. Worse yet I had a separate partition with data which seems to have disappeared as well. Is there any way to recover or am I totally dead for Windows?

---

### Post by PinkFloyd102489 on 2008-07-24
Open the partition editor (System > Administration > Partition Editor) and check to see if there's still an NTFS partition. If so, Vista is still there, just not listed in GRUB. Easily added.

---

### Post by marvlowe on 2008-07-24
I went to system-administration but there was no partition editor listed in the menu.

Marv

---

### Post by Melk79 on 2008-07-24
Install Gparted from the Synaptic Package Manager under System->Adminstration or open a terminal and enter
```

sudo apt-get install gparted
```

---

### Post by Sef on 2008-07-24
Easy way to check if you still have Vista:

Applications > Accessories > Terminal 

then copy and paste (or type)

```
sudo fdisk -l
``` small L

Copy and paste the results here.

---

### Post by marvlowe on 2008-07-24
Here's the results from sudo fdisk -l. Am I out of luck with Vista?

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e86f523

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18729   150440661   83  Linux
/dev/sda2           18730       19457     5847660    5  Extended
/dev/sda5           18730       19457     5847628+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009f64a

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         461     3702951    b  W95 FAT32
/dev/mmcblk0p2             462         489      224910    5  Extended
/dev/mmcblk0p5             462         489      224878+  82  Linux swap / Solaris

---

### Post by Sef on 2008-07-25
> Here's the results from sudo fdisk -l. Am I out of luck with Vista?

You overwrote Vista.  I do not see an NTFS partition.

What to do is download [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and see if you can recover your Vista and data partitions.

---

