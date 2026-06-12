---
title: "Two VERY annoying bugs"
date: 2009-09-17
forum: x86 64-bit Users
---

### Post by jarrhed on 2009-09-17
I'm running Ubuntu 9.04 with the latest updates as of 9/17/09 and I have two very very annoying bugs. The first one is that Ubuntu won't detect at all my 320gb External USB HDD. The second one is that when I hit CTRL+F1 or CTRL+F2 to go to the non-gui terminal, the screen is completely blank. My system specs are:
AMD Atholon 64 x2 6400+ 3.2ghz
4GB Ram
nVidia 9800gtx+ 512mb EVGA
2x37gb 10,000rpm SATA
1x320gb 7200rpm External USB

When I try to run sudo fdisk -l, it doesn't list my 320gb hardrive
Output:
```

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8768b3c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        4501    36046848    7  HPFS/NTFS

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b92c69b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4310    34620043+  83  Linux
/dev/sdb2            4311        4500     1526175    5  Extended
/dev/sdb5            4311        4500     1526143+  82  Linux swap / Solaris

```
Please note that I manually installed the nVidia graphics driver if that may be of help, off the nvidia website with the build-essential and kernel-package metapackages installed for the kernel I'm running on.

Any Help?

I'm not a linux newbie, I've worked with Arch, Gentoo, Slackware, Sidux(Debian Sid in a distro), and a few others and have not had this problem, but I want Ubuntu because I'm developing programs in Rails and want something simple to set up

---

### Post by amd-64 on 2009-09-17
just a couple of ideas

what is the output of lsusb

Do you have usb_storage module loaded.

---

