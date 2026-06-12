---
title: "Remounting HDD-Drive After Converting it from NTFS to FAT"
date: 2006-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by metalspree on 2006-12-12
I recently converted one of my drives in my primary SATA HDD (using partition Magic from NTFS to FAT32). Now the drive isn't getting mounted during boot-up.
I tried editing fstab but did no good....iv noticed a "ID" side by to the "/dev/sda5" line. I didnt wanna toy around much with fstab, i'd rather consult the expertise :-| 

Any ideas of how to get it mounted back to life :rolleyes: ?

---

### Post by pay on 2006-12-13
add this to the end of your fstab
```
/dev/sda5 /where/you/want/to/boot vfat default 0 0
```

---

### Post by metalspree on 2006-12-13
Had some difficulties figuring that out...Perhaps you could tell me what to do on this. (Btw the partition was sda6)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=2954a9c9-9a7d-485c-813e-12948f5cd497 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8CA43C25A43C13E4 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=366CC499A3AC8E09 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=A478245B78242F0C /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=18ECE9C7ECE99F6E /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=8ED0EEB2D0EE9FA7 /media/sda8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb7
UUID=10CC0E8BCC0E6B74 /media/sdb7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb8
UUID=12D3EA0387AD12F9 /media/sdb8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=d64f1015-3446-4122-8ffe-480921eff47a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda6 /media/sda6 vfat default 0 0

```

---

### Post by pay on 2006-12-13
try ```
sudo mkdir /media
sudo mkdir /media/sda6
sudo mount -a
```

---

