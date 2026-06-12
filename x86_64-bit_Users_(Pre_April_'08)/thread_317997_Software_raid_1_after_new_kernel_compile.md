---
title: "Software raid 1 after new kernel compile?"
date: 2006-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by SundaY82 on 2006-12-13
Hi!

Im quite new to ubuntu/linux but i managed to install ubuntu 6.10 server x64. In ubuntu installation i created 2 raid1 partitions, one on 20gb for / and one on 2gb for swap. This worked great and i system boots fine on md0. But i now wanted to compile a new kernel to enable dm-crypt support with lukes according to this guide [http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian](http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian) .
And i also wanted to compile in support for my highpoint rocketraid 2240 controller. I followed this guide to compile my new kernel (2.6.19-1) [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) .

But now when i boot the new kernel first the system freezez after the usb line with hid-core.c for some time, maybe after 1-2min it says [DONE] and continues to mount the filesystem, but here its stuck, it cant find the /dev/md0 device. I have checked so Raid Support in enabled under Multi-device support in kernel config.

System are:
MB: ASUS M2N-LR/SATA
CPU: Athlon 64 3500
MEMORY: 512MB DDR2 800Mhz ECC (More on the way)
CONTROLLER: Highpoint Rocketraid 2240
And alot of disks.

Anyone know why i cant get it to boot?

Is there anything special i have to do for it to recognize my raid1 arrays?

I loaded the default (2.6.17-10) .config file when i compiled my new kernel and just made the changes to enable dm-crypt support and 2240 controller, i also changed from x64 general to athlon64/opteron as cpu, thats about it.

Would really appreciate if someone could help me out with this.

When i installed ubuntu with raid1, does the installation install grub on both drives and not only on the raid array so i can still boot if one disk fails?

---

### Post by psusi on 2006-12-15
I don't think you need to compile your own kernel - dm-crypt is already enabled in the stock one.

---

