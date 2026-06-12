---
title: "grub loader"
date: 2008-11-30
forum: x86 64-bit Users
---

### Post by gretarsson on 2008-11-30
Hi there
If I take hdd out of one pc and put it into another pc and install ubuntu 8.10 into that hdd and mark grub loader for that hdd but when I take that hdd back to my pc it load up his grub karnel but nothing more, I have tried to install from live cd into that pc but first screen come up and then nothing how do I fix this?

---

### Post by cariboo on 2008-11-30
What error message are you getting? Can you post he output of:

```
sudo fdisk -l
```

You will need to run the above command from a Applications-->Accessories-->Terminal.

Also could you paste a copy of /boot/grub/menu.lst in yur next post.

You can use the LiveCD to but into your new installation, by choosing boot from hard drive from the menu.

Jim

---

### Post by gretarsson on 2008-11-30
> **cariboo907 said:**
> What error message are you getting? Can you post he output of:

```
sudo fdisk -l
```

You will need to run the above command from a Applications-->Accessories-->Terminal.

Also could you paste a copy of /boot/grub/menu.lst in yur next post.

You can use the LiveCD to but into your new installation, by choosing boot from hard drive from the menu.

Jim

Hi and thanks
my error is error 13  but know it say boot hdd 0,0 and uuid number and then it freeze 
My problem is I have new computer and had ubuntu 8.04 ultimate edition and upgradeed to 8.10 after that my pc did not load so I burn live cd but when I hit install nothing happen I tried many times so I took that hdd (hdd A) out of my pc and into another pc with ubuntu 8.10 and install that same live cd into that hdd (A) and mark that hdd (A) for grub karnel loading and put it back to my pc and got error 13, I tried to fix my grub loader with cd call super grub loader, still nothing so I put another hdd (B) into my pc witch already have ubuntu 8.04 so I can go into my main hdd (A) so my pc have now 2 hdd A and B I tried to install that live cd into hdd (B) same story here are out print from fdisk -l hdd A is 320GB 
                                                         hdd B is 250GB
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062f79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37778   303451753+  83  Linux
/dev/sda2           37779       38913     9116887+   5  Extended
/dev/sda5           37779       38913     9116856   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a4b3f90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29272   235127308+  83  Linux
/dev/sdb2           29273       30401     9068692+   5  Extended
/dev/sdb5           29273       30401     9068661   82  Linux swap / Solaris
jon@jon:~$ 
and know I got this when I go into grub

grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> 

And here is menu list from boot/grub/menu.lst from hdd (A) I did not copy the top part of it

title		Ubuntu 8.10, kernel 2.6.27-7- Gabriel
uuid		ca39f40c-428f-4932-9504-7f956fb2d7ac
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca39f40c-428f-4932-9504-7f956fb2d7ac ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ca39f40c-428f-4932-9504-7f956fb2d7ac
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca39f40c-428f-4932-9504-7f956fb2d7ac ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ca39f40c-428f-4932-9504-7f956fb2d7ac
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9923f9ea-e2d2-4031-ae20-622813a022e9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9923f9ea-e2d2-4031-ae20-622813a022e9 ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9923f9ea-e2d2-4031-ae20-622813a022e9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9923f9ea-e2d2-4031-ae20-622813a022e9 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by gretarsson on 2008-11-30
> **gretarsson said:**
> Hi and thanks
my error is error 13  but know it say boot hdd 0,0 and uuid number and then it freeze 
My problem is I have new computer and had ubuntu 8.04 ultimate edition and upgradeed to 8.10 after that my pc did not load so I burn live cd but when I hit install nothing happen I tried many times so I took that hdd (hdd A) out of my pc and into another pc with ubuntu 8.10 and install that same live cd into that hdd (A) and mark that hdd (A) for grub karnel loading and put it back to my pc and got error 13, I tried to fix my grub loader with cd call super grub loader, still nothing so I put another hdd (B) into my pc witch already have ubuntu 8.04 so I can go into my main hdd (A) so my pc have now 2 hdd A and B I tried to install that live cd into hdd (B) same story here are out print from fdisk -l hdd A is 320GB 
                                                         hdd B is 250GB
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062f79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37778   303451753+  83  Linux
/dev/sda2           37779       38913     9116887+   5  Extended
/dev/sda5           37779       38913     9116856   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a4b3f90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29272   235127308+  83  Linux
/dev/sdb2           29273       30401     9068692+   5  Extended
/dev/sdb5           29273       30401     9068661   82  Linux swap / Solaris
jon@jon:~$ 
and know I got this when I go into grub

grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> 

And here is menu list from boot/grub/menu.lst from hdd (A) I did not copy the top part of it

title		Ubuntu 8.10, kernel 2.6.27-7- Gabriel
uuid		ca39f40c-428f-4932-9504-7f956fb2d7ac
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca39f40c-428f-4932-9504-7f956fb2d7ac ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ca39f40c-428f-4932-9504-7f956fb2d7ac
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ca39f40c-428f-4932-9504-7f956fb2d7ac ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ca39f40c-428f-4932-9504-7f956fb2d7ac
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9923f9ea-e2d2-4031-ae20-622813a022e9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=9923f9ea-e2d2-4031-ae20-622813a022e9 ro single 
initrd		/boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9923f9ea-e2d2-4031-ae20-622813a022e9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9923f9ea-e2d2-4031-ae20-622813a022e9 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
 And here is boot/grub/menu.lst from hdd B (I am running on that one now) look at text in the end of it

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=32a774a8-28be-421d-9803-40809f820538 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=32a774a8-28be-421d-9803-40809f820538 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=32a774a8-28be-421d-9803-40809f820538 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=32a774a8-28be-421d-9803-40809f820538 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, kernel 2.6.24-17-generic (on /dev/sdc1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4ab63b8b-6f90-417f-b85a-4a64afa007ff ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4ab63b8b-6f90-417f-b85a-4a64afa007ff ro single 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4ab63b8b-6f90-417f-b85a-4a64afa007ff ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4ab63b8b-6f90-417f-b85a-4a64afa007ff ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
title		Ubuntu 8.04, memtest86+ (on /dev/sdc1)
root		(hd2,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

title jon
root		(hd1.0)
makeactive
chainloader    +1

---

### Post by gretarsson on 2008-11-30
Here is my grub list before when I tried to get him I was not logged as root user 

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
 (hd1,0)
grub>

---

