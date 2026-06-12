---
title: "Ubuntu doesn't auto mount my ntfs partition"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by jemrpo on 2008-05-15
Hi here is my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb8
UUID=4e1775bb-a411-4b7b-a4fe-08e63980101e /               ext3    relatime,errors=remount-ro $
# /dev/sdb7
UUID=e17a23f2-3240-9994-1d2b-60e26db8a65e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
###
/dev/sda1 /media/disk  ntfs-3g realtime,auto,nls=utf8,umask=0222 0 0
/dev/sdb6 /media/disk-1 ntfs-3g realtime,auto,nls=utf8,umask=0222 0 0
/dev/sdb5 /media/Musica ntfs-3g realtime,auto,nls=utf8,umask=0222 0 0

when I start ubuntu it doesn't load sda1, sda6 ,sda5 partition by default, so when I try ie with amarok It doesn't play any music...
I have to go to gnome menu -> places -> home folder. then I have to  click on these partitions and they start working. what could I add to my fstab to make my partitions from the beginning without doing what I've already explained.

---

### Post by Yellow Pasque on 2008-05-15
I'm not familiar with the realtime option (it could be valid). Try looking through system logs with:
```
dmesg | grep sda
```

---

### Post by jemrpo on 2008-05-15
jemrpo@jemrpo-desktop:~$ dmesg | grep sda
[   29.255328] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   29.255338] sd 1:0:0:0: [sda] Write Protect is off
[   29.255340] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.255351] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.255395] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   29.255401] sd 1:0:0:0: [sda] Write Protect is off
[   29.255403] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   29.255413] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.255415]  sda: sda1 < sda5 sda6 sda7 sda8 >
[   29.305014] sd 1:0:0:0: [sda] Attached SCSI disk
[   38.906826] Adding 506008k swap on /dev/sda7.  Priority:-1 extents:1 across:506008k
[   39.444918] EXT3 FS on sda8, internal journal
jemrpo@jemrpo-desktop:~$

---

### Post by Yellow Pasque on 2008-05-15
Ok, it looks like they're mounting properly. I believe the issue is with permissions. Let's try:
```
/dev/sda1 /media/disk ntfs-3g realtime,auto,nls=utf8,uid=1000,gid=100 0 0
/dev/sdb6 /media/disk-1 ntfs-3g realtime,auto,nls=utf8,uid=1000,gid=100 0 0
/dev/sdb5 /media/Musica ntfs-3g realtime,auto,nls=utf8,uid=1000,gid=100 0 0
```
[http://wiki.archlinux.org/index.php/NTFS_Write_Support](http://wiki.archlinux.org/index.php/NTFS_Write_Support)

---

### Post by jemrpo on 2008-05-15
didn't work :S

---

### Post by BlueSkyNIS on 2008-05-15
You are using different options that I do, here is a peak at my fstab, maybe will do for you either:

```

# /dev/sda1
UUID=5C10CDFE10CDDF60 /media/System ntfs rw,noatime,relatime,nosuid,nodev,auto 0 0
# /dev/sda2
UUID=3E448444448400BF /media/DATA ntfs  rw,noatime,relatime,nosuid,nodev,auto 0 0

```

If not, look at [this]("http://ubuntuforums.org/showthread.php?t=766688&highlight=automount+partitions").

---

### Post by jemrpo on 2008-05-15
sudo vol_id -u /dev/sda1

so your fstab file will have this line
Quote:
UUID=NUMBER_ID /media/backup ntfs defaults,umask=007,gid=46 0 1
where NUMBER_ID is the output from vol_id for your device, i.e.:
UUID=78980E1B980DD890 /media/backup ntfs defaults,umask=007,gid=46 0 1
instead of
/dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 1 



done deal with that..
thx guys.

---

