---
title: "Problem mounting hard disks"
date: 2006-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by matog on 2006-08-02
i've installed Ubuntu Dapper 64.
It worked great, all my hardware were supported!
I've got a sata hard disk, with 3 partitions:
- One nhtfs, were xp is   installed.
- One with Ubuntu
- One FAT32

First time I started ubuntu, all partitions were detected and mounted. Even my hard disk on other computer, conected by a lan.

But, two days after, I've restarted my computer, and the fat partition, and the one frome the lan were not mounted. But I can browse the lan, and enter to the folder of the hard disk with no problem at all.
The fstab file is (I've only included the lan folder line, the rest is the default version of the file):

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1, defaults,umask=000 0 1
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

//mariana/misdocumentos /media/red/ -o username=Matias,password=pass,,dmask=777,fmask=777
//mariana/rigido-mariana /media/rigidomariana/ -o username=Matias,password=pass,,dmask=777,fmask=777
```

---

### Post by Kilz on 2006-08-02
Looking at it, the vfat line

```
/dev/sda3 /media/sda3 vfat defaults,utf8,umask=007,gid=46 0  1, defaults,umask=000 0 1
```
isnt quite right. It should say
```
/dev/sda3  /media/sda3  vfat   defaults,utf8,umask=007,gid=46   0  1
```
You can edit it with this command in a terminal
```
gksudo gedit /etc/fstab
```

For the ntfs im not sure why its not mounted at /media/sda3. Are the /media/sda3 and /media/sda1 folders already created?
For the network shares, are the shares on a windows computer? If so what version of windows?

---

