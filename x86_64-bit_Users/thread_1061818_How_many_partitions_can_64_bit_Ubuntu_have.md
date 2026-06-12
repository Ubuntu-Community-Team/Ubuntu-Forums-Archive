---
title: "How many partitions can 64 bit Ubuntu have ?"
date: 2009-02-06
forum: x86 64-bit Users
---

### Post by randiroo76073 on 2009-02-06
Sounds dumb I know, but am currently running 8.10 & seem to only be able to get 15 partitions, # 16 will not format, always get error when trying. Reason for asking is I multi-boot different distros(chain-load) & Ubuntu has always been my swing/main OS on partitions 1 & 2, the rest come & go.

---

### Post by drs305 on 2009-02-06
From this Ubuntu Documentation Link. Note it is from 7.04 so it's a bit dated. It has some reference links:
[https://help.ubuntu.com/7.04/installation-guide/i386/partition-programs.html]("https://help.ubuntu.com/7.04/installation-guide/i386/partition-programs.html")


> Linux limits the partitions per drive to 15 partitions for SCSI disks (3 usable primary partitions, 12 logical partitions), and 63 partitions on an IDE drive (3 usable primary partitions, 60 logical partitions). However the normal Ubuntu system provides only 20 devices for partitions, so you may not install on partitions higher than 20 unless you first manually create devices for those partitions. 

---

### Post by randiroo76073 on 2009-02-06
Thanks drs305, very helpful. I plan on getting a 1tb sata soon and wonder if it wouldn't be better to go with LVM ?

---

