---
title: "[SOLVED] Partition names change on reboot"
date: 2008-09-10
forum: x86 64-bit Users
---

### Post by Ellhound on 2008-09-10
Hey.

 I'm pretty new to linux, just started using it last week. I've been trying to get my ntfs partitions mounted the way i want and sharing them using Samba. I got it working, but very time i reboot my computer, the partition names (/dev/hda, /dev/hdb etc) get mixed around. As a result, every time i reboot theres a different partition on every mountpoint. This is rather annoying, and i havent been able to find a solution anywhere. 
I hope someone will be able to help out here.

---

### Post by sisco311 on 2008-09-10
mount the partitions by uuid.

use
```
sudo vol_id -u */dev/hdXY*
```to get the uuid of the partition.

fstab example:
> UUID=*6616dc7a-c8f7-42d3-b9f0-28f909180833* */mount/point* ntfs *options 0 0*

---

### Post by Ellhound on 2008-09-10
Thanks, that fixed it.

---

