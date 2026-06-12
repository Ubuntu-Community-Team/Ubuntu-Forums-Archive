---
title: "initramfs-tools ?"
date: 2007-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ulefr01 on 2007-05-28
root@xxxxx4-ubuntu:/boot# mkinitramfs 2.6.20-16-generic -o initrd.img-2.6.20-16-generic-1
root@franz4-ubuntu:/boot# ls initrd.img-2.6.20-16* -la
-rw-r--r-- 1 root root 7213131 2007-05-28 14:41 initrd.img-2.6.20-16-generic-1
Strange is 7213131 bytes !
root@xxxxx4-ubuntu:/boot# update-initramfs -c -k 2.6.20-16-generic
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
root@xxxxx4-ubuntu:/boot# ls initrd.img-2.6.20-16* -la
-rw-r--r-- 1 root root 7213220 2007-05-28 14:42 initrd.img-2.6.20-16-generic
-rw-r--r-- 1 root root 7213131 2007-05-28 14:41 initrd.img-2.6.20-16-generic-1
root@xxxxx4-ubuntu:/boot# mkinitrd.yaird 2.6.20-16-generic -o initrd.img-2.6.20-16-generic
yaird error: destination initrd.img-2.6.20-16-generic already exists (fatal)
root@xxxxx4-ubuntu:/boot# mv initrd.img-2.6.20-16-generic initrd.img-2.6.20-16-generic-2
root@xxxxx4-ubuntu:/boot# mkinitrd.yaird 2.6.20-16-generic -o initrd.img-2.6.20-16-generic
root@xxxxx4-ubuntu:/boot# ls initrd.img-2.6.20-16* -la
-rw------- 1 root root 1518821 2007-05-28 14:45 initrd.img-2.6.20-16-generic
-rw-r--r-- 1 root root 7213131 2007-05-28 14:41 initrd.img-2.6.20-16-generic-1
-rw-r--r-- 1 root root 7213220 2007-05-28 14:42 initrd.img-2.6.20-16-generic-2
As you can see, it is now 1518821 bytes !
I can boot with this initrd.img-2.6.20-16-generic.
With the generated initrd.img-2.6.20-16-generic-1 and initrd.img-2.6.20-16-generic-2 i can not boot ! 
I get :
BusyBox v 1.1.3
/bin/sh : can't access tty; job control turned off
initramfs : usb 2-1.2 can't set config #1 error -71

After a reinstall of the initramfs-tools this problem still exists.
After an install of a new kernel with apt-get ; the problem comes up again because the initramfs is automatically reexecuted and a wrong initrd.img file is made.  A manual reexecution with mkinitrd.yaird solves this problem.
Any idea ?
Thanks

---

