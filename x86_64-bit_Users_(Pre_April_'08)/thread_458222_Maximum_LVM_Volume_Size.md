---
title: "Maximum LVM Volume Size"
date: 2007-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by deviantintegral on 2007-05-29
I'm building a system with 6x250 GB and 2x500 GB disks using RAID5 and LVM. Will 32 bit Ubuntu allow me to have a LVM and partition size larger than 2TB? While it's not going to be bigger than that yet, I would like to be able to grow the volume without having to reinstall the x64 version.

Thanks!
--Andrew

---

### Post by Ken_Lewis81 on 2007-05-30
That 2 TiB limit is the Linux Kernel's block layer.  LVM2 doesn't have an upper limit, but a quick google tells me that this upper limit is imposed by the 32-bit kernel.  You'd need to move to the amd64 edition anyway if you expanded your LVM.

Take care.
Ken.

---

### Post by deviantintegral on 2007-05-30
Excellent, that's what I was finding too, but I wasn't sure. Thanks!

---

