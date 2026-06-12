---
title: "Mouting HFS+ DVD-RAM Media"
date: 2006-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by zpro on 2006-05-12
Ubuntu does not load up Mac formated DVD-RAM media,
it will load, universal formated, and windows fat file system.

So, everthing mount, usb drives, all except Mac formated, dvd-ram media.
help please. ](*,) 

TKS +;)

---

### Post by ssam on 2006-05-14
try
```
sudo mkdir /media/dvd-ram
sudo mount -t hfsplus /dev/hdc /media/dvd-ram
```

---

### Post by BoneKracker on 2006-05-16
I put it in /etc/fstab as 

/dev/hdc     /media/cdrom     hfsplus,iso9660,udf     user,noauto     0 0

---

