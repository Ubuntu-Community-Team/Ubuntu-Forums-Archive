---
title: "ubuntu V. SuSE yast  / Mac Mini"
date: 2006-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by rayc on 2006-03-30
Hi all,

previous linux experience: install of SuSE 8 on a Dell Laptop dual booting with XP. Install was really simple for a novice.

recently transitioned over to the MacMini and got myself a Ubuntu 5.10 for PowerPC. Was expecting a SuSE Yast type install experience.

Went for custom install as I *obviously* did not want to reformat my entire harddisk

Custom partitioning is not very clear. I do not want to use iPartiton and I do not (yet) want to follow the support outlined here [http://www.ubuntuforums.org/showthread.php?t=89960](http://www.ubuntuforums.org/showthread.php?t=89960) because I believe the partitioning should be facilitiated through the install process. Compare Yast for a User Experience model.

Any help appreciated.

Thanks,

RC

---

### Post by ssam on 2006-03-30
you can do partitoning on the default install.

if you want really easy partitoning get the live cd, and use gparted to creat the partitions. (there is also a thread somewhere about resizing hfsplus partitions).

dapper (due out in june) will have a fancy graphical installer see [https://wiki.ubuntu.com/UbuntuExpress](https://wiki.ubuntu.com/UbuntuExpress)

---

### Post by rayc on 2006-04-01
[QUOTE=ssam]
if you want really easy partitoning get the live cd, and use gparted to creat the partitions. (there is also a thread somewhere about resizing hfsplus partitions).

[/QUOTE]

Tried this but gparted only gives me the option to delete, not resize or create.

Any pointers?

Cheers,
R

---

### Post by ssam on 2006-04-01
try [http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

---

### Post by jdp on 2006-04-01
It should be noted that **parted** on the command line from the installer CD *is not* the same as trying to use **gparted** from a LiveCD.  The HFS Resize thread describes using **parted** from the install CD.  They're very different things.

---

