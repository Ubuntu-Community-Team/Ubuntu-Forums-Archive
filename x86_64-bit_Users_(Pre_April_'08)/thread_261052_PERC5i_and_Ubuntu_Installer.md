---
title: "PERC5i and Ubuntu Installer"
date: 2006-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Contivity on 2006-09-19
I have PowerEdge 2900, with PERC 5i RAID 1 system. Seems like Ubuntu installer sees the disk as 3 separates disks (/dev/sda, /dev/sdb, /dev/sdc). The sdc seems to point to the PERC while the rest is to individual disks. 

There are some threads that indicates if I use 6.06 (with 2.6.15-23 kernel), there's a workaround, but not with 6.06.1 (with 2.6.15-26 kernel).

I am using the amd64-server build and planning to load the amd64-xeon kernel. Any help would be appreciated.

Also, would installing using the desktop version then changing the kernel to server would work?

Thanks

---

### Post by Kilz on 2006-09-19
> **Contivity said:**
> I have PowerEdge 2900, with PERC 5i RAID 1 system. Seems like Ubuntu installer sees the disk as 3 separates disks (/dev/sda, /dev/sdb, /dev/sdc). The sdc seems to point to the PERC while the rest is to individual disks. 

There are some threads that indicates if I use 6.06 (with 2.6.15-23 kernel), there's a workaround, but not with 6.06.1 (with 2.6.15-26 kernel).

I am using the amd64-server build and planning to load the amd64-xeon kernel. Any help would be appreciated.

Also, would installing using the desktop version then changing the kernel to server would work?

Thanks

It looks like there is a bug report on this subject. You might want to keep an eye on it or add any info you think is important to help it get resolved.
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55138](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55138)
You might want to test the live cd or desktop cd, as it will tell you if the raid is seen as one disk. Yes you could install it the way you sugest if it dose see it that way. Even removing the desktop or changing to a lower resource desktop if it is going to be a server.
Im not real knowlageable on raid's but if the setup sees the raid and the seperate disks, it may be possible to just comment out the disks from the fstab file.

---

### Post by Contivity on 2006-09-20
Thanks Kilz

For anyone that knows:
I was shaking my head and saw this thread:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/57265](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/57265)

If I am installing for the first time (I downloaded the amd64 server version), how do I add the patch to the kernel as I am installing?

I used to be using Gentoo (couple years back), but moved to the Hoary for the smaller servers (sempron based with IDE HDD). I've loved Ubuntu, but not sure how to do all these in Ubuntu. I pretty much have until end of month to bring my mail server up.

Thanks in advance guys. You guys rocks!

---

### Post by Contivity on 2006-09-25
Bumped

---

