---
title: "Partition problem - RAID5"
date: 2008-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by sevenmichael on 2008-04-02
Hi,

We have a new server, with RAID5 array for storage (6TB total - 4.5TB usable). I installed Ubuntu 7.10 server on a separate HDD (outside of the RAID array).

The OS runs fine and recognizes the RAID5 array and shows the correct size.

Here is the problem: when I try to create a partition with parted, and even though I select the full 4.5TB - it creates a partition of 550GB only... 

Is there any limitation on the partition sizes in Ubuntu ?

Thanks,

Michael

---

### Post by fjgaude on 2008-04-05
I don't think md and mdadm was made to be able to partition after an array is made.

If you wish more than one partition you make them before you create the arrays, then create them.

---

### Post by Robstarusa on 2008-04-07
> **sevenmichael said:**
> Hi,

We have a new server, with RAID5 array for storage (6TB total - 4.5TB usable). I installed Ubuntu 7.10 server on a separate HDD (outside of the RAID array).

The OS runs fine and recognizes the RAID5 array and shows the correct size.

Here is the problem: when I try to create a partition with parted, and even though I select the full 4.5TB - it creates a partition of 550GB only... 

Is there any limitation on the partition sizes in Ubuntu ?

Thanks,

Michael

This could very well be a parted problem.  Did you try with fdisk from the CLI?

---

### Post by stevecs on 2008-04-07
Ubuntu doesn't have a problem with large volumes itself (I'm running a 24TB array here and I've used >32TB arrays before both as lvm and non-partitioned (raw filesystem layout on device).

I haven't used parted much as I don't partition my drives (or at least none of my larger ones).  so yes it could be a parted problem.

---

