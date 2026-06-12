---
title: "Installing Ubuntu on second drive of a G5"
date: 2005-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by pindar on 2005-11-01
I'm not sure if this was just my individual problem. I installed Ubuntu 5.10 on the second internal drive of my G5. Installation was smooth, but the system wouldn't boot off the drive because the yaboot.conf file written by the installer was incorrect. I had to fix it manually. In case it might help anybody, here's my yaboot.conf:

```

boot=/dev/sdb2
device=sd1:
partition=8
ofboot=sd1:2
root=/dev/sdb8
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
enableofboot
macosx=/dev/sda3


image=/boot/vmlinux
      label=Linux
      root=/dev/sdb8
      initrd=/boot/initrd.img
      partition=8
      read-only

```

Of course, you'll have to adapt the partition numbers to your actual setup. To see your partitions, run
```

# sudo parted /dev/sdb print
Disk geometry for /dev/sdb: 0.000-239372.437 megabytes
Disk label type: mac
Minor    Start       End     Filesystem  Name                  Flags
1          0.000      0.031              Apple
3        128.031 102400.031  hfs+        Apple_HFS_Untitled_1
5     102528.031 133120.031  hfs+        Apple_HFS_Untitled_2
2     133120.031 133120.812  hfs         boot                  boot
7     133120.812 133632.812  linux-swap  swap                  swap
8     133632.812 239372.437  ext3        root                  root
Information: Don't forget to update /etc/fstab, if necessary.

```
After adjusting yaboot.conf, run
```

ybin -v -C /etc/yaboot.conf

```
and you should be ready to roll.

---

