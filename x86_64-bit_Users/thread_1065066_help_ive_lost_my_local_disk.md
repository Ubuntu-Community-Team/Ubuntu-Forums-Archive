---
title: "help ive lost my local disk"
date: 2009-02-09
forum: x86 64-bit Users
---

### Post by bregale on 2009-02-09
hi all i have a dual boot system xp and ubuntu on 2 seperate hard drives, my ubuntu version is 8.04 . both drive are partioned into 2.
 i booted into windows at the weekend and deleted some files on my ubuntu local disk which i did no longer want, now when i boot ubuntu it cannot see my local disk ( the 2nd partion on my ubuntu drive)
    has anyone any idea how i can restore this without a full reinstall

        thanks

---

### Post by drs305 on 2009-02-09
My understanding is that you can still boot to ubuntu normally, but can't see a second linux partition.

First, see what your partition setup is like:
```
df -Th
```
Is the partition still showing up?

Do you have a listing for it in fstab?
```

cat /etc/fstab

```
If so, does the mount point still exist?

Run nautilus as root and see if you can find the mount point.
```
gksudo nautilus
```

---

### Post by bregale on 2009-02-09
yes i can still boot ubuntu ok . 
  thanks i will try as you have suggest

---

### Post by bregale on 2009-02-09
no file system found on the first comand, !!

---

### Post by Yellow Pasque on 2009-02-09
Your post confuses me. Did you use some sort of utility within Windows to delete files on an ext3 partition?

I'm imagining your partition setup as follows:
Disk 1, Partition 1 = NTFS Drive (with Windows OS)
Disk 1, Partition 2 = NTFS Drive (data storage)

Disk 2, Partition 1 = ext3, Ubuntu OS
Disk 2, Partition 2 = ext3 (perhaps /home or other data storage)

Correct me if I'm wrong.

---

### Post by bregale on 2009-02-10
hi temujin you have got it spot on thats how it was set up , i did not use any programme or utility just deleted files manualy there was nothing specific just old divx files photos etc .

   thanks if you could be any help

---

